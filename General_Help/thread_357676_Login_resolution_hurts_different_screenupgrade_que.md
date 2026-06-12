---
title: "Login resolution hurts different screen/upgrade question"
date: 2007-02-09
forum: General Help
---

### Post by Entity` on 2007-02-09
My login screen displays in 1280x1024 and I want it to run in 1024x768.  I dont know how to change it.  I cant find it anywhere how to do that and im using a different moniter and the resolution is hurting the screen.  Yea, it can display it, but i dont think it can support it.

Meanwhile I wonder If I can upgrade to version 6.10 from 5.10 (current) using only a CD I recently created.  The CD works fine and all but when I tried to install it to my (slow) server, It gave me a kernel panic and hung from there, forcing me to use an older version (5.10).  Would it work?  How do you do it?  I need to know because I dont have the connection speed to download over 600MB for an upgrade.  Estimated it would take over 12 hours and the other inhabitants in this house are quite impatient.

---

### Post by gcornett on 2007-02-09
I ran into this recently, too.  Open a terminal screen and type the following

sudo gedit /etc/X11/xorg.conf

Locate the Section "Screen"

You should see several Subsection "Display" entries with several resolutions listed for each.  Delete the 1280x1024 in all of them - assuming you never want to use that resolution.

Save the file and reboot.  You should be in 1024x768 resolution now.

Worked for me.

Can't help you with the other question.  Good luck.

---

### Post by Entity` on 2007-02-10
Thanks, now can someone else please shed some light on how to upgrade to 6.10 using only the CD.  Im sure it can be done, but don't know how.

And has anyone ever found an easy way to mount NTFS drives WITH READ & WRITE access???
Im trying to migrate entirely to linux without the using windows as a crutch.  

==OR==

Is there a way to convert NTFS drives to RieserFS or simalar without moving any data from the drive in question and still be able to retain the data after conversion??

I know Partition Magic can do this, but the version I have DEMANDS a stupid Floppy drive; of which I do not have the luxury of nor do I have the luxury of transferring data from the drive(s) in question.

As an afterthought can someone please give me the Command lines to install AVG free for LINUX on here?

Thanks in advance for all your help.

---

