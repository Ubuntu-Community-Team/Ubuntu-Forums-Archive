---
title: "Problems with accessing Remote Desktop from a Mac"
date: 2016-10-14
forum: General Help
---

### Post by ben1828 on 2016-10-14
Hello

I am running version 16.04 and wish to access the desktop remotely from another machine (in the house)

I have followed instructions for how to set it up - couldn't be easier - [https://help.ubuntu.com/16.04/ubuntu-help/sharing-desktop.html](https://help.ubuntu.com/16.04/ubuntu-help/sharing-desktop.html)

On my Mac i am using MS Remote Desktop Connection (I also use this to connect to a Windows Server) and simply get the error 'Connection refused'.

The obvious culprit is networks, however the Ubuntu machine is wired to a home router (simple, ISP supplied device) and the Mac client(s) are wireless to that router.

I've had a Google, but suggestions involve installing additional software on the Ubuntu machine, which doesn't seem right. Other links are accessing it from a Windows client.

Only thing I can think of is having to specify the IP and Port (rather than just port), but I don't know which port it's listening on.

Thanks for any suggestions

Ben

---

### Post by ben1828 on 2016-10-15
bump ?

---

### Post by davedgd on 2016-12-29
Did you ever find a fix for this problem? I'm having the same issue with both 16.04 and 16.10, whereas it works fine with a 15.10 install. When connecting remotely from my Mac I need to do it through a VirtualBox Windows 10 instance, whereas from Windows 10 directly it works fine.

---

