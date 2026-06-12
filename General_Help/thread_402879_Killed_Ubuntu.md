---
title: "Killed Ubuntu"
date: 2007-04-06
forum: General Help
---

### Post by jar3232 on 2007-04-06
OK, I know I should have a backup, but I am just not that far along in the install...I am still in my first couple of days of my first ubuntu experience and just started to get things working, barley...I was trying for the millionth time to get my wifi working (Entire problem in itself), I installed madwifi and restarted, when I did, were the login screen should be I get a pretty blue screen (RRRRRRRR) that says...

> Failed to start the X server (Your graphical interface).  It is likely that it is not set up correctly.  Would you like to diagnose the problem? Yes No

EE Failed to load module "nvidia" (module does not exist, no drivers available
Fatal server error, no screens found...

SO, what did I do, the graphics have been set for several days and working great and I did many restarts in between, I didn't think I was editing anything close to the part of the kernel with graphics...Someone please help this poor nooooob...

EDIT: I tried running recovery mode without any luck...

---

### Post by Atrio05 on 2007-04-06
ok well first when you boot up hit ctrl and F1 then try to get to your xorg.conf if you could post that on here i'm sure it would help us to help you.

type:   sudo nano /etc/X11/xorg.conf and try to post it on here

if all else fails reinstall and then for your wifi use NDIS Wrapper that will allow you to use the windows driver for your wifi card and that should work just fine for you.

edit:

yes try below before you reinstall i forgot about doing that!

---

### Post by Arisna on 2007-04-06
Before you get to the "reinstall" step, try this command in the Ctrl-Alt-F1 console:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jar3232 on 2007-04-06
> type: sudo nano /etc/X11/xorg.conf and try to post it on here

It came up to a blank screen...

And x conf did work either...

What's the command to reinstall

...and I used to think I knew what I was doing...

---

### Post by cisforcojo on 2007-04-06
By blank screen do you mean NOTHING on the screen or a blank text file? 
Are you SURE you typed the path correctly, capitals and everything? (I mean X11, not x11)

If so, to reinstall, you're going to have to reuse your LiveCD to reinstall it (if none of hte other suggestions have worked).

Next, you should DEFINITELY back up your /etc/X11/xorg.conf

It's VERY easy to mess this file up. Just one typo and your X (GUI) won't load. When this happens, rather than messing around with a text-based text editor, I find it's much easier to just use the backup file instead. 

Hope ya don't have to reinstall!

---

### Post by jar3232 on 2007-04-06
No, nothing is working...Very frustrating...

So I am trying to start fresh, reinstall ubuntu and give it one more shot...I go through the install and manually set up the partitions, I see my xp, old ubuntu, and swap, select what i want to reformat t, but when I get them all selected and checked, I keep getting an error "No Root System"...What am I doing wrong...I searched around and found this link, but it doesn't help...

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Here is a screen shot of my poor partition list if it helps, At this point it is sheer determination that this works...

[IMG]http://img502.imageshack.us/img502/1631/screenshot1mm8.png[/IMG]

:mad:

---

### Post by jar3232 on 2007-04-07
^ Bump...Anyone?

---

### Post by Maestro23 on 2007-04-07
Try deleting  the old Ubuntu partiton and swap.  Then re-create those partitions in the unused space from scratch.

---

