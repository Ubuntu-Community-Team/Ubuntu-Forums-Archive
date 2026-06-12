---
title: "Major Problem with external Hard Drives - nobody can figiure it out - plz help!"
date: 2007-12-24
forum: General Help
---

### Post by Syndacate on 2007-12-24
I'll try to make this as short, sweet, and to the point as possible.

I have Kubuntu Gutsy (with ubuntu desktop) installed on a P4 3.0 proc. with an IC7-G MB, and a SATA200gb HD, 256mb radeon rage 9550 - nothing special, an old gaming computer.

I have a 750GB Buffalo external hard drive enclosure with dual 375's inside.

I plug it in, it recognizes both drives (they show up).  It mounts one of them (a particular one) automatically in Gnome, and in KDE it doesn't mount either.  In KDE it fails to mount either if you right click >> mount - you have to use Thundar, and even then it can only mount one of them.  Here, in Gnome, both of them show up, it automatically mounts the one that could be mounted in KDE, and doesn't mount the other one, right clicking on it >> mount gives you an error message of the following (which is the same error message Thundar gives me if I try to mount in KDE):

```

fuse: failed to access mountpoint /media/sdc5:  No such file or directory
FUSE mountpoint creation failed
Unmounting /dev/sdc5 (HD-WIU2)

```

So that would lead one to believe that my fstab file is off or something...butttt it isn't, as this is they:

**cat /etc/fstab**
```

# /dev/sdb5
UUID=C18E2B918E2A0C6 /media/sdb5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
# /dev/sdc5
UUID=E45C77555C77220A /media/sdc5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8

```

**blkid**
```

# /dev/sdb5
UUID=C18E2B918E2A0C6 /media/sdb5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8
# /dev/sdc5
UUID=E45C77555C77220A /media/sdc5 ntfs-3g defaults,noauto,user,locale=en_US.UTF-8

```

I don't understand it, nobody can figure it out.

Please, I need to get to this drive.

PS:  It's only one (particular) of the drives, it's not like it's random each time.

