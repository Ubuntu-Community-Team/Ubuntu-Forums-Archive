---
title: "Boot problem while checking filesystems"
date: 2006-09-19
forum: General Help
---

### Post by Mathiasdm on 2006-09-19
I have an Acer Aspire 5002.
During boot, while checking the filesystems (2 FAT32-partitions, 1 Linux ext3-partition and an ext2-boot-partition), I get the following error:
```

Checking all filesystems...
<stuff about checking FAT-partitions -- not important>

There are differences between boot sector and its backup.
Differences: (offset: original/backup)
65:01/00
Not automatically fixing this.

```
So, I type Ctrl+C to stop the boot process, and Ctrl+D to continue. That way, I can start the computer.
However, it's kinda annoying to do this at every boot.

Any way to fix it?

---

### Post by kunuub on 2006-09-19
Thank you Mathiasdm... I had the same issue with my new Kubuntu install and I thought I was stuck... until I read your post on how to go past that stage and into Kubuntu! After 2 days of unsuccessful searching I'm glad you posted this!! Thanks!

If it helps, I found this thread with a similar issue to ours...
[http://ubuntuforums.org/showthread.php?t=224830&highlight=differences+boot+sector+backup](http://ubuntuforums.org/showthread.php?t=224830&highlight=differences+boot+sector+backup)

I haven't tried it (I'm not sure what it does) but here's what Clickwir suggests:
[..]
Boot off Ubuntu or Kubuntu Live CD.
Goto a console screen

sudo fsck -V -r /dev/hda2

choose Y for yes when selected.
If you have Windows on a different partition (maybe /dev/hda1) then use that. Mine and several others were on /dev/hda2.
[..]

I'm a total newbie (researched on the net for linux options over the last one month, chose Kubuntu, got the CD, studied dual booting and installed it this Sunday!) so apologies if what I've posted didn't help you... I'm still learning commands (and their implications)!

Have fun!

---

### Post by Mathiasdm on 2006-09-19
Well, glad to be of assistance :p Even if it wasn't my intention :)
I'll give that fix a try. I hope it'll work :)

---

### Post by kunuub on 2006-09-23
Any luck?

---

### Post by Mathiasdm on 2006-10-26
> **kunuub said:**
> Any luck?

It worked:) Thanks!
Sorry about not noticing this earlier!

Sadly, I now have a similar problem with Edgy.

I can't fix it yet, since I don't have a LiveCD, and my download limit is nearly maxed out:-? 

This time, it's more annoying. Ctrl-C and Ctrl-D don't even work](*,) 

Suggestions would be welcome:p

Edit: strange that this is in 'Desktop Environments'. Could a mod move this?

---

### Post by Mathiasdm on 2006-10-27
Okay, I'm going to download Edgy anyway, and have a go at it.
If anyone has other suggestions, do mention :p

---

### Post by singlewc on 2007-11-04
> **Mathiasdm said:**
> Okay, I'm going to download Edgy anyway, and have a go at it.
If anyone has other suggestions, do mention :p


So this crap has been happening for over a year, and no one has addressed it, and fixed it?

What's up with that? I got the same problem today, with 7.10 that I had six months ago with 6.10 so I search for help, and end up in a one year old thread with the same problem.

Good grief.... Can't tell the world about Ubuntu if I cannot even boot the damn thing up. Bad enough the normal Live  CD cannot install because qparted sucks, and I have to go dig up the alternate, but then after the time it takes to install and reboot, I end up with the very same problem that is in this thread.....

Not very impressed at all. Not at all. 

Gonna overtake windows? Shoot, at least windows installs.

---

