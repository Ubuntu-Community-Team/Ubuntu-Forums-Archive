---
title: "Share folders in virtualbox-ose windows xp"
date: 2008-01-28
forum: General Help
---

### Post by Masterj15 on 2008-01-28
I need help trying to share folders in the virtualbox -ose. I have windows xp runnning in the virtualbox ose and I have guess addition installed. When I go to the terminal and Type vboxmanager the terminal says that their is no comand. I tried doing everything I can think of and nothing works. Can someone please help me.

---

### Post by codesplice on 2008-01-28
first up, capitalization is important in the terminal.  Try "VBoxManage".

To set up a shared folder (I'm assuming between the host and guest OSes?), there are a few things you'll need to do.  First, establish a shared folder from within the VBoxManage app.  Then, in windows, run in the command prompt
```
net use x: \\vboxsvr\Sharedfoldername
```

You *should* then have a network folder mounted on your Guest that is actually hosted by your host OS.  

Good luck!

---

### Post by Masterj15 on 2008-01-28
[QUOTE=codesplice;4225056]first up, capitalization is important in the terminal.  Try "VBoxManage".

as far as the next thing: It says the local device name is already in use. I tried alot of file but they all say the same thing.

---

### Post by mynamesforrest on 2008-04-25
It's kinda odd because you can't browse \\vboxsvr for the folder, but you CAN map directly.

Either type net use x: \\vboxsvr\sharename 

Or right click on My Computer and Map Network drive, enabling the option to reconnect on logon

---

