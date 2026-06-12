---
title: "Can’t save /etc/fstab in emergency mode"
date: 2020-02-03
forum: General Help
---

### Post by adamantie on 2020-02-03
Hello everyone! 

I’ve only just recently started to get into ubuntu for the purposes of setting up a server so I was following a tutorial on youtube, but I believe that an edit I made in the /etc/fstab file is preventing me from booting normally now. I thought I could just edit the it to remove the stuff I added, but it doesn’t let me save it even as the root user. I’ve tried multiple things now from what I found online, but one in particular caught my attention because of what it said when I tried it so maybe this is the problem? Only thing is that I don’t know what the solution would be so I really hope you guys can help me out. 

What I tried was to type in:

mount -o remount ,rw /

And what I got from doing that was:

mount: /: can’t find UUID=bcce5624-01f2-4f73-b4bb-21eeeb7d2b4e

This is the same thing that shows up in the /etc/fstab file so that’s why I guess it could have something to do with it. Thank you for any help!

[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/2f340c6b-4ba5-44e0-9f82-6b6386dff12f[/IMG]

---

### Post by guiverc on 2020-02-03
I would usually boot a 'live' media (such as your Ubuntu install media) using the 'try ubuntu'.

I would use `blkid` to get the UUIDs for your usual media (ignore the 'live' media you are using now, usually pretty easy to spot) and then ensure the UUID's are correct in your `/etc/fstab` file; given what you said regarding possible incorrect UUIDs.

Note: when using the 'live' media, the `/etc/fstab` file will refer to the 'live' media, so you'll want to mount your normal / partition to say /mnt, then edit the `/mnt/etc/fstab` (or wherever you mounted it).

---

### Post by adamantie on 2020-02-03
Ok so I was able to edit out the lines from /etc/fstab by doing what you suggested and was able to boot into default mode and ssh now. Buuuut it seems that all of my files are read only now for whatever reason even if I use sudo.

---

### Post by Bashing-om on 2020-02-06
adamantie; Hello -

It is unclear what
> 
was able to boot into default mode 

means.

Is this a server that has no GUI , such that you boot to a terminal interface ?
The interface will determine the tools we employ for continued investigation.

Perhaps as you have
> 
 all of my files are read only now 


Will be good to show us you current /etc/fstab file:
```

cat /etc/fstab

```

A file system check/repair from the liveUSB is in order ?

Please post back the result of terminal command:
```

sudo fdisk -lu

```

so we can give specific instruction to perform the check.

[INDENT]we can do that
[/INDENT]

---

