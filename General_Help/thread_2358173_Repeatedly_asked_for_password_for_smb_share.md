---
title: "Repeatedly asked for password for smb share"
date: 2017-04-10
forum: General Help
---

### Post by chris431 on 2017-04-10
I have a shared hard drive connected to my router that I use for storing media. I have no problems connecting to this share on my Windows 10 desktop, Mac laptop and Ubuntu (15.10) laptop. However, if I try to connect with my Ubuntu (16.04) desktop I am repeatedly given the user and password dialog:
[IMG]https://i.stack.imgur.com/9impK.png[/IMG]

If I configure the share to not use a username and password I have no problems connecting.

How do I find what is causing this and fix it?

---

### Post by TheFu on 2017-04-10
How?  Look at the log files. See what they show.  Take corrective action based on google-fu.
[https://wiki.ubuntu.com/DebuggingSamba](https://wiki.ubuntu.com/DebuggingSamba)
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Wouldn't hurt to look at the samba client upgrade notes too, since 15.10 --> 16.04 something appears to have changed that broke something you needed.  

Support for 15.10 ended last July, BTW. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

