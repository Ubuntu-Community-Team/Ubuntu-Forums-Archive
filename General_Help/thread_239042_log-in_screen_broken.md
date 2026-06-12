---
title: "log-in screen broken?"
date: 2006-08-18
forum: General Help
---

### Post by ren wins on 2006-08-18
i started having this problem a while ago, and basically abandoned ubuntu b/c of it.  I upgraded to dapper yesterday, hoping it would fix the problem, but no luck.

here's the original thread

[http://ubuntuforums.org/showthread.php?t=174956](http://ubuntuforums.org/showthread.php?t=174956)

here's the tutorial i followed to upgrade to dapper (i did it all through the terminal log-in)

[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

basically, when i try to log-in, the log-in screen blacks out like it should. the little timer mouse-icon appears like it should, then instead of popping up kubuntu or xubuntu, or ubuntu, it dumps me back into the log-in screen

i've tried uninstalling and reinstalling the kubuntu and ubuntu desktops, i tried installing xubuntu yesterday. i tried sudo dpkg-reconfigure xserver-xorg several times.

i'm kind of at a loss. i may just scrap it and do a complete reinstall... but i feel that that is a bit overkill. and that there must be a better sollution.

:confused:

---

### Post by tommcd on 2006-08-18
I read your original thread. At this point, I think you may solve your problem faster and easier with a clean install. Looks like you've been dealing with this for a while now. Wish I had a better solution.

---

### Post by .t. on 2006-08-18
Post here your /var/Xorg.0.log; if you can! It may give a clue. Also; your hardware details.

---

### Post by ren wins on 2006-08-18
> **.t. said:**
> Post here your /var/Xorg.0.log; if you can! It may give a clue. Also; your hardware details.

/var/Xorg.0.log is aparently an empty file?

hardware specs:

AMD XP 2200+ processor (1.67 gHz)
512 MB pc2700 RAM
nVidia Geforce FX 5700+ graphics card 
2 hard drives (60 GB and 200 GB)

---

### Post by ren wins on 2006-08-18
here's another interesting problem, that may be related

when i try to do a man for a command, for example man ls, i get this problem

> gzip stdout:No space left on device
man: command ' /bin/gzip -dc /usr/share/man/man1/ls.1.gz failed with exit status 256 

---

### Post by .t. on 2006-08-19
Woah. Sounds like your system's seriously messed up, mate. Is your HD full perchance? If not, is your HD mounted ro? If that's the case, and I don't know why it would be, you need to re-mount it rw. But it should do that automatically. Errr....

---

### Post by ren wins on 2006-08-20
my hard drive is not full (it's 200 GB, plus another 60 that windoze is barely using)
but my linux partition might be full?

how would i check how full it is?

ALSO
on a whim, i "sudo startx" from the terminal prompt, and gnome fires right up! or at least ubuntu does, i'm pretty sure this is gnome.

this is bizzare, but a step in the right direction...

---

### Post by .t. on 2006-08-20
Yeah - it would but be careful since you'd be running with root access. Probably just "startx" is better, if it works, that is. To check how full your mounts are, do "df -h" (disc free) in a terminal

---

### Post by ren wins on 2006-08-20
it looks like it's full
oops :(

```
root@violet:/root# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              15G   14G   28M 100% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hda1              75G   31G   45G  41% /media/windows
/dev/hdb6              43G   22G   22G  51% /media/noise
/dev/hdb7              43G   40G  2.6G  95% /media/eyes
/dev/hdb8              43G   17G   27G  39% /media/support
/dev/hdb9              43G   13G   30G  30% /media/static

```

this could be tricky
i'm going to have to fix windoze enough to partition it's harddrive so ubuntu's got a 30 GB partition
man, this is kind of bothersome

---

### Post by ren wins on 2006-08-20
oh wait, i can partition it right now
there's plenty of space on my windows partiton

is there an ubuntu partitioner somewhere?

---

### Post by .t. on 2006-08-20
Well, good luck on that! How did you manage to fill all that?

As to your second post, well use the GParted LiveCD. I don't know what it's like on NTFS though. FAT32 is fine, I think.

---

### Post by ren wins on 2006-08-21
i blame synaptic

i think i'll uninstall xubuntu, for temprorary fixing

can i somehow uninstall breezy?
and i think i may have a knoppix live DVD laying about, do you think i could use that?

---

