---
title: "vnc issues"
date: 2006-10-23
forum: General Help
---

### Post by wynutter on 2006-10-23
Heya All,

I've been having a few problems with my Ubuntu (edgy) distribution. I can't seem to get VNC to work at all. Each time I try to connect it does this:

ama42@pccl061:~> vncviewer  mycomputerIPhere
VNC server supports protocol version 3.7 (viewer 3.3)
Password:
VNC authentication failed

I've tried uninstalling as much as I can and then reinstalling. It is still actually doing this despite not having any VNC servers running on the thing. The things I can't uninstall are vnc-common, vnc4-common or xvncviewer because Ubuntu seems to depend on them. I'm really confused as to what I've got wrong because I believe this isn't a problem for most people's distrobutions. I know the IP address is right because I'm SSH'd into it making these changes. Any assistance would be much appreciated!

Austin

---

### Post by Malakia on 2006-10-23
What client is running on the computer you are trying to connect to sometimes that can be the culprit or try tightvnc or openvnc.

---

### Post by wynutter on 2006-10-24
I did try both of those, but the thing that really confuses me is that I have no server installed at the moment and it's still confronting me with the same response when I try to access it from a remote computer.

Austin

---

### Post by rich710 on 2006-10-25
I also have some issue with remote desktop, everytime i restart my computer the password is "reset" or something, but if I enter it again in system-admin remote desktop, then vnc works until I restart my computer again. How do I do to make the password in remote desktop stay "forever" ??

---

### Post by yariops on 2006-10-29
i have this problem too :(  need to insert the password every time that computer restarts.. anyone know the answer to this problem ? 

thanks and best regards

---

