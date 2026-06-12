---
title: "login via ssh"
date: 2019-01-22
forum: General Help
---

### Post by The Cog on 2019-01-22
At the command prompt on the pi, use the commands
```
sudo apt update
sudo apt install openssh-server
```
Then you can connect to it from elsewhere with the command:
```
ssh pi@192.168.0.105
```
but using the IP address of your pi of course - that's my pi.
Remember that ssh is regularly scanned by hacking bots that sit there all day guessing usernames and passwords. You should google for "passwordless ssh", where you generate a key on your client and configure the server only to accept recognised keys. It is passwordless because 1) you don't get asked for a passsword - as long as you have the right key you connect without question, and 2) no amount of password guessing will get someone without a key connected.

---

### Post by HermanAB on 2019-01-22
I tried "ssh pi@192.158.0.105", but your RPi is offline.
;)

---

### Post by The Cog on 2019-01-22
> **HermanAB said:**
> I tried "ssh pi@192.158.0.105", but your RPi is offline.
;)
Typo, sorry. Its correct address is 192.168.0.105. That's what comes of typing in a hurry.
Just noticed you're winking, so I guess you know that anyway.

---

