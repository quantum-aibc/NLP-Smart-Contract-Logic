# NLP-Smart-Contract-Logic
import requests

def generate_solidity_code(natural_language_input):
    # Mistral API endpoint
    url = "https://api.mistral.ai/v1/generate"

    # API key
    api_key = "YOUR_API_KEY"

    # Headers
    headers = {
        "Authorization": f"Bearer {api_key}",
        "Content-Type": "application/json"
    }

    # Payload
    payload = {
        "prompt": f"Convert the following natural language instruction to Solidity code: {natural_language_input}",
        "max_tokens": 150
    }

    # Make the request
    response = requests.post(url, headers=headers, json=payload)

    # Parse the response
    if response.status_code == 200:
        return response.json()["choices"][0]["text"]
    else:
        return "Error generating Solidity code"

# Example usage
natural_language_input = "Create an ERC-20 token with minting restricted to an allowlist"
solidity_code = generate_solidity_code(natural_language_input)
print(solidity_code)
