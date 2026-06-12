---
title: "Problems with Samba File Sharing"
date: 2008-03-22
forum: General Help
---

### Post by ThePorthos on 2008-03-22
Hello guys,

I've just been trying to setup my extra computer as a file sharing platform for the rest of my networked pc's around my house. I install Samba and SMB, and the GUI front ends. I have tried following several online tutorials and everything is going well into in some point in the tutorials, I come across a command that in my konsole doesn't seem to be recognized, or have to edit a conf file that doesn't exist.

On my install of Samba, the only .conf file in my samba folder is smb, and then theres smb commands. I do not have smbusers or smbpasswords. Is there a reason for this? Is there something I may have neglected to install with apt-get, or am I just being dumb. I mean all I want to do is share files its like ARGHY ARGHY !!  I can pull files from my other windows PC's and browse the home network. But sharing a folder on the Ubuntu machine is just XD.


I can see it listed, but when I try to log in to the share via my windows computers, it prompts me for a username and password, and I use my login I have on my Ubuntu box, and it says its invalid?

Please Help! :confused:

---

### Post by tvtech on 2008-03-22
pop into terminal 

username@localhost:~$smbpasswd -a username
this should allow you to assign a password to your username for smb shares.   then you should be able to enable them by going to 

System>Administration>Shared folders

---

### Post by ThePorthos on 2008-03-25
Thanks, Will try right after I finish my reformat on my Ubuntu Machine, will let you know how it goes.

---

