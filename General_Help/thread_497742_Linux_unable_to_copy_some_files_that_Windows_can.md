---
title: "Linux unable to copy some files that Windows can"
date: 2007-07-10
forum: General Help
---

### Post by kung fu buntu on 2007-07-10
Weird but true... I don't know what else to say...
I was able to copy the files using xp running on vmware.
These are the kind of things that make me want to go back to windows :mad:

> cp: reading `/media/cdrom0/xxx/abc.pdf': Input/output error
Anyone else ever had this problem???

UPDATE: I tried again now and the error didn't occured... :-/ Nonetheless, this is a very serious bug!

BTW is there any way to change the way KDE mounts CDs? I want to set some mount options...

---

### Post by jespdj on 2007-07-10
> **kung fu buntu said:**
> BTW is there any way to change the way KDE mounts CDs? I want to set some mount options...

K Menu -> System Settings -> Advanced -> Disk & Filesystems
Go to Administrator Mode (button at the bottom of the window) and then you can change settings for the disks listed.

---

### Post by kung fu buntu on 2007-07-29
> **jespdj said:**
> K Menu -> System Settings -> Advanced -> Disk & Filesystems
Go to Administrator Mode (button at the bottom of the window) and then you can change settings for the disks listed.

I don't have any menu like that =( and I have KDE 3.5.7. I have:
K-Menu -> System Menu
K-Menu -> Settings

I explored both menus and checked again on KControl but couldn't find any "Disk and Filesystems" entry =/
Any hint?
Thanks

---

### Post by rillip on 2007-07-29
Mmm, he's right, it's a green computer screened icon, says system settings, right above the actions section.  You might edit your kmenu and see if it's just hidden

Also, if it's getting IO errors, that's not a bug, that's your hardware failing.

---

### Post by kung fu buntu on 2007-08-02
> **rillip said:**
> Mmm, he's right, it's a green computer screened icon, says system settings, right above the actions section.  You might edit your kmenu and see if it's just hidden

Also, if it's getting IO errors, that's not a bug, that's your hardware failing.

I don't have anything like that. I guess that's something only available in Ubuntu - I have Debian.

---

### Post by strabes on 2007-08-02
Run kcontrol, open "System Administration" then go to Disk & Filesystems.

---

