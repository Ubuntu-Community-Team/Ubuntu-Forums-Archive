---
title: "GDM could not write to authentication...blah"
date: 2007-12-11
forum: General Help
---

### Post by dchurch24 on 2007-12-11
Hi all,

my own stupid fault but was downloading some files and left the machine on for a few days, I was not here, so on my return the disc had run out of space.

I deleted a few large files (about 60gb) and then rebooted.

Since then I get the "GDM could not write to autheitication file" etc...

I have ssh'ed into the machine and deleted the .Trash files and cleaned a lot of stuff with RM in my home folder - I have about 100gb spare now

I try to log in and I still get the same error

Doing a DF gets me:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            368970852 355953564         0 100% /
varrun                 3967108       256   3966852   1% /var/run
varlock                3967108         0   3967108   0% /var/lock
procbususb             3967108       124   3966984   1% /proc/bus/usb
udev                   3967108       124   3966984   1% /dev
devshm                 3967108         0   3967108   0% /dev/shm
lrm                    3967108     38972   3928136   1% /lib/modules/2.6.20-16-generic/volatile
/dev/sdc1            244196348  77066868 167129480  32% /mnt/win2
root@frontroom-ub:/home/dave# Filesystem           1K-blo


```

so it looks like I am still using 100% of the disk, and when I try to log in I get the same GDM error.

I am at my wits end, and I'm not that happy about having to use my XP laptop to be honest, I'm getting used to things just working!! ;-)

I've googled it, but the suggestions are all "CTRL-ALT-F1 and then delete some stuff", I've done that, bit the OS doesn't seen to realise that I have!

Please help, I am getting desperate now!

---

### Post by taurus on 2007-12-11
Boot into recovery mode from GRUB menu and run

```
apt-get clean
df -h
```
That should clear out your cache, giving you some space to log in as a regular user.  You can reboot your machine with

```
shutdown -r now
```

---

### Post by pieisgood4589 on 2007-12-11
Wow. That's harsh... I was going to recommend a fresh install after backing up your important files but...

---

### Post by dchurch24 on 2007-12-12
Hi, thanks for that.

I booted into recovery mode, did as you suggested, but it still says:

```

/dev/sdb1             352G  340G     0 100% /

```

Does that not mean that there is 12gb free?

I have also deleted (rm) quite a few very large files I had on that volume (ubuntu and kubuntu iso's), and yet although they have dissapeared it seems to have made no difference to the amount of disk usage.

I am at a complete loss.  I don't really want to be reinstalling if I can help it.

The funny thing is, from my XP laptop I can VNC into the Linux box quite happily.

---

### Post by dchurch24 on 2007-12-12
Should this be registered as a bug do you think?

If my mum or dad had this error they would be buggered (ha, as am I at the moment) - they can use Ubuntu quite happilly, but to fix this would give them trouble.

---

### Post by dchurch24 on 2007-12-12
I just don't understand this - I've cleared 13gb of stuff and still I get the same error?

Just how much space does it need?

I don't understand when it says that /dev/sdb1 has used 100% when it shows 13gb spare?

---

### Post by dchurch24 on 2007-12-12
Oh God, I don't want to have to go back to Windows.

I have cleared tons of space now, but I still get the same error - what am I doing wrong?

---

### Post by dchurch24 on 2007-12-12
It is possible to actually delete files from Ubuntu isn't it?

I know it sounds like a stupid question, but I've VNCed into the box, deleted some HUGE files - about 10gb worth, and yet when I go into the .Trash folder there is nothing there.

---

### Post by dchurch24 on 2007-12-14
They appear to have been moved to the "deleted items folder", but I don't know how to access this from the console?

Any idea?

---

