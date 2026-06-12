---
title: "Home folder files on desktop"
date: 2008-02-17
forum: General Help
---

### Post by jeffreyldavidson on 2008-02-17
Somehow my home folder files are not on my desktop. I cannot get rid of the files for it deletes them also in my home folder. There is a home and desktop folder but it seems to be duplicated and I cannot get the files off of the desktop.

Help

---

### Post by Flyingjester on 2008-02-17
I'm confused.. are these files on, or not on your desktop?

---

### Post by jeffreyldavidson on 2008-02-17
They are both on the desktop and in my home fiolder. But if I delete them off of the desktop it also deletes them from my home folder

I thiink it may due to a missing desktop folder but I cannot create a new one, it won't allow it to be created.

---

### Post by Flyingjester on 2008-02-17
did you delete said desktop folder? and what is the message you get when you try to create a new one?

---

### Post by jeffreyldavidson on 2008-02-17
This is the message,,,

The item could not be renamed.
Sorry, couldn't rename "untitled folder 2" to "Desktop".

I really do not know how this happened or I got to this point.

---

### Post by Flyingjester on 2008-02-17
kk, try navigating to your home dir in terminal

> cd /home/yourusernamehere

, and typing 

> sudo mkdir Desktop

, then 

> sudo chown yourusernamehere /home/yourusernamehere/Desktop

---

### Post by voteforpedro36 on 2008-02-17
Try under Accessories -> Terminal, type:
sudo mv "untitled folder 2" Desktop

You'll have to type in your password, and it won't show up in stars, just type it and press enter.

But do you have a "Desktop" folder in your home folder, or do the things in your home folder show up on your desktop?

EDIT: Actually what he said ^^

---

### Post by jeffreyldavidson on 2008-02-17
This is the message I get


\mkdir: cannot create directory `Desktop': File exists

Although I cannot see a Desktop folder.

---

### Post by Flyingjester on 2008-02-17
wow.. dunno man, i was kinda fishin, sorry i can't help any further, i have no idea what happened.

---

### Post by NineseveN on 2008-02-18
Press Alt+F2, then type
gconf-editor
Navigate to apps>nautilus>desktop and check/uncheck the boxes for what you want to be visible or not visible on your actual desktop.


Unless of course I'm misunderstanding your problem, which just might be the case.

---

