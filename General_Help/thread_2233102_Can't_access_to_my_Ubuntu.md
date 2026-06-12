---
title: "Can't access to my Ubuntu"
date: 2014-07-06
forum: General Help
---

### Post by _SPiRiT_ on 2014-07-06
I wanted to change permission for a folder located in Documents using this command
 chmod -R 777 /folder/path/. it started to list a lot of folders following them with access denied message.
Then whatever application I tried to launch, I got an access denied message. I had to force restart the computer, but now I can't log into Ubuntu. And I get a message concern graphic card and I can't bypass it. But the recovery mode loads fine, but I don't what command I shall use to grant access to ubuntu again.

---

### Post by Elfy on 2014-07-06
the command was actually chmod -R 777 /folder/path or something else?

What do you see in your bash history?

---

### Post by steeldriver on 2014-07-06
Hello and welcome to the forums

What was the exact /folder/path that you typed? What directory were you in when you executed the command, and did you use 'sudo' or just execute it as your regular user?

---

### Post by grahammechanical on 2014-07-06
Are the two problems related? Or did the force restart mess up the loading of the proprietary video driver. It would be useful to give us the full message regarding the graphic card. Recovery>Resume load Ubuntu with an open source video driver. If there really was a problems with the file permissions then Recovery Mode should not be loading either. Try installing or re-installing the video driver with Additional Drivers.

Regards.

---

