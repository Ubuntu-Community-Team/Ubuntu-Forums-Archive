---
title: "how to exit to command line?"
date: 2007-02-23
forum: General Help
---

### Post by Mateo on 2007-02-23
hello, I want to know how to exit to the command line, so I can unmount the hard drive and run fsck on it.  thanks.

---

### Post by taurus on 2007-02-23
You want to get to command line from Gnome or from where exactly?

---

### Post by Mateo on 2007-02-23
Yes, my computer loads to gnome.  I then want to get to the command line.  That means I want to exit gnome completely and be just at the command line.

Also, once I get there, how do I get back to gnome (is 'startx' the command?)

thanks.

---

### Post by cmost on 2007-02-23
CTRL+ALT+Backspace kills the X server.  :-)

---

### Post by Mateo on 2007-02-23
ctrl+alt+backspace goes back to the login manager, though.  I want to go to the command line.

---

### Post by Qew on 2007-02-23
Tried ctrl+alt+F1? To get back out of the command line from doing that, you just use ctrl+alt+F7.

---

### Post by Mateo on 2007-02-23
i'll give that a try later, thanks.

---

### Post by bobpaul on 2007-02-23
What's wrong with gnome-terminal? It's in applications, or accessories, or something, or you can Alt+F2 and type gnome-terminal

If you ctrl+alt+backspace multiple times quickly enough, it will not relaunch the x session. You can then use 'sudo /etc/init.d/gdm restart'

---

### Post by punx45 on 2007-02-23
ctrl+alt+F1 will take you to a full screen console, but GDM will continue to run.   if you are doing this for performance purposes, go to the console, and then stop GDM.
```
/etc/init.d/gdm stop
```

i think that should do the trick.   then if you want to go back to gnome later, just reverse the process.  

/etc/init.d/gdm start
ctrl+alt+F7

---

### Post by llamakc on 2007-02-23
Or, just type:

ctrl-alt-F2

or ctrl-alt-F3

or ctrl-alt-F4

or ctrl-alt-F5

or ctrl-alt-F6

and type ctrl-alt-F7 to get back to your X session.

---

### Post by Mateo on 2007-02-23
> **bobpaul said:**
> What's wrong with gnome-terminal? It's in applications, or accessories, or something, or you can Alt+F2 and type gnome-terminal

If you ctrl+alt+backspace multiple times quickly enough, it will not relaunch the x session. You can then use 'sudo /etc/init.d/gdm restart'

like I said, I want to run fsck.  So to do that I have to unmount the hard drive.  Doing that within gnome would be a little like trying to change the oil in your car with the engine running, wouldn't it ;)

---

### Post by Chake99 on 2007-02-23
If you have two hard drives, boot from the one you don't want to fsck, if you have only one boot from a livecd (does the ubuntu livecd fsck?)

---

### Post by taurus on 2007-02-23
> **Mateo said:**
> like I said, I want to run fsck.  So to do that I have to unmount the hard drive.  Doing that within gnome would be a little like trying to change the oil in your car with the engine running, wouldn't it ;)

Do that from the LiveCD.

---

### Post by Mateo on 2007-02-23
why can't i just do it this way?  loading to a livecd takes forever.

---

### Post by taurus on 2007-02-23
Because you cannot fsck the partition you are using.  And you cannot unmount it because you need to use it.  It's like a catch-22.

---

### Post by po0f on 2007-02-23
Mateo,

You won't be able to fsck the root filesystem if you aren't booted into an environment that doesn't have it mounted (ie, a live CD).

---

### Post by Mateo on 2007-02-23
> **taurus said:**
> Because you cannot fsck the partition you are using.  And you cannot unmount it because you need to use it.  It's like a catch-22.

the system does it every 30 boots, how is it able to do it and I'm not?

---

### Post by llamakc on 2007-02-23
It does so before mounting the partitions.

---

### Post by ~LoKe on 2007-02-23
Maybe he wants to fsck a partition that /home is on? o_O

---

### Post by Mateo on 2007-02-23
> **llamakc said:**
> It does so before mounting the partitions.

how does it run fsck if the partition isn't mounted?  isn't fsck a program in the hard drive?

---

### Post by ~LoKe on 2007-02-23
**EDIT:** Hm..not so sure now.  It must be mounted immediately or it wouldn't be able to read from /boot, but then it must unmount because it runs fsck...or maybe certain parameters are available for fsck without requiring an unmount (check for problems, but not correct?).

---

### Post by Mateo on 2007-02-23
> **~LoKe said:**
> **EDIT:** Hm..not so sure now.  It must be mounted immediately or it wouldn't be able to read from /boot, but then it must unmount because it runs fsck...or maybe certain parameters are available for fsck without requiring an unmount (check for problems, but not correct?).

yeah, you are following my reasoning.  quite a paradox, but it does it somehow.

---

### Post by ~LoKe on 2007-02-23
It appears you can fsck a mounted drive, so long as you aren't trying to repair it.

> loke@x04d:~$ sudo fsck /home
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
loke@x04d:~$ sudo fsck -N /home
fsck 1.40-WIP (14-Nov-2006)
[/sbin/fsck.ext3 (1) -- /home] fsck.ext3 /dev/sda1 

---

### Post by po0f on 2007-02-23
Mateo,

It probably loads the program in memory before unmounting the drive for the fsck.  Anyway, you could try [this](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/) maybe:

```
[font="Courier New"]$ sudo touch /forcefsck[/font]
```

and just reboot.

---

### Post by Mateo on 2007-02-23
good idea, i'll give that a try

---

### Post by bobpaul on 2007-02-26
The bootup fschk is done with the partition as read-only, AFAIK. After the kernel loads, the root partition is mounted read only, then the boot continues. When it comes time, the /etc/fstab file is read and those partitions are mounted per the files instructions (which makes your / read-write)

If you want to fsck your /, I would recommend the liveCD, as other have said. You can also do it with recovery mode (single user mode) although you'll have to issue some mount command like:
```
mount remount something something, search google or read manpage ;)
```

If you can't figure that out--sorry I can't be more specific--and the liveCD takes too long, try a smaller liveCD from another distribution, such as puppy linux or one of the gentoo minimal liveCDs (console only). You might also be able to force the ubuntu liveCD to load console only with something like "--nox". I don't have one lying around ;)

---

