---
title: "Citrix Receiver through Command Line?"
date: 2016-11-24
forum: General Help
---

### Post by Barry_Keegan on 2016-11-24
Hi all. I'm wondering if you can connect to a remote server through the command line when using Citrix Receiver.

In my situation the remote server is simply a "Jump Box" before I connect to Routers/Switches on the network. I'd rather skip the GUI on the Jump Box and connect through to get directly onto the Routers/Switches. In my mind if I could connect through the command line I could find a fast method of connecting onto the devices I'm working with.

---

### Post by TheFu on 2016-11-25
Most network management that I know is through ssh, not citrix. Is that an option for you? Sorry, don't know anything current about citrix - last used it in the 1990s. 

ssh is the swiss-army-knife of secure networking. Works on almost every platform except Windows. A few years ago, MSFT claimed they were making an ssh server, but I haven't heard anything more about it.  There were 3rd party sshd's, but keeping them patched on Windows (secure) was something most places failed at. Running an sshd with known security issues is really, really, really, bad.

---

