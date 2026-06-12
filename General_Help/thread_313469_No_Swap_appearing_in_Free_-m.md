---
title: "No Swap appearing in Free -m"
date: 2006-12-06
forum: General Help
---

### Post by Sef on 2006-12-06
When I checked my swap in the terminal, it showed this:

> sef@jokat1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        488         15          0         27        302
-/+ buffers/cache:        158        345
Swap:            0          0          0


I have 1000 GB swap partition, yet it shows up in the terminal as 0.   I'm sure this is related to 5 second loss of power due to a condensor on a power pole exploding. (I heard it.)  After that, I found my swap was gone, so I reinstalled it with GParted. I tried swapon, but it doesn't go on.  Is there someway to turn my swap on?

---

### Post by tommcd on 2006-12-06
You may need a new UUID for swap. See these:
[http://ubuntuforums.org/showthread.php?t=309102&highlight=swap](http://ubuntuforums.org/showthread.php?t=309102&highlight=swap)
[http://www.ubuntuforums.org/showthread.php?t=307009&highlight=swap+signature](http://www.ubuntuforums.org/showthread.php?t=307009&highlight=swap+signature)
[http://ubuntuforums.org/showthread.php?t=287096&highlight=swap](http://ubuntuforums.org/showthread.php?t=287096&highlight=swap)
Hope this helps. I came across these threads recenly.

---

### Post by drphilngood on 2006-12-06
```
Initialize and activate swap (substitute the partition number for your intended Ubuntu swap partition):

# mkswap /dev/hda5
# sync; sync; sync
# swapon /dev/hda5

```

See here:
[http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs04.html]("http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs04.html")

---

### Post by Sef on 2006-12-06
Thank you both.   I got it back on.

For those who are interested, here's what I typed in the terminal:

```
sef@jokat1:~$ sudo mkswap /dev/hda3
Setting up swapspace version 1, size = 1052831 kB
no label, UUID=7f2a8760-fd63-4b3e-8bdd-29e83db054cf
sef@jokat1:~$ sudo sync; sync; sync
sef@jokat1:~$ sudo swapon /dev/hda3
sef@jokat1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        404         99          0         25        215
-/+ buffers/cache:        164        339
Swap:         1004          0       1004

```

---

### Post by drphilngood on 2006-12-06
Just remember me when I need help.;)

---

### Post by tommcd on 2006-12-06
Glad you got it fixed. That "sync" command is a new one for me. 
[http://www.linuxcommand.org/man_pages/sync1.html](http://www.linuxcommand.org/man_pages/sync1.html)
I'll have to make a note of it.

---

