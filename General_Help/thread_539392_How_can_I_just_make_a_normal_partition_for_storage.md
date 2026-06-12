---
title: "How can I just make a normal partition for storage?"
date: 2007-08-31
forum: General Help
---

### Post by Zef_ on 2007-08-31
I've seen people saying it's possible, but I just don't get how to do it. I just want a primary partition for linux, along with the swap partition, and additional /home partition, and then just a completely empty partition that's easy to access, but I don't understand as it requires a specific kind of mount point. Can I just type /storage as a mount point and would it work like that?

So on a single 320 gig HD something like this

50gb for /
2gb for /swap
60gb for /home
rest of the hard drive just for general storage.

The first 3 partitions I know how to do, but don't understand what sort of mount point I need to use for the general storage partition.

---

### Post by kesman on 2007-08-31
I think the name could be anything, just like /storage. Physically the mount point would be then /storage, but I personally would then mount it to /home/user/storage too to make it easier to access. I'm not sure if you need a mount point at all for the beginning, as you install a new drive, it will be somewhere in /dev/hd(something) or /dev/sd(something) and then you can mount it to anywhere you like.

---

### Post by Zef_ on 2007-08-31
Hmm, ok I understand that. I just want the mount point to be independent of the actual os file system. For example in xp, the partition would just show up as an entirely separate drive in explorer, and you could treat it as such. You could safely format drive C: and leave the D: drive untouched. This is the sort of certainty I want to have :\

Just so hard to find good documentation that's easy to understand if you are new to the filesystem.

---

### Post by callan79 on 2007-08-31
> **Zef_ said:**
> So on a single 320 gig HD something like this

50gb for /
2gb for /swap
60gb for /home
rest of the hard drive just for general storage.

The first 3 partitions I know how to do, but don't understand what sort of mount point I need to use for the general storage partition.


Actually it's not that hard to do, but I know what you mean about the Linux file system taking some getting used to!

In traditional Linux/Unix, file systems were mounted underneath the /mnt directory, so for example /mnt/storage. These days in Ubuntu you mount them under /media. So you have for example /media/cdrom, /media/storage, /media/usbdrive, /media/ipod, etc.

You can do all this while you're installing Ubuntu, but if you want to do it later then this is what you need to do :

```
sudo apt-get install gparted
sudo gparted
```

This will get you into a nice graphical partition manager. You can create your 200GB storage partition with this tool. It's actually irrelevant whether this partition is on the first drive, or a separate hard drive, the process is the same. Format the partition as ext3 (Linux file system).

Then when that's done, you need to create a mount point for it :

```
sudo mkdir /media/storage
sudo chown AAAA:BBBB /media/storage
sudo chmod 777 /media/storage
```

In the above, AAAA is your Ubuntu username, and BBBB is your Ubuntu group name (probably the same as your username).

Then you need to edit your fstab to the drive is mounted to the mount point :

```
sudo nano /etc/fstab
```

and enter the following line :

```
/dev/hda4    /media/storage     ext3    defaults        0       2
```

Note that /dev/hda4 is an example, and your GPARTED program above will tell you the real name, could be /dev/hdb4, /dev/sda4, etc.

Let us know how you go with that...

Cheers
Callan

---

### Post by Zef_ on 2007-08-31
Well to be honest I was hoping that I could do what is to my mind a relatively simple thing without  having to use the command line and edit configuration files. Ah well, I'll give it a shot anyway.

---

### Post by callan79 on 2007-09-01
> **Zef_ said:**
> Well to be honest I was hoping that I could do what is to my mind a relatively simple thing without  having to use the command line and edit configuration files. Ah well, I'll give it a shot anyway.

Hi,

Actually I just had a look and if you want to do this without command line, try :

  -  Applications >> ADD/REMOVE
  -  Select GNOME PARTITION EDITOR from the system tools category
  -  Once installed, you can start Gnome Partition Editor from the System >> Administration menu
  -  Go make your partition as explained earlier
  -  You'll still need to go create your /media/storage directory as explained  earlier

Once the partition is made :

  -  Places >> COMPUTER
  -  Right click on the new partition in there (should be labelled 200GB volume, or similar)
  -  Choose VOLUME tab
  -  See if you can make this work :-)

My advice though, as much as the command line can be a pain, if you learn to use it for even basic commands, it's REALLY USEFUL for so much stuff, and once you are comfortable with it, life becomes so much easier (trust me - I started with no LInux command knowledge, 18 months ago, now I'm no wizard, but I'm certainly willing to learn).

Cheers
Callan

---

