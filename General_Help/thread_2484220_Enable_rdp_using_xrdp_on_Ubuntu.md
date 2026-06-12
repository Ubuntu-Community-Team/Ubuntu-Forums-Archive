---
title: "Enable rdp using xrdp on Ubuntu"
date: 2023-02-20
forum: General Help
---

### Post by briandr73 on 2023-02-20
Hello,

Newbie to Ubuntu\Linux. Reaching out here because google results tend to be old and sometimes all over the map. Really don't want to go by a result returned by google that might be 2+ yrs old. Hoping someone can provide a fairly newer link with step by step instructions on setting up rdp so my Ubuntu desktop\vm can be accessed from windows pc. thank you.

---

### Post by MAFoElffen on 2023-02-20
Here you go (current instructions): [https://tecadmin.net/how-to-install-xrdp-on-ubuntu-22-04/](https://tecadmin.net/how-to-install-xrdp-on-ubuntu-22-04/)

What is the VM Host? And what is the Ubuntu Version of the VM?

---

### Post by briandr73 on 2023-02-20
the VM host is 22.10 and I have not yet start building the thin client desktop that will run the same version. I have seen something very similar and I think this assumes a user and pw is already setup and when I connected to the session all I got was a blank blue screen that never finished loading. I need something that won't have any peripherals attached. In a perfect scenario I would use a Pi but the darn shortage is never ending and I cannot see spending 2x or 3x what the scalpers\crooks want from them. So I just want a small refurb thin client that would do what I need and let me remote into it.

---

### Post by MAFoElffen on 2023-02-20
Yes, connects through a user's credentials through an X11 session, via RDP protocol. Initial Screen should be the login screen with the xrdp login dialog. Once the credential are entered, then a pop-up will appear asking the resolution of the session (just like many other RDP sessions on connect).

---

### Post by briandr73 on 2023-02-20
I never got past the login screen with the xrdp login dialog. I will try again using your provided link.

---

### Post by briandr73 on 2023-02-20
When I check the status (this is on the Ubuntu vm) I get this: 

xrdp.service: Can´t open PID file /run/xrdp/xrdp.pid (yet?) after start: Operation not permitted

---

### Post by MAFoElffen on 2023-02-20
Usually when it gets that specific error using RDP protocol, it's telling you that it can only have one specific user logged in at a time. Meaning a User cannot be logged in locally, and the same user through RDP. If there is only one user configured in the system, if logged in locally, is will be locked... So if a user is logged in, log that user out, and try again. A way to get around that is to create a specific user that you will only use for RDP connections...

---

