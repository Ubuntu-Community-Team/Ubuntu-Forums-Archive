---
title: "nfs mount/mtab errors"
date: 2007-03-18
forum: General Help
---

### Post by gapplewagen on 2007-03-18
I just built a mythtv frontend box and it's suddenly experiencing some problems automounting an nfs share I have on another machine (the mythtv backend).  It's running Edgy.  During the mount I get:

mount: can't open /etc/mtab for writing: Input/output error

a cat of /etc/mtab yields the same error.

[code]
matt@pvr:~$ ls -la /etc/mtab
ls: /etc/mtab: Input/output error
matt@pvr:~$ ls -la|grep mtab
matt@pvr:~$ ls -la /etc|grep mtab
?---------   ? ?      ?            ?                ? /etc/mtab
[code]

I have read elsewhere that I may need to run fsck on the local disk.  All local partitions mount fine and there are no errors in dmesg, /var/log/syslog, or /var/log/messages.  I can mount this nfs share from my laptop with no problems.  Everything else seems fine with the frontend box (live tv, playback, audio playback, etc).

Any ideas on how to clear this up?

---

### Post by vinnn on 2007-03-18
Looks to me like filesystem corruption.
The node for the mtab file is there but the file is not.

Last time I saw something like that, a guy in work had shrunk a logical volume without shrinking the partition on it first.

Have you tried an fsck yet?
Use your Ubuntu disk to boot from (e.g. use it as a live cd) and **fsck -Va** your hard disk.

---

### Post by gapplewagen on 2007-03-19
Thanks for the response.  I had read elsewhere to give that a shot... I haven't done it yet but I will later this evening if I find time.  Wouldn't this be detected on boot though?  dmesg does show this on boot now:

```

[17179578.824000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.824000] EXT3-fs: write access will be enabled during recovery.
[17179580.536000] EXT3-fs: recovery complete.
[17179580.540000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.156000] EXT3 FS on hda1, internal journal

```

"recovery complete" but still get input/output errors when mounting or trying to do anything at all to /etc/mtab

---

### Post by gapplewagen on 2007-03-20
I discovered that I had some bad RAM in that system and it was causing a lot of issues.  It has been replaced now.

However, I am still getting the mounting error.  Running fsck -Va just states that the filesystem is clean and drops me back to a prompt.  I plan on re-running this using the -f option sometime today.

---

### Post by gapplewagen on 2007-03-20
Ok it's all fixed.  The man pages for fsck.ext3 are not the same as fsck alone.  -V is version info for .ext3 and the -a option is depreciated (still works but -p is replacement).  So I ran:

```

fsck.ext3 -pvf

```

and it fixed everything nicely.

---

### Post by americ on 2007-04-13
I just experienced the same input/output errors with mtab.

Listing /etc showed the same ?'s for mtab.

I checked /var/log/messages, and there are no errors or recoveries during subsequent reboots.

These errors started when I plugged in a damaged jump drive that couldn't be mounted by Windows or MacOS. That jump drive wouldn't mount, which didn't surprise me. However, a good jump drive wouldn't mount after that. At that point I checked /etc/mtab and got input/output errors. Rebooting did not fix the problem.

I rebooted a second time... and the problem has gone away. My jump drive mounts automagically again. /etc/mtab has returned and looks right.

I'll boot from the install disk and fsck, as the previous post suggested, just to be safe.

---

