---
title: "How to lock down Ubuntu"
date: 2016-09-23
forum: General Help
---

### Post by JohnnyTricksta on 2016-09-23
I am on the fire department and we just acquired a new computer to use at the station to receive emails from our dispatchers about 911 calls. I want to put this computer in the office, but want to lock it down. Basically, all I want is to block all internet traffic expect for an email client using IMAP. Is this possible? I do not want the office to be able to access any websites UNLESS you can recommend a good website filter.

---

### Post by Geoffrey_Arndt on 2016-09-24
Must have internet access for security updates to any OS.   Plus any Linux needs internet access to install programs, etc.  

If just wanting simple email, I've read that Geary is simple & good, and many folks use Thunderbird but it has more options than Geary.     uBlock Origin is a good filter . . good help and youtube tutorials available.   

Best way to lock it down is to have just 1 or 2 admins on the system - - other access not allowed if someone doesn't have a user profile created.    Be sure to find out how to lock the screen if the system is unattended.  Be sure not to share the login password except for the few authorized users.

PS:   malware not an issue in any Linux - - Firefox generally considered to have a slight edge re browser security.

---

### Post by DuckHook on 2016-09-24
How sophisticated are your users?

The answer depends on how geeky they are. The simplest way that occurs to me is to set your firewall (impossible to avoid the pun in your line of work) to block all outgoing/incoming ports except email and then set up a user account for general use that has no authority to elevate to root (not on sudoers). However, it is rather a nuclear option in that you have now converted your computer into a dumb email terminal. Also, it is child's play for even a relatively low-level geek to work around or disable such measures. It is a truism in the security community that anyone with physical access to the machine can defeat almost any restriction.

I would encourage you to also look into OpenDNS as a content-filtering/counter-phishing DNS service. Link as follows:

[https://www.opendns.com/](https://www.opendns.com/)

By setting your router to use only their Domain Name Servers, they will filter objectionable sites based on a community-driven blacklist. I use them mainly because personal use is free, but enterprise use (which yours appears to be) involves payment.

---

