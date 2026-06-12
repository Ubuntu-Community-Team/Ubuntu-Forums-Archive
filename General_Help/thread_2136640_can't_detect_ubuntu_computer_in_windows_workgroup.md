---
title: "can't detect ubuntu computer in windows workgroup"
date: 2013-04-18
forum: General Help
---

### Post by Novice Networker on 2013-04-18
I am a completely new Linux user, as I have been working with Windows for quite a while now. Recently, I decided to begin a project to create a Linux server as Media storage. After installing Ubuntu 12.10, and running Samba to detect the Windows (7) network, I discovered that, while I can see directories on the Ubuntu computer, I cannot see files. And on the Windows 7 computers, I cannot see the Ubuntu computer. 

As I said, I am a VERY new user to Ubuntu, so I ask that any advice be in simple terms. Thank you in advance for your help.

---

### Post by Elfy on 2013-04-18
*Thread moved to **General Help**.*

---

### Post by Novice Networker on 2013-04-18
So here's what I have done so far:
Added network to Samba by going to preferences, then server settings, adding workgroup name, and checking it in the smb.conf file. While I was there, I changed the NetBIOS name to be the same as the Workgroup name.
To be doubly sure, I removed my Win7 computers from their homegroup and created a new workgroup with the same name as I used on the Ubuntu computer.
However, the Ubuntu computer is asking for a Username\password for the Win7 computers. I am not aware that I have one for the workgroup, as I have turned off the Win7 password option in advanced sharing. Also, when I try my Win7 username and password, they are not accepted. Dialogue box says "Password required for share on <Win7 computer name>".

---

### Post by Novice Networker on 2013-04-18
Hmm...well, I am not entirely certain how, but during my mucking about, it seems that my Ubuntu machine is now connected to the network. However, I am only able to modify the Ubuntu machine from one Win7 machine (desktop), while the other (laptop) is only connecting to the other Win7 machine. It does not even detect the Ubuntu computer on the network (it never has), while the desktop does.

---

### Post by CharlesA on 2013-04-19
Try access the Ubuntu machine from the laptop via ip address and that will tell you if it's a name resolution issue or something else.

---

