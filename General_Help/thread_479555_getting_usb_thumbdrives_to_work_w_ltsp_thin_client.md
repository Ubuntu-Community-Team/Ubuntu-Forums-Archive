---
title: "getting usb thumbdrives to work w/ ltsp thin clients"
date: 2007-06-20
forum: General Help
---

### Post by mopey on 2007-06-20
I have a pretty plain ltsp setup on feisty.  I installed ltsp-server-standalone, and tweaked the lts.conf file slightly for X and usb compression.

When I plug in USB thumb drives to the thin clients, it does not auto detect them.  However, when I plug thumb drives into the main server, they are auto detected.

Looking at the server edition release ([http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)) it seems like there is an easy way to get the thumb drives to work.  Looking around at what other people did seem like kludges.  For example, this guy (the best tutorial I've found so far) [http://www.skolelinux.no/~klaus/newnotater/x2714.html](http://www.skolelinux.no/~klaus/newnotater/x2714.html) modifies the floppyd program.  Other people do junk with smb.  

My question is, are there any recommendations to get the thumb drives to be auto detected on the thin clients?

---

### Post by mopey on 2007-06-20
hehe.  This is my second post ever on this forum and it's also the second to go unanswered.  Maybe I'm wording the questions badly?

Anyway, I think I figured it out.  'apt-get install ltsp-server-standalone' doesn't install the fuse ltspfs.  Install that, and everything _should_ work.  Simple solution, but it was hard to find this answer.  I ended up going to #ltsp, where extremely helpful.

---

### Post by mopey on 2007-06-20
If you're doing what I say above, be sure that your user is in the 'fuse' group.

Actually, my usb stuff is not working, although the local client cd and floppy are mounting.  I'll keep looking in to it.

---

### Post by mopey on 2007-06-20
I did a complete reinstall of the chroot

```

rm -r /opt/ltsp/i386
ltsp-build-client --arch i386

```

And still, although the local hard drives and the cd rom and the floppies are detected, the usb is not.  The usb _is_ automatically detected and mounted when I plug it into the server.

Here are all the drives that are mounted:

```

$ ls -l /media/user/
total 0
?--------- ? ? ? ?                ? /media/superuser/boot
?--------- ? ? ? ?                ? /media/superuser/cdrom
?--------- ? ? ? ?                ? /media/superuser/floppy0
?--------- ? ? ? ?                ? /media/superuser/scsidisk-sda1
?--------- ? ? ? ?                ? /media/superuser/scsidisk-sda3

```

This is on the client with hard drives.  I have also tried with other usb ports, and other thin clients.  I think it's unlikely that this is a hardware issue.

Any help?

---

### Post by menoz on 2007-08-06
HI! I do not have an answer nor any advice, but I only wanted to say that I've got the same problem with debian etch and ltsp 5..
Can someone help us??

Thanks!:):):):):)

---

### Post by bazz on 2007-11-03
Just wanted to say thanks!!!! I too have been looking all over on how I could use the local cdrom of the thin client, and your post solved my problem.
I wish I could help you out but this machine does not have usb, so there is no way to test.
I have the same problem as you with the post as well. Most of my posts go without any answer, and I usually figure out the problem. I’m guessing its because no one has an answer to the question, or its like you say….maybe I just worded it wrong or posted in the wrong place.
Anyway….Thanks!!! You get to be the man!!!

---

### Post by Tuge on 2008-01-02
This comes "a bit" late but I figured I'll post this anyway.

I ended up having huge issues with all the forementioned not mounting on Gutsy using active directory authentication. I remember someone posting earlier about same thing but couldn't find the post anymore. The thing I did was to change the group fuse uses on 'etc/udev/rules.d/45-fuse.rules' and then setting up each user to be part of this group on AD ... Works like a charm!

The only problem I'm currently seeing is that on every reboot of the server for some reason i have to restart udev to properly fetch the groups and stuff (/etc/init.d/udev restart)

---

