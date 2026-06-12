---
title: "Add Separate Home Partition to existing installation"
date: 2007-09-12
forum: General Help
---

### Post by Leon945 on 2007-09-12
Hello people,
I installed ubuntu, and I just recently decided it was a good idea to have my home on a separate partition.

Can i change this without having to reinstall Ubuntu and without messing up my current installation?

Thank you in advance.

---

### Post by Tautoa on 2007-09-12
Shouldn't be a problem :)
I did have a link to a website which explained this really well, but I can't find it :S

But, the way I did it was...

Open a terminal and type 
```
sudo mkdir /newhome
```

Now, lets assume that your new partition is /dev/hdb1, then you would mount it at /newhome with this command
```
sudo mount /dev/hdb1 /newhome
```

Next, open Nautilus as root by typing
```
gksudo nautilus
```

Then, go to View, show hidden files (or something similar, I use Konqueror rather than Nautilus, so I'm not sure of the exact wording)

And use Nautilus to copy every file under /home to /newhome
Just so you know, the reason I say to use Nautilus to copy the files, rather than the terminal, is that I cant seem to find the flag that forces the cp command to copy hidden files as well... 

When the copy/paste is done, go back to the terminal, and unmount the new home by typing 
```
sudo umount /dev/hdb1
```

And then...

```
sudo mount /dev/hdb1 /home
```

Which should mount your new partition under /home :)

You'll also have to play with /etc/fstab, to make the new partition be mounted as /home every time you reboot... but you can search the forums for instructions to do that... I would tell you myself, but my brain isn't co-operating at the moment, I can't think, even this was an effort :) sorry!

---

### Post by aysiu on 2007-09-12
> **Tautoa said:**
> Shouldn't be a problem :)
I did have a link to a website which explained this really well, but I can't find it :S [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Tautoa on 2007-09-12
Typical!
That's the link I was looking for, and I found it after I posted that... came back and aysiu beat me to it :)

Disregard my last post, you won't find a better way of doing something than the psychocat way :)

---

### Post by Leon945 on 2007-09-12
excellent...

i'm really thankful of you guys taking your time to answer my question.. haha
i mean really... why would you care...

thanks alot!

---

### Post by Tautoa on 2007-09-12
Well...
[http://ubuntuforums.org/showthread.php?t=444127](http://ubuntuforums.org/showthread.php?t=444127)

Thats a thread that I started about 4 months ago, when I had just installed Ubuntu, and was thinking about moving things to other partitions, sorta like you are now :)

Everything I've learned about Ubuntu, I've learned from this forum, or from generally messing around with stuff. So if I'm around on here, and I notice a question that I might just know the answer to, why not take a minute to help someone? :)

Wouldn't be much of a forum if everyone was asking questions and no-one was answering? :)

---

### Post by Leon945 on 2007-09-12
I really appreciate it..

I've actually been using linux on a par with windows for about 2 years...
So i know how to get around, i'm not that much of a newbie..

But i'm no expert..  i just wanted to check this out before trying anything stupid..

thanks again!

by the way, i am now windows free

---

### Post by bananaman on 2007-09-13
Ok... I did EXACTLY as it said in the guide... one particular surprise at the end but no biggie...

Now, this is the issue at hand and I'll be as concise as possible.

Before now:
I had a 230gb hard drive... partitioned in 3: (hda1/reiserfs/213Gb), (hda2/swap/2Gb) and (hda3/ntfs/15Gb).

I wanted to move my home folder to a new reiserfs partition, but my home folder is about 100Gb... so I cut up the first partition in 2. After that I had:

hda1/reiserfs/107Gb
hda4/reiserfs/105Gb
hda2/swap/2Gb
hda3/ntfs/15Gb

What I did then was move my 100Gb home folder (as per the instructions) to the new partition. I rebooted and everything worked... so far so good.

Now... I deleted the backup of my home folder from my first partition (hda1) because I already have the working copy on the new partition (hda4).

So now what i want is give 90Gb from the first partition (hda1) to the new one (hda4) because I dont need that much space for the ubuntu installation, but I do want it for file storage in my home folder (now on hda4).

I successfully resized hda1 from 100Gb to 10Gb using the live CD and Gparted... but now the 90Gb left of unallocated space, I cannot add to my new partition (hda4).

Gparted tells me I can move/resize, but that isnt so... I can only resize partitions from the right and this unallocated space is on the left of my new partition (because it used to belong to the first partition on the disk)... and neither can I move the new partition to be next to the first one so that i can then resize it to the right...

[[IMG]http://img385.imageshack.us/img385/2029/gparted1xw9.th.jpg[/IMG]](http://img385.imageshack.us/my.php?image=gparted1xw9.jpg)

[[IMG]http://img208.imageshack.us/img208/5862/gparted2lq7.th.jpg[/IMG]](http://img208.imageshack.us/my.php?image=gparted2lq7.jpg)

So here I am... stuck and not knowing what to do... does anyone have any suggestions? Also, Gparted tells me I can only have 4 partitions on a disk, no more, so I cannot assign a new format to that unallocated space...

In case its not clear, what I want is for my 2nd partition on the disk (hda4) to absorb that unallocated space...

Help?

Thanks in advance...

---

