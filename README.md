from openai import OpenAI

client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key="<OPENROUTER_API_KEY>",
)

response = client.chat.completions.create(
    model="google/gemini-3.1-pro-preview",
    messages=[
        {"role": "user", "content": "Explain the implications of quantum entanglement."}
    ],
    extra_body={
        "reasoning": {
            "effort": "low"  # Maps to thinkingLevel: "low"
        }
    },
)

msg = response.choices[0].message
print(getattr(msg, "reasoning", None))
print(getattr(msg, "content", None))
