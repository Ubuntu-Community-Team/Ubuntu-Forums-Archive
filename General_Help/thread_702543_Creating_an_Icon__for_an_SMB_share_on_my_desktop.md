---
title: "Creating an Icon  for an SMB share on my desktop"
date: 2008-02-20
forum: General Help
---

### Post by briandorling on 2008-02-20
Hi,
I have an SMB folder on my desktop, that I somehow created. Its for a share available via smb. So the URI looks like this:

smb://xxxxxxx%3Bbrian@slug1/mp3

Where brian = user and xxxxx = password. Slug1 = server, mp3 = share name

If I look at properties, type it says "x-directory/smb-share" 

I cannot find a way to create another such icon, for a second share. The nice thing about this icon it is still shown when the share is not mounted. When I click the icon it asks for a password and then mounts it.
Exactly what I need. 

I looked through home to see if I could find the file associated with this icon, no luck.
So how do I do this please? Running on Ubuntu V7.10.

Cheers Brian

---

### Post by freelinuxhelp on 2008-02-20
Go to places, connect to server.

---

### Post by freelinuxhelp on 2008-02-21
Have any luck with this?

---

### Post by briandorling on 2008-02-22
Hi,
sorry it took so long to answer. If I do what you suggest, then as soon as I unmount the volume it removes the Icon from the desktop. I want the Icon to stay there, and to have the userid and pw kept so I dont need keep entering it myself.
But I have one icon for a share, it is on my desktop and in the places menu list, and it doesn't go away. And I have no idea how it got there.

Cheers Brian

---

### Post by freelinuxhelp on 2008-02-22
if you unmount the other icon, does it go away?

---

### Post by briandorling on 2008-02-22
Yep, sure does. So I guess for some reason it was being automatically mounted.

Anyway, is there anyway to create a "mount this drive" icon on my desktop?

Cheers Brian

---

### Post by freelinuxhelp on 2008-03-08
One way to do this is to write a bash script that mounts it for you.
I think I would just leave it mounted though; that way, it's there whenever you need it.

---

### Post by dcstar on 2008-03-08
> **briandorling said:**
> Hi,
I have an SMB folder on my desktop, that I somehow created. Its for a share available via smb. So the URI looks like this:

smb://xxxxxxx%3Bbrian@slug1/mp3
.........

Simply create a Launcher with the** LOCATION** of: smb://xxxxxxx%3Bbrian@slug1/mp3

---

