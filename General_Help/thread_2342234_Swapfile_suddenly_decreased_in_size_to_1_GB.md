---
title: "Swapfile suddenly decreased in size to 1 GB"
date: 2016-11-05
forum: General Help
---

### Post by &amp;KyT$0P# on 2016-11-05
A long time ago, I set up this system to use a swapfile with a size of about 9 GB.  The idea being that it's slightly more than my 8 GB of RAM.

Checking some stuff on my system just now, and noticed that my swapfile size - and swap space size - are suddenly reduced to 1 GB?

I don't check this stuff that often, nor do I back up my swapfile, so there's no way to know when this would have happened.

1) How could this happen on its own?
2) Given that disk space isn't an issue, is it safe to just increase the size back to 9 GB the normal way? (swapoff, rm, dd, mkswap, reboot)

---

### Post by &amp;KyT$0P# on 2016-11-07
bump

---

### Post by #&amp;thj^% on 2016-11-07
I have never seen where a swap partition has been decreased with out user interaction??
Do not take the above as a cheeky comment I am just bewildered how this could happen is all.
You have a couple of options here:
As also described in the same link as below.

I have used the GUI method of increasing the size of swap partition the way described Here:
[http://askubuntu.com/questions/178712/how-to-increase-swap-space](http://askubuntu.com/questions/178712/how-to-increase-swap-space)

---

### Post by Bashing-om on 2016-11-07
halogen2; Hey ...

Only as a thought .. more than the one swap partition on the drive(s) ?
```

sudo blkid
sudo fdisk -lu

```

I too multi-boot, and I insure that all installs share that one swap partition . I have on occasions had to insure that I make it so .

[INDENT][INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]ya gotta second guess what the system is going to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;KyT$0P# on 2016-11-07
This is a swap **file**, not a swap partition.  I don't have a swap partition.

Bashing-om, here's the output from that first command - *(deleted)*
The swapfile is on .

The disk is gpt so the 2nd command won't work.

---

### Post by &amp;KyT$0P# on 2016-11-08
bump

This information useful here?
```
$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/mnt/*****                              file            1048572 0       -1

```
(swapfile name obscured)

So is it safe to just increase the swapfile size back to 9 GB the normal way?

---

### Post by #&amp;thj^% on 2016-11-09
@ halogen2 I have never personally used a "**swapfile**" my self so "I" can not say for sure if it is safe to increase the **swapfile **size.
But I just happened to read this: [https://www.digitalocean.com/community/questions/how-to-change-swap-size-on-ubuntu-14-04](https://www.digitalocean.com/community/questions/how-to-change-swap-size-on-ubuntu-14-04)
And looks promising.
Anyway best of luck in your journey.
Regards

---

### Post by &amp;KyT$0P# on 2016-11-09
Well, I did a full system backup for other reasons.  So I decided to just try increasing the swapfile size, while things were relatively disposable.
```
$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/mnt/*****                              file            9437180 0       -1

```

Nothing seems to have blown up, nor has the swapfile shrunk again, so guess this is as solved as it's going to be.  Thanks all who replied.

---

### Post by cariboo on 2016-11-10
Just out of curiosity, are you using a swap file because you forgot to create a swap partition when you did your initial install, or is there some other reason for using one.

---

### Post by &amp;KyT$0P# on 2016-11-10
> **cariboo said:**
> Just out of curiosity, are you using a swap file because you forgot to create a swap partition when you did your initial install, or is there some other reason for using one.
Because this way it's no big deal to adjust the swap size if needed.  For example, if I use up nearly all of space on the partition, I can easily shrink the swap size to immediately get a little more disk space.

Of course, I did assume it'd be me controlling that.  Guess we really can't assume anything.

---

### Post by kingneutron on 2016-12-02
--Just a guess, but I wonder if the swapfile was truncated by an automatic fsck (after a certain number of mounts) - could have happened after a reboot. In that case, you are definitely better off re-creating the swapfile from scratch.  I'd also make sure chmod permissions are set to 700 for it.

---

### Post by &amp;KyT$0P# on 2016-12-02
> **kingneutron said:**
> --Just a guess, but I wonder if the swapfile was truncated by an automatic fsck 
Thanks, that could be it.  I did have a [file corruption problem]("https://ubuntuforums.org/showthread.php?t=2340762") around the time I first noticed this.

---

