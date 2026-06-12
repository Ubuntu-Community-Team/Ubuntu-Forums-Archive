---
title: "need help to set up autogen studio 2.0"
date: 2024-01-27
forum: General Help
---

### Post by Gatorade on 2024-01-27
I've been trying to install and run autogen studio 2.0 , but I am running into errors setting it up.

[https://gptpluginz.com/autogen-studio-ui/]("https://gptpluginz.com/autogen-studio-ui/")

all the tutorials state that python 3.11 , and a conda environment are prerequisite

I downloaded and installed anaconda, which to my understanding , contains python 3.11
this next step after completion of the installation , is where I am running into issues. 

trying to create a conda environment, is giving me errors like it can't find it or something.
If anyone here has successfully set up autogen studio 2.0, please let me know.

---

### Post by Gatorade on 2024-01-27
I have created a conda environment , activated autogen studio , and tried to export the api key

"Setting Up the API Key in Your Environment: After obtaining your API key, you’ll need to make it available in your Conda environment. This is done by setting it as an environment variable, ensuring that AutoGen Studio can use it whenever it needs to communicate with the language models. To set the API key, in your terminal, type:

export OPENAI_API_KEY=your_openai_api_key_here"


this is where I get an error. 

'export' is not recognized as an internal or external command,operable program or batch file.

can anyone shed some light on this issue for me please, and explain why this error is happening.

---

### Post by Gatorade on 2024-01-27
I resolved the issue with the help of chatGPT.


"It seems like you're encountering an issue with the export command, which is commonly used in Unix-like systems (Linux and macOS) to set environment variables. In Windows, the equivalent command is set. Here's how you can set the environment variable for the OpenAI API key in a Conda environment:
For Unix-like Systems (Linux, macOS):

bash

# Replace 'your_openai_api_key_here' with your actual API key
export OPENAI_API_KEY=your_openai_api_key_here

For Windows:

bash

# Replace 'your_openai_api_key_here' with your actual API key
set OPENAI_API_KEY=your_openai_api_key_here "

changing the command to 'set' solved the problem

---

