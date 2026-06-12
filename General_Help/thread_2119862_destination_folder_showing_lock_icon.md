---
title: "destination folder showing lock icon"
date: 2013-02-25
forum: General Help
---

### Post by mreos on 2013-02-25
Moved existing folders from laptop to new shared folder on PC and each of the folder on the PC has a lock icon on it. 

laptop is ubuntu 12.04 --> pc is ubuntu 12.10

What can I do now to fix all the folders?
What can I do in the future to prevent this from happening?

TIA

---

### Post by community on 2013-02-25
Can you access those folders showing lock symbols?  To where did you copy, to home folder or any other drives?

---

### Post by rnerwein on 2013-02-25
> **mreos said:**
> Moved existing folders from laptop to new shared folder on PC and each of the folder on the PC has a lock icon on it. 

laptop is ubuntu 12.04 --> pc is ubuntu 12.10

What can I do now to fix all the folders?
What can I do in the future to prevent this from happening?

TIA
hi
that means you are not the owner of the folder or you get no write permissions.
what you can do is: open a terminal and: cd /directory where are locked files are.
chmod 755 folder_name.
or when you are not the owner (ls -ld folder_name) then you have to change it:
sudo chown your_account:your_group folder_name and chmod 755 folder_name.
that's it (i guess you got another user-id on the second box)
ciao

---

### Post by mreos on 2013-02-25
> **community said:**
> Can you access those folders showing lock symbols?  To where did you copy, to home folder or any other drives?

I created a share folder on the PC within the Downloads folder. I can view the contents and access them.

---

### Post by mreos on 2013-02-25
> **rnerwein said:**
> hi
that means you are not the owner of the folder or you get no write permissions.
what you can do is: open a terminal and: cd /directory where are locked files are.
chmod 755 folder_name.
or when you are not the owner (ls -ld folder_name) then you have to change it:
sudo chown your_account:your_group folder_name and chmod 755 folder_name.
that's it (i guess you got another user-id on the second box)
ciao

I will give the 'chmod 755 folder_name' a try. Since there are many folders filled with files, can I 'chmod 755 *' instead?

I'm moving everything off the laptop so I can get OS reinstalled.  Would creating the same ID as the PC prevent this issue in the future?

---

### Post by mreos on 2013-03-04
@rnerwein

Here is the message I'm getting when using your command [COLOR=#0000cd][/COLOR]'[COLOR=#0000cd]**chmod 755 folder_name**[/COLOR]'

> chmod: changing permissions of `photos/': Operation not permitted

---

### Post by mreos on 2013-03-07
Since the command that was suggested is not working, can anyone tell me what I can do to get the folders to unlock?

---

### Post by Frogs Hair on 2013-03-07
[COLOR=#000000]Would creating the same ID as the PC prevent this issue in the future?

Having the same owner name may help. I use Ubuntu One for folder transfer to my new Ubuntu versions every six months, but have always used the same user names.  [/COLOR]

---

### Post by mreos on 2013-03-12
Thanks, I'll try to use the same ID in the future.

Anyone have a solution for folders showing the lock icon? How can I unlock and then delete?

---

### Post by mreos on 2013-03-17
I've been looking and looking but still can't find any solution to this problem

Please help!!

---

### Post by markling on 2013-05-19
Nothin.

---

