---
title: "all drives are read-only"
date: 2006-12-02
forum: General Help
---

### Post by wgscott on 2006-12-02
Suddenly all my drives are now read-only.

In single user mode, I am unable even to get 


mount -w /

to mount a rw version of the root directory.  Am I completely hosed?  Do I have to reformat the partion and install from a CD?

](*,)

---

### Post by ciscosurfer on 2006-12-02
What does your /etc/fstab file look like?  Post the output.

---

### Post by wgscott on 2006-12-02
I wish I could.  It is what I am trying to edit.  I started messing with it because at first my slave drives would not mount.  A previous version is posted here:

[http://ubuntuforums.org/showthread.php?t=310793](http://ubuntuforums.org/showthread.php?t=310793)

I doubtless introduced corrupted syntax.  The main point is I want to go back to my pre-edgy one that worked properly, which is saved as a backup. But I cannot access any partition now, including /

Is it possible to boot off the install cd and edit or replace the file?

Otherwise the only thing I can think of is to wipe out the partition (15 GB of ubuntu stuff, but fortunately nothing irreplacable).

---

### Post by ciscosurfer on 2006-12-02
This is an interesting predicament.  Any other time, I would certainly recommend booting from a live disc, mounting your partition, and changing whatever files you needed to.  In this case, however, since you have somehow botched your fstab file, and made it so the drive is only read accessible...you're in a bind.  I'm sure there is an easy fix for this.  Let me think about this and get back to you soon.

At the very least, you can boot via live disc, and then copy the syntax from your fstab file so we can see what has been changed around.

EDIT: I know there is a way to mount your partition (after loading the OS from a live disc) read/write.  stay tuned, I be right back!  In the meantime, you can read up on man mount pages here: [http://www.die.net/doc/linux/man/man8/mount.8.html](http://www.die.net/doc/linux/man/man8/mount.8.html)

EDIT: Take a look at the appropriate syntax for your partition and drive (which /dev it is and if its ext2, ext3, etc.) and then use the dash w switch ( -w ) this will make the partition read/writable.

---

### Post by wgscott on 2006-12-02
The change is from


UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 / ext3 defaults,errors=remount-ro 0 1

to

/dev/hdc1  / ext3 defaults,errors=remount-ro 0 1


which was pre-edgy

The problem started before I started messing with fstab, but it was originally limited to the slave drives.  Now all partitions are read-only.

---

### Post by ciscosurfer on 2006-12-02
Take my advice from above (I made EDIT's) and then switch it back to your previous setup.

---

### Post by wgscott on 2006-12-02
> **wgscott said:**
> I am unable even to get 


mount -w /

to mount a rw version of the root directory.  




I think there is something fundamentally wrong.  It's almost 11 pm here, which means 1 am in Chicago.  I really appreciate your help, but one thing I have learned with computers is not to panic.  I'm going home and will work on this tomorrow.

I can't even remember how to boot from the CD (which I just downloaded and burned -- I haven't installed this in about 2 years).

I was at least smart enough to put all the system stuff on the root partition and everything else is isolated on other partitions, so throwing it in the fire won't be the end of the world.

On OS X I can just hold down the C-key to boot off the disk.  I think I have to mess with the bios or something like that in the present case.

Anyway, I really appreciate your help with "Stump the chump."  I was just yesterday griping about OS X and singing the praises of Ubuntu.  C'est la unix.

---

### Post by ciscosurfer on 2006-12-02
It is 1 am here, but that's we like to call "burning the midnight oil."

We can mess with this tomorrow, that's no problem.

Go home, get some sleep, dream of Penguins :-)

---

### Post by wgscott on 2006-12-02
On the way home I realized that fundamentally this cannot be a problem due to my /etc/fstab, as I hadn't so much as looked at it since the Edgy upgrade until after the problem began to develop.  I am more worried now that it is some sort of filesystem corruption.

If I can just cleanly format the 20 GB partition I have the system files on, I can install a new edgy on top of it cleanly, which is probably what I should have done in the first place (I've been using apt-get to do the last several version updates).

I am now for the first time starting to appreciate how OS X does this.  The /etc/fstab has been replaced by something called the Netinfo database.  The details aren't important (and are probably black-box proprietary) but essentially it spares the user having to deal with any of this.  The only thing in my /etc/fstab on OS X are my NFS mounts (and that is there only because I use it in backward-compatibility mode). It fully integrates the content with disk arbitration, which has always been a bit of a headache for me on this PC.

Again, thanks for your help.  I grew up in Chicago and miss the fine weather.

---

### Post by ciscosurfer on 2006-12-02
Interesting points, all.

Chicago is freezing right now.  You're not missing anything.  Trust me.

---

### Post by wgscott on 2006-12-02
So I burned a CD and tried to boot from it, but nothing.  From the scant information on the Ubuntu web page documenting this, I gather it should just recognize the CD in the drive and use it:

> 

Ubuntu install disks are bootable, put the disk into your computer's drive and restart you computer. You will then see a boot menu ...


so of course I have to figure out of I burned a bad CD (from OS X, not an impossibility).  If not, is there a way to force the bios to do this?

Thanks again for your help.

---

### Post by ciscosurfer on 2006-12-02
Yes.  In your BIOS you want to make sure that you set your CD/DVD drive to be the first drive your system sees/uses at boot time.  Once you've made sure of this, then make sure you've burned yourself an ISO with no errors (at the boot screen, there is an option that will allow you to check the integrity of the disc itself...or, of course, you can checksum the disc in OS X prior to trying to boot from it.

---

### Post by wgscott on 2006-12-02
Ok, it is fixed now (I think).  But that is 2 more hours of my life I will never have back.

Here's what I did (stripped of all the false starts):

1.  Downloaded and burned the boot disk to a DVD.  (Didn't fit the CD).

2.  Reconfigured the bios to find the DVD first.

3.  Booted demo.

4.  Opened terminal, issued sudo /bin/bash (after cursing the absence of zsh).  (You get a root shell that way).

5.  Issued (as root)

```


mkdir -p /mnt/temp

mount /dev/hcd1   /mnt/temp

cd /mnt/temp/etc

mv fstab  fstab.swearword

mv fstab.pre-edgy fstab

exit


```

Rebooted.  All appears normal again (so far).  But then the edgy one worked for a month before I had any problems.

The memory test I also did had one failure.  


There is absolutely no documentation for the average luser on how to do anything like this past step 3. Neither of two Ubuntu books I have (the good ones) suggest anything like this either.  Even the supposed rescue mode on the CD no longer exists.  It just says you can do everything from demo mode.

Anyway, for the moment at least it works again, so many thanks.  It's 65F and sunny today.  :mrgreen:

---

### Post by ciscosurfer on 2006-12-02
Bravo for getting everything back to normal.

The sudo /bin/bash trick is really cool (had no idea you could get root access in the terminal with that command!)

I also get memory test errors as well (don't think my memory has gone bad though...it's fairly new...but you never know)

As for booting off your HD to rescue mode (not of the CD/DVD -- but is still there btw), you can go into your menu.lst file and make sure that there is a line beneath your regularly schedule kernel (couldn't resist that one) and on the boot line there should be the word Single.  So, when GRUB boots up, you can enter Recovery mode my choosing that option in your list.  And off the CD/DVD, typing in single at the boot prompt will accomplish the same thing.

Anyway, glad all is back to normal (for now...)

Still cold, hovering around 27F, windy.  Brrrrrrr. *shivers_in_disgust_at_west_coast_temps*

---

### Post by wgscott on 2006-12-02
Yeah, I booted from the hard drive rescue mode, but the / was mounted read only , and since it was root, I couldn't unmount it to mount it rw (or something was preventing it -- probably the fstab, although the -n flag wasn't helping).

That's why I had to create a mount point (mkdir -p /mnt/temp ) and force the hard drive root partition to mount as a different name when operating from the demo DVD.

sudo /bin/(shell-of-choice) is my favorite security hole.

If you ever need OS X help for some reason, please don't hesitate to ask.   

I really appreciate your help.  Hope it warms up there (I still miss it).

---

### Post by emdeem on 2006-12-02
I'm curious what caused the original problem.
- When you originally tried to remount things as RW, what errors did you get?
- Why were you unable to post the contents of fstab?  Certainly you can cat a file without RW access.
- Did you save the old broken fstab?

---

### Post by wgscott on 2006-12-02
1.  I don't know what caused the problem. I am **speculating** that it has to do with using the UUID syntax in fstab rather than the old /dev/foo syntax, but I am only guessing.  The trouble with my guess is it doesn't explain why the new syntax worked for a month after the edgy update (unless the change to fstab was during a more recent apt-get update).

1a. I made the problem worse by editing the /etc/fstab and putting in syntax that works on BSD but not linux, but it didn't start there.  

2. I saved **that** file.  The only difference between the EDGY and pre-Edgy /etc/fstab is that the edgy one now used UUID serial numbers for the devices rather than the standard device names themselves.

3.  I could cat the file at the time but i was in single user mode and using the web browser on another computer. The problem was I couldn't edit it.

4.  When I issued for example

mount -w /

it told me the device was already mounted (and it couldn't write to /etc/mtab, since the partition was read-only).  When I issued umount / it failed silently.  Since I was using the root partition, it makes sense.  Since /etc/mtab probably then had the corrupted syntax (I can't remember) in addition to being read-only, it compounded the problem.

On OS X (which is a BSD variant) you can issue

mount -uw /

but that -u flag isn't valid on linux.

---

### Post by wgscott on 2006-12-02
Here is what was in the Edgy file:

```

UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 /    ext3   defaults  0 1

```

Here is how I screwed it up:

```

UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 /    ext3   defaults,errors=remount-rw 0 1

```

Here is what now seems to work (pre-edgy syntax):

```

/dev/hdc1    /               ext3   defaults,errors=remount-ro  0 1


```


(I thought changing  errors=remount-ro  to ,errors=remount-rw  would only help, but for some reason that syntax isn't recognized.)

The main difference though is the /dev/hdc1 instead of the UUID (none of my other entries had the errors=remount-ro line).

---

### Post by ciscosurfer on 2006-12-02
> **wgscott said:**
> Here is what was in the Edgy file:

```

UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 /    ext3   defaults  0 1

```Here is how I screwed it up:

```

UUID=42459227-e52a-41f6-a8e1-55200ccb05f3 /    ext3   defaults,errors=remount-rw 0 1

```Here is what now seems to work (pre-edgy syntax):

```

/dev/hdc1    /               ext3   defaults,errors=remount-ro  0 1


```(I thought changing  errors=remount-ro  to ,errors=remount-rw  would only help, but for some reason that syntax isn't recognized.)

The main difference though is the /dev/hdc1 instead of the UUID (none of my other entries had the errors=remount-ro line)."You've got Mac mail"...:D

---

### Post by wgscott on 2006-12-04
Unfortunately, this is not the complete solution to the problem.

Once again, my slave drives are read-only.

from fstab:

```

# These are the two subsidiary hard drives
/dev/sda1        /mnt/data_disk1 ext3    defaults      0 0
/dev/sdb1       /mnt/data_disk2  ext3    defaults       0       0

```

](*,)


EDIT:  I rebooted, and the problem (for now) went away.  But this is really getting annoying.

---

