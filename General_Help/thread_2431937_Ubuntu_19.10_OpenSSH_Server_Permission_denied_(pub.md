---
title: "Ubuntu 19.10 OpenSSH Server Permission denied (publickey,password)."
date: 2019-11-24
forum: General Help
---

### Post by El_Demiurgo on 2019-11-24
Dear All,
I am having issued while trying to log from one desktop to another. One PC is used as regular desktop and the other has Kodi. I am trying to log from the desktop to the Kodi one. I never had any problems in the past in previous versions but now I get the Permission denied (publickey, password) message.

My typical steps to install everything is:
1) Install clean Ubuntu 19.10
2) Install openssh server
3) activate sharing on configuration menu 
4) use keygen to delete all keys while trying to connect for the first time from the client computer

While trying to understand the problem I tried to log inside the server machine using the terminal and it works but I can't do it from any machine outside that one. I also allowed traffic con ufw.

I've been using ubuntu since 12.04 or something and this is the only time this happens.

Thank you for any help.!

---

### Post by TheFu on 2019-11-24
Anything interesting in **ssh -vv userid@remote**?
How far does it get?

I'm not seeing any issues going from 16.04 clients to a 19.10 server. I use ED25519 keys.

---

### Post by HermanAB on 2019-11-25
To test a network connection, you need to use tools that will generate sensible error messages.  One such simple tool is a telnet client:
$ telnet remote 22

Another tool is ssh client:
$ ssh -vvv remote

Then google the error messages.

---

### Post by El_Demiurgo on 2019-11-25
Hi HermanAB & TheFu,
Thanks for your messages. 
I've tried telnet and port 22 is ok.

I've also used ssh -vvv but the only thing I see is the original message I posted (I've reviewed the file several times). I am adding the error.txt file with the messages I get because maybe I am missing something.

Thanks!

---

### Post by HermanAB on 2019-11-25
According to that error log, both your key and your password are wrong, which probably means that your login user name is wrong.

---

### Post by El_Demiurgo on 2019-11-25
Thank you HermanAB. I reinstalled openssh for the third time and set up new users and now it works. Probably is what you said. Thank you.

---

### Post by TheFu on 2019-11-25
> **El_Demiurgo said:**
> Thank you HermanAB. I reinstalled openssh for the third time and set up new users and now it works. Probably is what you said. Thank you.

The easy answer for handling different usernames is to setup stanzas with aliases in your ~/.ssh/config file.  Learning how this works will save you so many hassles.

```
host vpn.example.com 
  hostname 190.23.34.231
  user thefu9444432
  port 50020
```

Have as many stanzas as you like. Only the "host" needs to be unique.  The hostname can be IPs or dns or /etc/hosts entries.  Never need to know the userid or that non-standard port again.  All ssh-based tools honor this file.  There are lots of other per-stanza options like specifying a different key or tunnel settings or .... anything in the manpage for ssh_config.

---

### Post by El_Demiurgo on 2019-11-25
TheFu, thanks a lot for going the extra mile helping me!!! Really appreciate. I will study and use this info.

Thanks again!

---

