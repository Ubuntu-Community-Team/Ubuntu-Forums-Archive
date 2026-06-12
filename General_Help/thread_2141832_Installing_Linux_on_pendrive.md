---
title: "Installing Linux on pendrive"
date: 2013-05-03
forum: General Help
---

### Post by VirginiaDrifter on 2013-05-03
All the information I can find for installing Linux on a pendrive (thumbdrive, flashdrive, whatever they're called) ( [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) ) says to install from the ISO and use [SIZE=2]the persistence to save files and such.

What I did seems a lot easier and I can take my whole system with me, not just a live version. (I used Xubuntu for this)

I unplugged my hdd.
Booted Xubuntu live cd
Connected USB flash drive (16Gb)

Then just went through the regular install. Installed updates. Installed Keepass x and Dropbox, which are the only 2 things I really need to access if I am traveling. Plus I still have plenty of space left instead of only the 4Gb [/SIZE]persistence allows you.
[SIZE=2]
As the title says, is anything wrong with this? Just wondering why this isn't mentioned as an option for installing on flash drives? I've booted it 3 or more times and no problems.  [/SIZE]:confused:[SIZE=2]




[/SIZE]

---

### Post by snowpine on 2013-05-03
No problem at all. Do a forum search for posts by user "C.S.Cameron" and you will find much discussion of this method. Probably it is not discussed much because it is so obvious; a drive is a drive is a drive, and the Ubuntu installer doesn't care whether the drive is physically inside of or outside of your computer. :)

---

### Post by VirginiaDrifter on 2013-05-03
Thanks snowpine. I'll check out those other posts.

---

### Post by Atitudes on 2013-05-03
Thanks snowpine, found the answers from C.S.Cameron very useful and also this [thread]("http://ubuntuforums.org/showthread.php?t=2130569")  that was very helpful. I will try the latter for sure! Nice way to show  a full customized Ubuntu to friends while making it very useful for  ourselves!! Thanks VirginiaDrifter for bringing this up.

---

### Post by C.S.Cameron on 2013-05-03
About the only advantage of a "Persistent" install over a "Full" install is it fits on a drive 4GB and under.
Nowadays 8GB is small for a flash drive, so that is not a big deal.
Another possible advantage is that a persistent install may make fewer writes to the drive, (maybe extending it's life from 10 years up to to 20 years), but I have seen no hard facts.
Other advantages of a Full install is that it boots faster, can be updated/upgraded and is more secure.
I have several of each that I use for different purposes.

---

### Post by Atitudes on 2013-05-03
> **C.S.Cameron said:**
> About the only advantage of a "Persistent" install over a "Full" install is it fits on a drive 4GB and under.
Nowadays 8GB is small for a flash drive, so that is not a big deal.
Another possible advantage is that a persistent install may make fewer writes to the drive, (maybe extending it's life from 10 years up to to 20 years), but I have seen no hard facts.
Other advantages of a Full install is that it boots faster, can be updated/upgraded and is more secure.
I have several of each that I use for different purposes.

Sorry for my noobiness but what is the real difference between "Persistent" and "Full" installation on a flash drive? Is it that the "Persistent" still leaves space for other files/partitions making the flash drive slower than a full dedicated one?

Also, regarding your very explicit and useful [post]("http://ubuntuforums.org/showthread.php?t=2139675"), is there any way to make a "full" installation without having to disconnect the hard drive? I thought the DVD->Flash drive option found [here]("http://ubuntuforums.org/showthread.php?t=2130569") would be a similar installation, resulting in a "full" installation. Does it?

Sorry for "mixing threads" but I am really curious now!

---

### Post by C.S.Cameron on 2013-05-04
A Full install is just like an install to internal drive, all of the individual files are extracted to the drive and are ready to use.
A Live install uses a read only squashfs file, (compressed similar to a ZIP file), the individual files are extracted as required.
Since filesystem.squashfs is read only, customizations such as newly install programs, etc are lost when the session is ended.
With a Persistent install changes are saved to a file or partition named casper-rw, (or home-rw). 
As a Persistent file, there is a limit of 4GB imposed by the FAT32 file system, Persistent partitions have no such limit.

If you are careful, it is possible to install without disabling the internal drive.
When you get to "Installation type" choose "Something else", then select the external drive for  install and as "Device for boot loader installation".

If you install this way the internal drive will be included in grub, but that is no big deal.

Yes your link is for a Full install, pay attention to the words in **bold**.

The reference in that post to Persistent CD is highly complex, all it takes is a flash drive formatted ext2 and labled casper-rw than pressing F6 when booting from the CD and typing <space>persisent.

---

### Post by Atitudes on 2013-05-04
Thank you very much for your kind explanation, I will definitely give it a try to show and use Ubuntu Studio with some friends at the studio and get another regular one for my personal use!

---

### Post by VirginiaDrifter on 2013-05-04
Thanks everybody :). A lot of good information and links posted.

---

