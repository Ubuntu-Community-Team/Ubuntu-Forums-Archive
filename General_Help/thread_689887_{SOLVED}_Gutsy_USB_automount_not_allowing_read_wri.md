---
title: "{SOLVED} Gutsy USB automount not allowing read write permissions to USB drive"
date: 2008-02-06
forum: General Help
---

### Post by slack31337 on 2008-02-06
**This post could be related to an Ubuntu bug filed at**:  [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/13662](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/13662) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				OK so I have been banging my head against the wall for this. 

I had a SD card that was not auto mounting read write , but if you looked at the permissions it showed user having read write permissions. So I was digging around and I found some threads here and there about a few things. 

First there was all this FSTAB editing .. i didnt want to do that because you shouldn't have to 

then tried the manual mount .. still no go .. read only filesystem

Then there was the this 

"HERE'S THE FIX:
--------------------

Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again. It works :-)

So I did APPLICATIONS --> SYSTEM TOOLS --> CONFIGURATION EDITOR --> opened SYSTEM --> STORAGE --> DEFAULT OPTIONS --> right-clicked on MOUNT OPTIONS --> EDIT KEY --> removed USEFREE option from the list."

[from https://bugs.launchpad.net/ubuntu/+source/hal/+bug/13662]("from https://bugs.launchpad.net/ubuntu/+source/hal/+bug/13662")

and then there was some mention of a corrupt filesystem and an instruction to run 

sudo fsck.vfat /dev/sda1

so I did and there were quite a few errors. I corrected them and still no go

This was stated in some bug report that this is how the kernel should react to this circumstance of a usb disk being heavily corrupted. Apparently it will mount read only to not cause any more damage. Which makes sense . but there should be a gui warning for n00bs like me :) 

So i copied all the good files to my hd , then re-formated the drive fat32, unplugged it and replugged it and it automounted read write .  So i throw back on all the good files and now its all good.


Just thought I would post to save a anyone else the headache :)

---

### Post by jou770d on 2008-03-24
Thanks! iGracias! Merci! Shoukran!
You've really saved me from a lot of work...
This was driving me crazy all day long. I'm so glad that your thread was my first result when I finally got home and searched for a solution..
But I hope that the fsck won't be always necessary cause I can't tell each person that asks me to copy something for him to wait while I fix his usb  (and there are tons of people who do that in university since I'm the only one using linux thus my device won't spread around the annoying win-viruses filling every device on campus).

---

