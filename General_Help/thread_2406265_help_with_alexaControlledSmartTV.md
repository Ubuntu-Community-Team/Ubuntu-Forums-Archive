---
title: "help with alexaControlledSmartTV"
date: 2018-11-18
forum: General Help
---

### Post by russellhearn691 on 2018-11-18
I'm trying to get alexa to control my Samsung tv using alexaControlledSmartTV, I have followed the bellow instructions but cant get past the "[COLOR=#333333][FONT=&amp]python3 alexasmartcli.py login" [/FONT][/COLOR] command. and the output i get from ssh terminal is this, if anyone can help me that would be great. Thanks

"Password:
Traceback (most recent call last):
  File "alexasmartcli.py", line 49, in <module>
    file = open('.auth/token','w')
PermissionError: [Errno 13] Permission denied: '.auth/token'
russellhearn69@HomeServer:~/AlexaControlledSamsungTV$"



[COLOR=#333333][FONT=&amp]Steps:[/FONT][/COLOR]

[LIST]
[*]Create an account here (I assume you already have one)
[*]On your raspbery pi run the following inside any directory
[LIST=1]
[*]git clone [https://github.com/eclair4151/AlexaControlledSamsungTV](https://github.com/eclair4151/AlexaControlledSamsungTV)
[*]cd AlexaControlledSamsungTV
[*]pip3 install -r requirements.txt
[*]python3 alexasmartcli.py scan
[/LIST]

[*]Copy the ip address, model, and mac address into the tvconfig.py file
[*]Rename the TV to want you want to call it and change prefer HD to False if you dont have hd cable
[*]then run the following commands
[LIST=1]
[*]python3 alexasmartcli.py login
[*]python3 alexasmartcli.py register
[*]python3 alexasmartcli.py setup_cable (optional and only currently works in the US)
[*]python3 alexasmartcli.py start (run with -m to mute the output)
[/LIST]

[*]to run this automatically on boot edit /etc/rc.local and add this line before exit: 
python3 /PATH/TO/FOLDER/alexasmartcli.py start -m &&
[*]you should now be all setup. Go on your alexa app to the 'Smart Home' section. Search for unonfficial Samsung Smarttv controller and install it
[*]Link to Alexa skill: [https://www.amazon.com/dp/B07886XNK8](https://www.amazon.com/dp/B07886XNK8)
[*]Log in with your account, discover devices and you should be good to go
[/LIST]

---

### Post by oldos2er on 2018-11-18
You might want to create an issue at [https://github.com/eclair4151/AlexaControlledSamsungTV/issues/13](https://github.com/eclair4151/AlexaControlledSamsungTV/issues/13), for specialized software like this ubuntuforums may not be the best place to seek help.

---

### Post by russellhearn691 on 2018-11-18
Thanks for pointing me in the right direction mate, cheers

---

