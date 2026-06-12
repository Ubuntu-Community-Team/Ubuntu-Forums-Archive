---
title: "Feisty mondo rescue?"
date: 2007-05-02
forum: General Help
---

### Post by whitefort on 2007-05-02
Hi,

Mondo rescue is a (usually) very easy to use backup program.  Basically it does the same as Norton Ghost, making a copy of the hard drive, so that in the event of a hard drive failure (or accidentally screwing up your operating system, you can have the machine exactly the way it was in a few minutes.

I used it a lot with dapper, and it was a real life saver.  But after  two weeks of trying every day, I still haven't been able to get it to work with Feisty.  The Backup part seems to go OK, but when it comes to compare/restore, it's fails to recognise the backup files.

I was just wondering if anyone has managed to get it working with Feisty, as I really need Mondo (or something that does the exact same thing - and there doesn't seem to be anything else)

---

### Post by phidia on 2007-05-02
There is a thread here [http://ubuntuforums.org/showthread.php?t=429810](http://ubuntuforums.org/showthread.php?t=429810) that might help but I agree with the premise that backup/restore programs are either incomplete or weak in linux.

I did check out the mondo webpage and that appears to be saying that mondo was recently updated to fix a bug.
[http://www.mondorescue.org/](http://www.mondorescue.org/)

---

### Post by phidia on 2007-05-02
Just to update my reply since I'm very interested in this issue too, I checked and synaptic gives the version of mondo as 2.20 while the mondo website has 2.3 out for some distros and as source.
The most recent release isn't available for deb yet.

---

### Post by whitefort on 2007-05-02
I've been downloading and trying various versions of Mondo & Mindi, but haven't been able to get anything to do a restore in Feisty.

This is a real bummer.  i experiment with my installations a lot, and as a result I break them a lot.  And if *I* don't, then I can' be fairly sure that a Ubuntu update will come along and break something...

It's really nice to do a disk image to a bootable DVD, and know that even if I trash the entire system - or even wipe the whole hard drive, I can have everything back exactly the way it was in about 15 minutes or so.

Nothing else seems to be so powerful *and* so easy to use.  Looking at some of the alternatives, they seem to start out saying 'this is easy. You just...' (Followed by pages of complex instructions).

I'm going to keep trying until the weekend, but this is a big enough issue for me that if I can't get it working, I'll be taking Feisty off all my machines and going back to Dapper.  Which is a shame, because there's a lot I like about Feisty.  But I can't live without my backups!

---

### Post by ruibernardo on 2007-05-16
Hi,

I was trying to get mondorescue to work in feisty, but it was giving me uuid errors, because  the packages in the repos were too old. I got mondorescue working by using the packages for debian 4.0 that are in mondorescue site. Here's how I've done it:

```
 # installed from the repos normally so the dependencies are installed
sudo apt-get install mindi mondo

# downloaded the deb packages
mkdir temp
cd temp
wget [ftp://ftp.mondorescue.org/debian/4.0/mindi_1.2.3_i386.deb](ftp://ftp.mondorescue.org/debian/4.0/mindi_1.2.3_i386.deb)
wget [ftp://ftp.mondorescue.org/debian/4.0/mindi-busybox_1.2.2-2_i386.deb](ftp://ftp.mondorescue.org/debian/4.0/mindi-busybox_1.2.2-2_i386.deb)
wget [ftp://ftp.mondorescue.org/debian/4.0/mondo_2.2.3_i386.deb](ftp://ftp.mondorescue.org/debian/4.0/mondo_2.2.3_i386.deb)

# installed the downloaded packages. It will say something about
# downgrading, but I think it's because of the version number of
# the packages that are in the repos. 
sudo dpkg -i *.deb

```To get them upgraded automatically when they get upgraded in the repos to the actual version, add this to the file /etc/apt/preferences:

```
 Package: mindi
Pin: version 2.23*
Pin-Priority: 500

Package: mondo
Pin: version 2.23*
Pin-Priority: 500
```Now mondorescue is working fine :). I hope this works for you too. 

IMHO mondorescue should get upgraded with urgency, since uuid errors must have ocurred since edgy! And this is a very valuable piece of software.

---

### Post by whitefort on 2007-05-16
Thanks for the reply - I've been trying absolutely ***everything*** I can think of to get Mondo to work - including installing the stuff from the Debian site.

I really can't do without Mondo.  I get cranky and nervous if I have to go more than a couple of weeks without a full system backup.!   :) 

I have to admit that I've been planning to take some time this weekend to 'upgrade' all the way back to Dapper on  my machine - just to have a working Mondo. The irony is that this step backwards will be incredibly easy - because I made a bootable Mondo DVD of that installation immediately before installing Feisty.

What's happening in my case is that the backup ***seems*** to work perfectly - but when I use 'compare' absolutely every single file is listed as 'changed'.

If I were a braver soul, I might try to do a 'nuke' from one of those 'failed' backup disks just to see if it works in spite of reporting a couple of hundred thousand errors!   In fact, if I can't get Mondo working, perhaps I'll try this as a desperate  last resort just before I go back to Dapper, since by then it won't matter if my Feisty setup gets trashed.

I'll work through your instructions to the letter sometime today, and report back - if You've got it working in Feisty, then there may be hope for me - but your error seems to be a different issue from what's happening on my machine.

I'll let you know how it goes.

Thanks!

---

### Post by ruibernardo on 2007-05-16
The packages I downloaded are for Debian, but not from a debian repository, but from the ftp server of mondorescue website!

I just tried the 'compare' option and all seems to work here. The only errors I got were about floppy0 (I don't a have floppy drive) and the kernel modules that mindi didn't copy to the backup dvd. 

All the rest went very well. mondorestore mounted the disk partitions as it should and compared the files without any problem.

Please confirm if this worked for you too.

---

### Post by whitefort on 2007-05-17
No, Still no luck.  :(

I've installed the new versions of Mondo, Mindi & Mindi-busybox, but the only noticeable difference is that now the Ubuntu update manager keeps popping up to tell me my versions are out of date.

I do seem to be hitting a different issue from you.  I have't had any UUID problems, but when I try to run 'compare' from the recovery DVD, I eventually get a message that the partition couldn't be mounted, and asking if I want to abort.

If I say 'no', the compare continues, but not surprisingly finishes up by telling me that there are 111740 changes (ie, every file on the machine!)

I've discovered that if I use the recovery disk from WITHIN Ubuntu, I can restore individual files with no problems, but that's not really good enough.  I need to be able to run a restore from the boot DVD so that I can get up and running even if I have a system that can't  boot, or a totally blank hard drive.

I'm guessing that if I can't 'compare' correctly by booting the DVD, I won't be able to 'nuke' correctly either.

Decent backup software seems to be one of Linux's really weak areas...  Oh for something like Genie Backup Manager or Norton Ghost... It almost (only ALMOST!!!) makes me nostalgic for  my old XP setup...

---

### Post by ruibernardo on 2007-05-17
> **whitefort said:**
> No, Still no luck.  :(

Sorry to hear about this. 

> **whitefort said:**
>  I've installed the new versions of Mondo, Mindi & Mindi-busybox, but the only noticeable difference is that now the Ubuntu update manager keeps popping up to tell me my versions are out of date.

To avoid this create or update the file /etc/apt/preferences as posted previously. If you don't, the files will be upgraded in the next system upgrade and mondorescue will be broken again.

This is a shot in the dark, but these problems might be related with the fact that the backup was made with the broken version. As a last resort, I would suggest you to make a new backup with the mondo* mindi* packages installed as explained before (and with the file /etc/apt/preferences updated to).

Here mondo is working very well, including the compare *and* the nuke options (tested).

It very sad that one of the best backup software in linux is broken in the Ubuntu repositories.

---

### Post by whitefort on 2007-05-17
Hi  again, and thanks for trying to help.

Yep, that new preferences file did the trick - thanks!

But no, I did an all-new backup with the new versions, but got the same result.  When I run 'compare' and Mondorestore tries to mount my hard drive, I get the message that it can't be mounted (sda1), and then I'm offered an abort/continue choice.  If I continue, it runs through the whole thing and finally reports that every file on the PC is different.

I'm going to go to the Mondo mailing list to see if I can get some help there.

But even if my problems seem to be unrelated to the version of Mondo in the repository, II totally agree with you that it's shocking that a broken version of such a mission-critical piece of software is allowed to remain in the repository.

---

### Post by imon9 on 2007-05-17
Hi eveyrone, 

i am very interested in using mondo, but the official website doesnt really explain how things works... here is a few questions i wanted to know:

(1) my previous experience with such backup system, it always require us to run it as a different boot from the working partition that we trying to backup, meaning, IF i were to backup my current ubuntu drive, i have to boot from a liveCD or something to backup this partition. My question is: how come we are installing it into feisty itself? if it is being run from within feisty, does it mean we can't backup this particular partition?

(2) from the screenshots, it seems pretty "terminal" based interface, so IF i were to run it within feisty, does it mean, i had to run it in "safety mode" or i can go into my normal desktop and fire-up terminal, then run "mondo" and backup my partition?

(3) the official page has no ubuntu .deb files, only sources. But it appears that the installation is giving someone a hard time now... so i prefer to get it from apt-get :) so i suppose there isnt much problem with the older builds from apt-get repositories, rite? (in am in gutsy repo now)

thanks in advance for the answers. Cheers!

---

### Post by keineAhnung on 2007-05-17
Hi whiteford

we had the same problem.The reason seems to be that mindi does not load the kernel modules
in the same order as ubuntu, causing the 'wrong' module taking over the IDE-Disks.  The following trick worked

1) vi `which mindi`

comment out the line starting with "IDE_MODS=" (around line 72)

put in the following string

IDE_MODS="libata ata_piix generic"

This might be different for your machine. We basically removed all modules that were not loaded
on the running system (check with lsmod) This makes mindi see your harddisk as /dev/sdXX

2) mondo/mindi does not yet deal correctly with the UUID schema for identifiying your 
    filesystems. This can be changed by editing 

a) /etc/fstab : remove all UUID identifiers and replace them by 'normal' /dev/sdXX lines, e.g.

/dev/sda1 / ext3 default,errors=remount-ro 0 1

b) /boot/grub/menu.lst

Make your kopt-line to look like this (NOTE: Your root partition may not be sda1!)

# kopt=root=/dev/sda1 ro

c) The ubuntu-version of /sbin/update-grub will REWRITE this line every time back to 
    a UUID line. To  disable this, edit /usr/sbin/update-grub and around line 800 you will 
   find 

