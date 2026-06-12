---
title: "[SOLVED] blank screen and sharing swap partion"
date: 2008-01-28
forum: General Help
---

### Post by mohbana on 2008-01-28
Hi everyone,

1) I run into problems getting Ubuntu to run on a 8800 512mb gts i think its g92 chip but i am not sure, anyhow after installing the nvidia drivers all was good after everything boots that it.  The issues are

i) after choosing ubuntu in grub the screen goes totally blank until i reach the login screen, it doesn't display the status or anything, the same thing happens when i shut down/restart.  The monitor powers down for like 30 second it says no input signal found and then shows the login screen althought its working shouldn't it display the status?

2) I seem to be getting some problems when trying to share a swap partion between Fedora and Ubuntu don't know why.  Just take a look at the pic its not registering that I have a partion.

[http://img150.imageshack.us/img150/9517/systemmonitorlr5.png]("http://img150.imageshack.us/img150/9517/systemmonitorlr5.png")

3) Can someone take a screenshot of the forum i want to see how the fonts come out, mine is attacthed please comment if you dont think its right.

[http://img246.imageshack.us/img246/756/ufontqz1.png]("http://img246.imageshack.us/img246/756/ufontqz1.png")



But in general Ubuntu is great :).  Everything is straight forward, though i believe installing development problems could be easier.

---

### Post by accatagon on 2008-01-28
As far as the second problem, is /dev/sda5 your swap partition? If so, try "sudo swapon /dev/sda5" and see if that helps. If it does, then it is a boot problem, but I personally am not sure where in the boot-scripts it is supposed to execute that statement.

As far as the third: Yes, that is the way they look. A bit odd, huh?

---

### Post by mohbana on 2008-01-28
> sudo swapon /dev/sda5
Yep it works, i tried that in fedora aswell and it mounted it but the issue is i guess is after i boot into the other distro and boot back into ubuntu i'll have to do this again and i am not hibernating.


The fonts are different to when i intially installed ubuntu they where more crisp.   I'll put in the live cd and take a snapshot when i get a chance.

---

### Post by accatagon on 2008-01-28
Type the command
```
ls -l /dev/disk/by-uuid | grep sda5
```

The result should look something like this:
```
lrwxrwxrwx 1 root root 10 2008-01-28 09:51 334966ce-e1d3-4b8b-944b-e657faf5d5cf -> ../../sda5
```

The corresponding segment in your fstab should look like this(oddly, my swap partition is also sda5):
```
# /dev/sda5
UUID=334966ce-e1d3-4b8b-944b-e657faf5d5cf none            swap    sw              0       0
```
Note that the UUID is the same as the one from /dev
If this is not the case, then we have found your problem, and you have two options.
[LIST=1]
[*]Put the correct UUID in
[*]Put "/dev/sda5" in in place of the "UUID=. . ." stuff
[/LIST]

---

### Post by mohbana on 2008-02-04
yep thanks it worked

---

