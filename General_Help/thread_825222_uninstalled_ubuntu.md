---
title: "uninstalled ubuntu"
date: 2008-06-10
forum: General Help
---

### Post by sunaruni on 2008-06-10
I just deleted my ubuntu partitions, but now I can't boot windows because GRUB is missing. How can I install grub again? Right now, I have to run ubuntu off the cd, so that's all I have until I get it fixed. Help a brotha out?

---

### Post by ibuclaw on 2008-06-10
GRUB is not needed (You'll find out why in a minute).

Which partition is Windows on?

Can you mount the drive it and post the output of this terminal command
```
df
```

Regards
Iain

---

### Post by muadnu on 2008-06-10
Do you want to reinstall Ubuntu or just be able to boot into Windows?

---

### Post by sunaruni on 2008-06-10
When I boot I get GRUB ERROR 22, I believe. No terminal or anything. I just want to be able to boot into Windows, I'm done with ubuntu.

---

### Post by ibuclaw on 2008-06-10
Sunaruni,

Boot up into the Ubuntu LiveCD and,
[LIST]
[*]Mount your main Windows partition.
[*]Open up a terminal
[*]Type in the command```
df
```and post the output of that command in your next post please. So I can give you the right instructions in order to restore Windows MBR.
[/LIST]
Thank-you.

Regards
Iain

---

### Post by muadnu on 2008-06-10
Sorry to hear that... In any case, I believe you can get it fixed with the XP installation CD, if you have it. You need to choose "repair system" or something like that and then choose somewhere "fix mbr". That should get your computer booting into Windows again. As you see, I'm not sure about the exact steps, but I'm almost sure it can be done, and you can try to search it on the web.

---

### Post by ibuclaw on 2008-06-10
> **muadnu said:**
> Sorry to hear that... In any case, I believe you can get it fixed with the XP installation CD, if you have it. You need to choose "repair system" or something like that and then choose somewhere "fix mbr". That should get your computer booting into Windows again. As you see, I'm not sure about the exact steps, but I'm almost sure it can be done, and you can try to search it on the web.

Muadnu, [Read Here.]("http://ubuntuforums.org/showthread.php?t=799895")

I know exactly how to do it. I just want to make sure I know which drive the Booted Windows Partition is on **before** I paste the command.

Regards
Iain

---

### Post by sunaruni on 2008-06-10
There's only one drive right now. I deleted everything else.

Plus I have no idea how to mount Windows from the ubuntu live boot.


EDIT: Oh yeah, my XP OS disc is cracked haha.. So that's a no-go there.

---

### Post by muadnu on 2008-06-10
> **tinivole said:**
> Muadnu, [Read Here.]("http://ubuntuforums.org/showthread.php?t=799895")

I know exactly how to do it. I just want to make sure I know which drive the Booted Windows Partition is on **before** I paste the command.

Regards
Iain

Well, I thought it was worth to give it a try, since it might be easier. But from the last post it seems that it's not even an option...

---

### Post by ibuclaw on 2008-06-10
/me sighs :)

OK!
In the Ubuntu Terminal ("**Applications>Accessories>Terminal**")

And copy and paste this command:
```
sudo fdisk -l
```
And paste the output (perhaps I should've ask that to begin with).

Sorry about the wait. It's just that I'd feel better knowing what /dev/sd** your drive is before I hand out a (safe, but risky when misused) command.

Regards
Iain

---

### Post by sunaruni on 2008-06-10
> **tinivole said:**
> /me sighs :)

OK!
In the Ubuntu Terminal ("**Applications>Accessories>Terminal**")

And copy and paste this command:
```
sudo fdisk -l
```
And paste the output (perhaps I should've ask that to begin with).

Sorry about the wait. It's just that I'd feel better knowing what /dev/sd** your drive is before I hand out a (safe, but risky when misused) command.

Regards
Iain
Well, the partition manager says it's /dev/sda1. Filesystem says "ntfs" and under flags it says "boot".

If that's not what you need, I'll give that a shot.

---

### Post by ibuclaw on 2008-06-10
Yes!
That will do.

Still need to open a terminal though :D

OK, copy and paste these into the terminal **one line at a time**.

```

sudo apt-get install syslinux

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```
Wait around 5-10 seconds for each command to finish.

Now reboot and remove the LiveCD.

And fingers crossed, The Windows logo will be the first thing that you see when you next boot up.

PS:
So long, sorry it hasn't been what you expected.
We all know the pains of how it feels to learn to administer a completely new system.
But you are always welcome back to our friendly community!

Regards
Iain

---

### Post by sunaruni on 2008-06-10
Ahhh, thanks man.. I'll give that a shot in a bit, I'm going out for a smoke with a friend. I'll let you know what happens.

---

### Post by ibuclaw on 2008-06-10
/me wishes you the best of luck!

Regards
Iain

---

### Post by lisati on 2008-06-10
> **sunaruni said:**
> Ahhh, thanks man.. I'll give that a shot in a bit, I'm going out for a smoke with a friend. I'll let you know what happens.

Keep on smiling!

---

### Post by sunaruni on 2008-06-10
Just put those two lines into the terminal. BTW, I'm not completely ubuntu illiterate, I just didn't know how to mount windows haha.. I had enough problems getting it to work initially that I learned it pretty good. Thanks for that, though. I'll restart and tell you what happened, just in case.

---