# Update the root device to mount-by-UUID
kopt=$(convert_kopt_to_uuid "$kopt")

  and now simply comment out the line starting with "kopt". To test your changes,
rerun update-grub and then check your /boot/grub/menu.lst.

With these changes, the current mondo/mindi version of ubuntu works ok.

:):):)

---

### Post by afilonov on 2007-06-22
I wonder if anybody tried version 2.2.4 (in Mondorescue repositories: [ftp://ftp.mondorescue.org/ubuntu/7.04/)?](ftp://ftp.mondorescue.org/ubuntu/7.04/)?) They claim that UUID bugs are fixed.

---

### Post by whitefort on 2007-06-23
I've been trying various versions and following tips from Mondo's creator - but stull haven't succeeded in getting Mondo to work with Feisty (Dapper is fine).

---

### Post by maxrisc on 2007-08-04
I just tried the latest Mondo out of the repos and I can assure you that the UUID problem has not been resolved.

I am looking into this now to see if there is a simple way to recover.  For the moment I had to remove the UUID from the Grub menu and specify root=/dev/hda1

I will post back my findings.

---

### Post by maxrisc on 2007-08-04
Well actually the problem is resolve with UUID but if you change hard disks you are gonna be up a creek without a paddle.

So here is a quick how to recover when changing out your disk for a different and getting GRUB to boot up accordingly.

First things first.

Boot your comp and press escape at the menu.

Press E to edit then use your arrow keys to select the line that says kernel and press E again.

You will see a line that has something like root=UUID=xxxxxxxxxxxxxxx ro 

Make it match your partition information   root=/dev/hda1  (I have an IDE hard disk for scsi it would be /dev/sda1)

Press enter.  Then B for Boot.

Once your system comes up it is going to complain about a lot of things.  Simply ignore them.

If you are in KDE/Gnome/XFCE etc open two terminal windows.

If you are on the console get out your pen and paper.

You will need to run the comman "sudo blkid"  This will echo all of your partition UUIDs.

Right down the correct UUID for your root partition /dev/hda1 or /dev/sda1

Now run "sudo nano /boot/grub/menu.list"

You will need to find the line that has KOPT in it.  It looks like this.

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ecb7480c-7756-4952-b2f9-da9894a6773e ro

```

On the kopt line put in the UUID you wrote down or copied.

Press CTRL+X to exit and save your changes.

Now we are all set to do things the Ubuntu way.   Run "sudo update-grub" and it will replace all instances in your boot loader with the correct UUID.

The only other thing left to do is edit your filesystem table.

Run "sudo nano /etc/fstab" and replace the UUIDs in this file with the UUIDs from the BLKID command you ran earlier.  

Now save that file and reboot.

Enjoy your new hard disk.

---

