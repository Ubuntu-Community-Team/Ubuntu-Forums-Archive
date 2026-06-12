---
title: "Why no &quot;Mantainence wizard, Defrag or Scan disk in Ubuntu?"
date: 2008-05-18
forum: General Help
---

### Post by Ian Drummond on 2008-05-18
I am curious? Why does Ubuntu not have the usual maintainence tools that come with Windows? I see no defrag, scan-disk or maintainence wizard anywhere and wondered why?

Ian.

---

### Post by steveneddy on 2008-05-18
Linux is not Windows.

---

### Post by tact on 2008-05-18
> **Ian Drummond said:**
> I am curious? Why does Ubuntu not have the usual maintainence tools that come with Windows? I see no defrag, scan-disk or maintainence wizard anywhere and wondered why?

Ian.

Not needed.  Welcome to the new world and new ways to do (or not have to do) things.

Hope you got ways to use all the time you used to spend maintaining your system, scanning disks, cleaning up virii or malware etc.  :)

You will find that periodically linux will pause during startup and do a file system integrity check every now and then.  Its automatic and can be skipped if its not a good time.  :)

Cheers

---

### Post by sdennie on 2008-05-18
Basically because it's not needed.  Fragmentation isn't an issue if you are using ext3 and when a filesystem is mounted a certain number of times (or after a certain amount of time I think), it will automatically check the integrity of the filesystem and fix any problems it finds (think chkdsk).

---

### Post by dasunst3r on 2008-05-18
Linux uses file systems such as EXT3.  The nature of this file system is such that it is highly unlikely that you need to defragment.  More information at [1].  As for Scandisk, the equivalent of that is *fsck* (_f_ile_s_ystem _c_hec_k_, but it is highly unlikely that you need it.  Finally, there is no maintenance wizard because Linux does not need one!  Good programming practices don't end at the program itself -- it propagates into installation/uninstallation routines.

[1] [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Sef on 2008-05-18
> Basically because it's not needed. Fragmentation isn't an issue if you are using ext3 and when a filesystem is mounted a certain number of times (or after a certain amount of time I think), it will automatically check the integrity of the filesystem and fix any problems it finds (think chkdsk).

It will check the disk about every 25-30 boots.

If you use reifersfs, it will never defrag.  Ext3 does not have a defragging problem unless you get over 90% full.

---

### Post by kevdog on 2008-05-18
Its actually untrue that Ubuntu will never need defragmenting.  In fact I know some users have post defragmentation scripts to the T&T section in the past.  This issue hasn't been brought up in a while, however its a regular occurring discussion with the conclusions being reached each time slightly different.

---

### Post by empthollow on 2008-05-19
> **tact said:**
> Not needed.  Welcome to the new world and new ways to do (or not have to do) things.

Hope you got ways to use all the time you used to spend maintaining your system, scanning disks, cleaning up virii or malware etc.  :)

You will find that periodically linux will pause during startup and do a file system integrity check every now and then.  Its automatic and can be skipped if its not a good time.  :)

Cheers

What's the magic keystroke for skipping the system check at boot?

---

### Post by czechman86 on 2008-05-19
> **empthollow said:**
> What's the magic keystroke for skipping the system check at boot?

i believe that it is escape. it will tell you what your options are while it is scanning.

---

### Post by empthollow on 2008-05-19
thanks, i never noticed.

---

### Post by Rinzwind on 2008-05-19
> **empthollow said:**
> What's the magic keystroke for skipping the system check at boot?

As of Hardy: ESC
Before that it was not possible.

Also: the check is skipped on notebooks when on battery.

---

### Post by empthollow on 2008-05-19
Ahh, that's good to know, i don't feel as stupid now, i've been using ubuntu for years. hehe

---

### Post by Ian Drummond on 2008-05-19
Thanks for putting me straight on this everybody, now I know! ps, Ubuntu has opened my eyes to the possibilities in Linux. Thanks!

Ian

---

