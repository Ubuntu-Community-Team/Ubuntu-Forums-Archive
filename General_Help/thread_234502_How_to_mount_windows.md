---
title: "How to mount windows"
date: 2006-08-11
forum: General Help
---

### Post by Alexeon Lanar on 2006-08-11
I followed the instructions in this guide:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)
and the Windows folder shows up in the media folder, but its empty. I also tried the other method they suggested, to mount it on the spot, not at startup, but that didnt work either.
Can someone tell me what Im supposed to do? My NTFS partition is at dev/hda2, so I didnt mess up and put hda1 like they did.

Thanks! :lol:

---

### Post by Zalbor on 2006-08-11
There's a serious mistake in that wiki: It supposes your windows partition is /dev/hda1 without telling you to change that if it isn't.
So if your win partition isn't /dev/hda1, change that part in fstab to what it is. If your win partition IS that one, then I can't think what the problem would be.

---

### Post by Alexeon Lanar on 2006-08-11
I know Im supposed to change it, so I did. Mine is dev/hda2 so thats what I put. That isnt the problem...

---

### Post by Patrick-Ruff on 2006-08-11
mounting windows eh? for some reason my linux laptop automatically mounted my windows partition onto the desktop :D its whiked awesome, I can access all my windows stuff through linux, as well as write folders and everything on to it. so yeah its awesome, I don't know how to accomplish it, but it works for me so yeah good luck.

---

### Post by DimaIL on 2006-08-11
I think [this guide]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") can help you.

Dima

---

### Post by Zalbor on 2006-08-11
I thought of something else. What I'm going to say might be a load of ****, but it surely won't hurt to try.
Leave out the nls=utf8 part. Is it possible that your ntfs partition's files won't display in a utf8 coding?

---

### Post by Alexeon Lanar on 2006-08-13
Thanks for the help. I was gone for a while so I couldnt reply. My Windows partition just appeared when I turned on Ubuntu. I hadnt turned it on since I tried to mount Windows. Oh well.


Thanks for the help! :lol:

---