Thanks in advance....please help :(

---

### Post by ~LoKe on 2007-12-24
```
sudo mkdir /media/sdc5
sudo mount -a
```
?

---

### Post by Syndacate on 2007-12-24
> **~LoKe said:**
> ```
sudo mkdir /media/sdc5
sudo mount -a
```
?

No go.

```

syndacate@syndacate-desktop:~$ sudo mkdir /media/sdc5
mkdir: cannot create directory `/media/sdc5': File exist

```

I think it runs the command:
```

sudo mount -a

```

at boot, but I ran it anyways, no go, same error message when I try to mount it through File Browser too.

:(

Anybody else have any suggestions?

---

### Post by zarqoon on 2007-12-24
in my /media directory the directorys for the ntfs drives i mount dont exist before i mount them(by clicking them in nautilus). Try deleting the directory (check that its really not mounted so you dont accidently delete your drive).

---

### Post by Syndacate on 2007-12-24
> **zarqoon said:**
> in my /media directory the directorys for the ntfs drives i mount dont exist before i mount them(by clicking them in nautilus). Try deleting the directory (check that its really not mounted so you dont accidently delete your drive).

Can you repeat that?  I don't understand, completely.

---

### Post by Syndacate on 2007-12-24
Anybody else?  C'mon, somebody's gotta know...

---

### Post by Ocxic on 2007-12-24
try deleting the folders for your drives, just make sure your drives are NOT mounted or it will result in data loss. you can check if there mounted by useing the command "mount" that will give you a list of everything currently mounted.

---

### Post by dasunst3r on 2007-12-24
+1 for pulling out the drive and then deleting the directories in /media (all of them except for the cdrom ones).  Then, try plugging the drive back in and see if it automounts.

---

### Post by Syndacate on 2007-12-24
> **Ocxic said:**
> try deleting the folders for your drives, just make sure your drives are NOT mounted or it will result in data loss. you can check if there mounted by useing the command "mount" that will give you a list of everything currently mounted.

I can't.

```

syndacate@syndacate-desktop:/media$ ls -l
total 18
lrwxrwxrwx 1 root       root          6 2007-12-20 08:24 cdrom -> cdrom0
dr-xr-xr-x 4 4294967295 4294967295  136 2006-05-05 04:30 cdrom0
lrwxrwxrwx 1 root       root          7 2007-12-20 08:24 floppy -> floppy0
drwxr-xr-x 2 root       root       4096 2007-12-20 08:24 floppy0
drwxrwx--- 1 root       plugdev    8192 2007-12-21 02:54 sda1
drwxr-xr-x 2 root       root       4096 2007-12-24 06:14 sdc5
syndacate@syndacate-desktop:/media$ sudo rm -rf /sdc5/
syndacate@syndacate-desktop:/media$ ls -l
total 18
lrwxrwxrwx 1 root       root          6 2007-12-20 08:24 cdrom -> cdrom0
dr-xr-xr-x 4 4294967295 4294967295  136 2006-05-05 04:30 cdrom0
lrwxrwxrwx 1 root       root          7 2007-12-20 08:24 floppy -> floppy0
drwxr-xr-x 2 root       root       4096 2007-12-20 08:24 floppy0
drwxrwx--- 1 root       plugdev    8192 2007-12-21 02:54 sda1
drwxr-xr-x 2 root       root       4096 2007-12-24 06:14 sdc5

```

Does anybody else have any other ideas?

I can't believe an external hard drive refuses to work with Ubuntu, especially since one external works fine and my USB works fine.

---

### Post by ugm6hr on 2007-12-24
Does GParted (System->Administration->Partition Editor) see the drive?

If so - maybe that can mount it?

---

### Post by zionpsyfer on 2007-12-24
You ran the command *syndacate@syndacate-desktop:/media$ sudo rm -rf /sdc5/*

You tried removing the directory /sdc5 instead of /media/sdc5.  You'll notice in the ls -l you did that the creation times were the same.  Either get rid of the / before the sdc5  so that you're using the relative path.... or use the absolute path of '/media/sdc5'.


i.e. 

sudo rm -rf /media/sdc5

OR

cd /media
sudo rm -rf sdc5




As the prior posts stated, make sure that sdc5 is unmounted prior to running the command.  Matter of fact, let's make this easy.  Power both drives down and run the commands on those two directories.  Then just power the drives on.

---

### Post by Syndacate on 2007-12-24
> **ugm6hr said:**
> Does GParted (System->Administration->Partition Editor) see the drive?

If so - maybe that can mount it?

Wow

I don't have that.

I have Kubuntu with GDE installed.

I searched System >> Administration >> - nothing there resembling "partition" or "editor"

So I checked and said "maybe I'll find it in the same place it stores thundar..."

So in "system tools" while looking for Thundar I find "NTFS Configuration Tool" - So I said "hrm..." and click on it.

There's two boxes, one said "enable NTFS write for internal" - the other says "enable NTFS write for external."

I clicked external, opened www, and the drive mounted right up - both of them.

The only thing now is in "NTFS Configuration Tool" It's EITHER, enable for internals, or enable for externals, not both.  So what happens to the 120GB partition on the same drive that Kubuntu is installed on (internal). ??

---

### Post by insert_name_here on 2007-12-24
You can install gparted with "sudo aptitude install gparted" in konsole.

Have tried telling mount exactly what to do?

Try:  mount -t ntfs-3g /dev/sdc3 /media/sdc3

(assuming /dev/sdc3 is the device name - that is the 3rd partition on the 3rd SCSI SATA or USB hard disk - it's more likely to be sdc1.  And make sure /media/sdc3 exists)

---

### Post by Syndacate on 2007-12-24
> **insert_name_here said:**
> You can install gparted with "sudo aptitude install gparted" in konsole.

Have tried telling mount exactly what to do?

Try:  mount -t ntfs-3g /dev/sdc3 /media/sdc3

(assuming /dev/sdc3 is the device name - that is the 3rd partition on the 3rd SCSI SATA or USB hard disk - it's more likely to be sdc1.  And make sure /media/sdc3 exists)

Things just changed.

Before when I clicked "enable write access for external hard drives" the other box unchecked, but now when I just did it - they're both checked.  Now everything's mounted both the other partition of this hard drive and both of my external drives).  

Everything appears 100% normal, actually, I'm going to try and restart and see if anything changes...

---

### Post by Syndacate on 2007-12-24
Yeah, everything seems to work, thank you all very much.

Hey, just a quick Q, should I be unmounting these external drives before I reboot?

---

### Post by Syndacate on 2007-12-24
> **ugm6hr said:**
> Does GParted (System->Administration->Partition Editor) see the drive?

If so - maybe that can mount it?

I figured it out man.

In the NTFS Configuration Tool "Enable Write Access on External Drives" wasn't checked - I checked that, it works now, and mounts automatically when I boot.

Should I be unmounting them (the externals) before I restart?

---

### Post by ugm6hr on 2007-12-25
> **Syndacate said:**
> I figured it out man.

In the NTFS Configuration Tool "Enable Write Access on External Drives" wasn't checked - I checked that, it works now, and mounts automatically when I boot.

Should I be unmounting them (the externals) before I restart?

Glad it works.  Your problem was in fact pretty simple.  Funny that in giving my advice (which would not have helped), you found the solution yourself!

As for unmounting before restarting or turning off - unless Kubuntu behaves differently to Ubuntu - it should unmount all drives automatically when you turn off / restart.  So, in theory the answer is - you can if you want, but it is not necessary.

I hope that's the correct answer this time ;)

---

### Post by dasunst3r on 2007-12-25
Indeed -- the kernel will do the umounting procedure as you shut down or restart -- it is completely independent of the window manager.  Just to play it on the safe side, *do* eject the device whenever you intend on pulling it out.

---

### Post by Syndacate on 2007-12-26
Yeah, I know that the scripts unmount it when I shut it down, I was just wondering if like pulling it out when it's not ejected, shutting it down when it's not ejected could cause data corruption?  That's all.

---

### Post by ugm6hr on 2007-12-26
> **Syndacate said:**
> Yeah, I know that the scripts unmount it when I shut it down, I was just wondering if like pulling it out when it's not ejected, shutting it down when it's not ejected could cause data corruption?  That's all.

Pulling it out when it's not ejected can cause potential problems - generally all the changes made since the last eject will be messed up.

Shutting down when not ejected is not an issue - Ubuntu will not allow it.  It will unmount before shutting down automayically.

---

### Post by Syndacate on 2007-12-26
> **ugm6hr said:**
> Pulling it out when it's not ejected can cause potential problems - generally all the changes made since the last eject will be messed up.

Shutting down when not ejected is not an issue - Ubuntu will not allow it.  It will unmount before shutting down automayically.

Gotcha, so if there's an error in processing the unmount script when shutting down Ubuntu won't continue anyways and shut down with it still mounted?

---

### Post by ugm6hr on 2007-12-26
> **Syndacate said:**
> Gotcha, so if there's an error in processing the unmount script when shutting down Ubuntu won't continue anyways and shut down with it still mounted?

I'm no expert, but I don't think it can turn off without unmounting all drives.  I have certainly never had a problem.

---

### Post by Syndacate on 2007-12-26
> **ugm6hr said:**
> I'm no expert, but I don't think it can turn off without unmounting all drives.  I have certainly never had a problem.

Yeah, me neither, just looking to be prepared, y'kno?

---

### Post by kelvin spratt on 2007-12-26
If you are dual booting you need to boot up windows get it to force disc check on the drives. Then you need to get windows to safely unmount the drives reboot to windows unmount again then boot into Linux, hopefully your drives should now be Ok..My ext drive is permanently connected to my  desktop,

---

### Post by Syndacate on 2007-12-27
> **kelvin spratt said:**
> If you are dual booting you need to boot up windows get it to force disc check on the drives. Then you need to get windows to safely unmount the drives reboot to windows unmount again then boot into Linux, hopefully your drives should now be Ok..My ext drive is permanently connected to my  desktop,

Mine is permanently connected too.  Force disc check?

---

### Post by kelvin spratt on 2007-12-27
Your posts show the drives you have problems with are NTFS is that true. If it is when ntfs partitions get corrupted for any reason then Linux does not allways mount them as they are unclean, You then have to either use windows to force disc check the partitions, reformat the complete h/drive or try to repair the partition? If you don't have windows plug your h/drive into someone elses, go to my computer right click on the drive icon click on disc tools you will then see an entry to check and try to repair the partition it has to boxes click both boxes follow the instuctions. do that on all drives on your h/drive. I use kubuntu with a mix of drive formats out of the box it sees and mounts them all as read/write with no problems that goes with all the 7.10 releases its out the box the only problems I get is with dirty ntfs drives. I hope this is helpful to you as i don't like to offend people by trying to spell things out.

---

### Post by Syndacate on 2007-12-27
The problem was simply that Ubuntu wasn't set to write to NTFS drives.

After I set that they worked fine.

---

