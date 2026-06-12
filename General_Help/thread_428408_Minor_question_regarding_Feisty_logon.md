---
title: "Minor question regarding Feisty logon"
date: 2007-04-30
forum: General Help
---

### Post by Blueshift on 2007-04-30
I have a small question if you like... Why do you have to write the password twice when logging on the Ubuntu box? Is it an extra security measure or just a small flaw?

---

### Post by Snowcat on 2007-04-30
You're not supposed to...

Unless the second time it is the keyring-manager asking for your password? (It is a window that appears after logging in, and is requested by NetworkManager to recall stored network information).

---

### Post by aldenhg on 2007-04-30
I could be that something is in your startup tab that needs superuser permission. Go to System>Preferences>Sessions and take a look at the Statup Programs lst. If there's anything in there that would need clearence, it's the culprit.

---

### Post by Blueshift on 2007-04-30
I can't see anything unusual in the session manager:

```
External Media...
Evolution Alarm Notifier
Network Manager
Restricted Drivers Manager
Power control
Update Notifier
```

(Translated from Danish Ubuntu to English, sorry if its not 100% correctly translated)

Care to comment, if there is anything thats not suppose to be there?

-----------------------

I shouldn't have to type in the other password for the keyring manager as I have installed the pam_keyring module to automate that for me... and its still in the splash screen anyway, when its asking me to type my password for a second time... so still don't get why I have to type it twice... :confused:

---

### Post by aldenhg on 2007-05-01
Hmmm... I don't know then. There are so many variables from system to system that it's hard to pinpoint problems like this for someone who in the grand sceme of the Linux world is a relative newbie. I only know what I've had to deal with myself, so keep looking for answers!

---

### Post by Guranic on 2007-05-26
> **Blueshift said:**
> 
I shouldn't have to type in the other password for the keyring manager as I have installed the pam_keyring module to automate that for me... and its still in the splash screen anyway, when its asking me to type my password for a second time... so still don't get why I have to type it twice... :confused:

I guess you followed some howto to make your keyringmanager to stop asking password. I did. And My lappy was like your box before I read the howto thread again. [http://ubuntuforums.org/showthread.php?t=192281&highlight=pam+network+manager&page=8](http://ubuntuforums.org/showthread.php?t=192281&highlight=pam+network+manager&page=8) page 8 tells you what to do with Feisty.. assuming you followed this thread before.. Try this..

---

### Post by maidamar on 2007-07-19
Could it be that the first time you type your password you type a wrong one? In my case, and I'm still trying to figure it out, the first character I type in the logon screen is not actually typed in the input field, so I have to type a character twice.
Just an idea.

---

