---
title: "Very Strange Problem....."
date: 2005-10-28
forum: General Help
---

### Post by Breezy Badger on 2005-10-28
Well I have outdone myself again.  I had to use my linux partition to store some files while clearing another hard drive.  I am such a tard here...I did not leave enough space on the drive to even loan linux.

now when it loads it cannot write to temp, thus not allowing it to start because there is not any free space....like i mean none.  How can i fix this, I need to get in and delete something from the promt screen.

Badger

---

### Post by ronin_ar on 2005-10-28
[QUOTE=Breezy Badger]Well I have outdone myself again.  I had to use my linux partition to store some files while clearing another hard drive.  I am such a tard here...I did not leave enough space on the drive to even loan linux.

now when it loads it cannot write to temp, thus not allowing it to start because there is not any free space....like i mean none.  How can i fix this, I need to get in and delete something from the promt screen.

Badger[/QUOTE]

Boot with a live CD and mount the partition.
then rm what you can to try to boot 

Good luck!

---

### Post by taurus on 2005-10-28
Or if you have an empty partition, mount it as /tmp...

---

### Post by Breezy Badger on 2005-10-28
sorry I have never used this, where do I get it

Badger

---

### Post by Breezy Badger on 2005-10-28
I have windows on this computer as well...is there anyway I can view the linux partition in windows and do it from that, that would seem like the easiest solution

Badger

---

### Post by ronin_ar on 2005-10-28
[QUOTE=Breezy Badger]I have windows on this computer as well...is there anyway I can view the linux partition in windows and do it from that, that would seem like the easiest solution

Badger[/QUOTE]

Mmm, you should run a search in google, I think there were some apps that let you read ext2 / ext3 partitions, but don't know if write to them ( ie delete files)

---

### Post by Breezy Badger on 2005-10-28
my linux is in reisers format but i get what you mean

---

### Post by agger on 2005-10-28
[QUOTE=Breezy Badger]my linux is in reisers format but i get what you mean[/QUOTE]

Rescue plan:

Go (from another computer) to [http://www.dynebolic.org](http://www.dynebolic.org) - download ISO image of the dyne:bolic Linux distro - boot with this CD.

You now are root and have access to all your disks, so you can delete
whatever you please - delete whatever necessary.

Now shutdown and boot.

There's a lot of other "live" distros around that can do essentially the same thing, dyne:bolic just happens to be the one I use for such things.

---

### Post by Breezy Badger on 2005-10-29
Ok I got it all fixed thanks for all the help guys.

The easiest thing to do was start it, and in the command promt just remove soemthing from the hard drive with the rm - code.  I deleted something I did not need and freed enough space to start it.

Thanks again for all the help

Badger

---

