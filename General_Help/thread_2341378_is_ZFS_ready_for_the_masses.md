---
title: "is ZFS ready for the masses?"
date: 2016-10-27
forum: General Help
---

### Post by rclocher3 on 2016-10-27
I've read about the wonders of ZFS, how it can [detect and automatically repair bitrot]("http://arstechnica.com/information-technology/2014/01/bitrot-and-atomic-cows-inside-next-gen-filesystems/"); and also act like a RAID mirror, so that if one disk fails the system continues to work fine, and the user is notified to replace the failed drive.  These features sound like things I could use.

On the other hand, it doesn't sound like the Ubuntu installer offers to install ZFS.  The ZFS documentation that I've seen doesn't seem as though it's aimed at ordinary users; it seems aimed more at administrator-types who play with complex storage arrangements like logical volumes and the many flavors of RAID for a living.  Also I saw [this wiki page]("https://wiki.ubuntu.com/Kernel/Reference/ZFS") that says that ZFS is just for data storage, and not for the root filesystem; that implies that if I want to use it for mirroring and to prevent bitrot on my desktop computer, then I would need three drives: one for the root filesystem, and two for a ZFS-configured mirror.

I'm just a tinkerer with Ubuntu, and not a paid administrator-type.  Is ZFS simple enough for people like me to think about playing with?  I don't want to wake up one morning and discover that my system won't boot and that I have all sorts of clever manual GRUB configuration to do just to get my system to boot again...

---

### Post by kevdog on 2016-10-27
The problem is that I dont think the ZFS kernel drivers are distributed in the mainline linux kernel -- in fact I know they are not since Linus went on some rant about ZFS on day.  That makes it rather difficult when the kernel is upgraded, unless when the kernel supports dkms.  With a dkms kernel supporting ZFS, I believe it is possible for /root to be as a ZFS file system. Honestly however Linux support is sketchy at best.  Supposedly Ubuntu was going to be the only linux distro with all their kernels released with ZFS support, however I'm not exactly sure if this is true.  This subject is discussed frequently over at Arch Linux forums and they use dkms modules for their ZFS drivers, however these are maintained by a third party (who at one time was a big contributor to these Ubuntu forums!!!). The entire linux solution is kind of wonky.  If wanting to use ZFS for a NAS, it probably better just to go with a bsd variant or FreeNAS (another BSD variant), where ZFS support is built into the kernel

---

### Post by rclocher3 on 2016-10-27
Thanks @kevdog, you've convinced me to not mess with ZFS yet, if the kernel doesn't support updating when the root filesystem is on ZFS.  I have a desktop computer that I use for everyday use that also has all my important files; I don't want to support a separate device as a NAS, and I don't want to have three spinning drives running up my electric bill.  (Of course a solid-state drive would help.)  Time to learn about RAID1 via mdadm...

---

### Post by oldfred on 2016-10-27
Note that RAID is not backup, but just to maintain system running.

       If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[URL="http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/"]http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/
[/URL]
 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 

      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) 
    [URL="http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/"]
[/URL]

---

### Post by rclocher3 on 2016-10-27
Thanks for the advice and the interesting links @oldfred!  I plan to use RAID1 so that if a drive fails I get a nice polite email, instead of a system that I need to rebuild and a backup that I need to restore.  I realize that RAID won't do squat for me if my house burns down.   I have a proper backup system in place, and just for grins I even test it from time to time.

---

### Post by alexjpowell on 2016-10-27
What are you actually going to be using your system for?

---

### Post by kpatz on 2016-10-27
I'm running ZFS on my new 16.04 file server I built, but not as a boot drive.  I don't think booting from ZFS is well supported in Linux, if at all.  I just use ZFS (a mirrored pair of 4 TB drives) for data storage, the OS is on a 120 GB SSD.  I like it so far, sending snapshots to another machine for backup is a snap, or save them on an external USB drive.

So far it seems to work well.  Time will tell how well it holds up, how stable it is.  Btrfs is another option which has some intriguing features I wish ZFS had such as file-level deduplication, but btrfs isn't really considered stable for production use.

---

### Post by rclocher3 on 2016-10-30
> **alexjpowell said:**
> What are you actually going to be using your system for?

The computer I'm talking about is my home computer that I use for everyday stuff.  I have about 15 years' worth of pictures, emails, and documents on it.  A NAS might make sense, except I don't want to complicate my life with another device.

---

### Post by kevdog on 2016-10-30
If you have another computer in the house -- that could be your poor man's NAS.  I understand about your 15 years worth of data -- loosing all of that would be catastrophic since it probably couldn't be replaced.  I'd definitely look at duplicating the data somewhere.  RAID 1 is a start however you probably need another copy somewhere else.  I don't know a lot about btrfs...I've looked at it but never really never used it.  ZFS on linux is stable as long as you don't format your /boot partition with it.  However even using well established backup systems beyond a file system feature is advantageous.  rsync is probably the easiest soloution, however if you need snapshots, you'll need something like rsnapshot or duplicity.  I'm currently using a program called borg.  This is a versioned backup system similar to rsnapshot, however you can encrypt your backups as well.  The only versioned, encrypted backup solutions I'm aware of are obnam and borg.  I've tried both.  I really like the Larz who is the author of obnam, although I didn't find obnam to be nearly as stable as borg when testing the products over several months.  At a minimum I'd recommend you either use rsync, rsnapshot or another program and backup that important data of yours to possibly another computer in your house. A lot of other people swear by offsite solutions like SpiderOak, however I've never used this.  Others here in the forums could probably tell you about other online backup solutions.

---

### Post by Roasted on 2016-10-30
Regarding BTRFS, I'm pretty sure I saw a Twitter post a few weeks/months ago that literally stated they recommend ZFS for certain RAID environments as some new/not previously disclosed findings were that your data was at a pretty high risk of loss.

Personally, I'm a boring person. I stick to ext4 partitions on a software raid array with mdadm. It works well, does the job, and I really don't have any complaints about it.

I'd be happy to share some of my experiences/processes with you in case it helps. If it doesn't, well, maybe somebody reading this thread in the future may benefit. :D

Truth be told, I'm not a fan of cloud storage (except my beloved Nextcloud box). I want my data in my control on my devices. As a result, I never considered third party storage, so I can't really comment on that. That said, I have a file server at home -- nothing special, just a low end/low wattage i3, 6TB of storage (4x 3TB WD Reds) in a RAID 6. This serves as the central point of our network. It houses backups (every machine runs a quick rsync 60 seconds after logging in) as well as core storage. What I mean by core storage is some items we store on the server but no where else; we don't keep any pictures, music, etc on our actual computers. Instead we store everything on the server itself. This allows me to leverage small (therefore, cheap) SSDs in our laptops, desktop, etc and utilize the 6TB array for the good stuff. Using autofs, our systems auto mount the share when needed. Shotwell, for example, points to /media/user/vault/pictures (/media/user/vault being the autofs auto-mounted smb share). Fire up Shotwell and 36,000 pictures are presented to you in the UI. Same goes for music when we open Clementine, as Clementine's music dir is pointed to /media/user/vault/music, etc etc.

Point I'm trying to get across is our file server has turned into a must-have/would-be-lost-without-it device. Next up, backups. I have a 1TB (yes, only a 1TB) external hard drive. It's a 2.5" HDD I salvaged from a laptop that sustained water damage with a relative who gave me the old rig to gut. 10 dollars on Amazon later, I had an enclosure, and here we are. I work close to home, so once a week when I come home for lunch I bring the drive with me. It otherwise stays in my locked office at work. That way if my house gets abducted by aliens, I have my data -- or at least, most of it. Given there's 3TB of space in use on the server, and only 1TB of space on the drive, I choose only the most important items to sync -- documents (such as our tax documents, warranty information for certain things, etc etc), pictures, and backups (backups being the backups our systems run after logging in). Items I can afford to lose (basically anything you can regenerate, such as music files, TV shows, etc) get the back seat given my off-site storage availability.

What I do is I plug the drive in, SSH to my server, and type the word "backup". After entering my root password, it does its job, and unmounts automatically. After confirming the output from the rsync job(s) was error free, I unplug it, eat lunch, go back to work, and done.

```
#!/bin/bash
mount /dev/disk/by-uuid/0611280c-eb45-4be8-a02a-d861b6890374 /media/off-site-drive/
if findmnt UUID=0611280c-eb45-4be8-a12a-d861b6790374 > /dev/null; then
echo "Backup drive mounted. Backup starting..."
rsync -a --progress --delete /media/vault/backups /media/off-site-drive/
rsync -a --progress --delete /media/vault/documents /media/off-site-drive/
rsync -a --progress --delete /media/vault/pictures /media/off-site-drive/
sleep 5
echo "Unmounting backup drive..."
umount /media/off-site-drive
fi
exit
```

Basically, the script looks for the drive via UUID, mounts it, and if it sees that it's mounted, begins the sync. Once done, it unmounts, and.. that's it. The ability to type "backup" and it just work is done via an alias. At the bottom of .bashrc in my server user's home directory I have this:

alias backup='sudo bash /usr/local/bin/off-site-backup.sh'

If you work much further from home and don't like the idea of bringing the off-site drive home to spend the night so you can sync up (therefore your main storage + off-site is under the same roof; an alien's dream), consider using two and rotate them. That way one always stays at the office (or wherever). It may be more expensive than 5 dollars a month or whatever it would cost to lease 1TB of space from a cloud provider, but consider the pros and cons. Dropbox, for example, says right in their ToS there is zero guarantee for your data, even for paid accounts. At least I can plug in my off-site drive and see the new data there and know I'm covered. Likewise, these items get "paid for" and have no monthly costs -- something I greatly appreciate. Just my 2c.

If you're concerned about power usage (understandable -- I was too), my UPS is currently reading an 81w load. My server is as follows:

i3 3220T 35w TDP processor
8GB RAM
1x 60GB SSD for Ubuntu Server
4x 3TB WD Red for RAID 6 @ /media/vault
1x 2TB WD Purple for video surveillance storage (my file server is also a video surveillance server with Bluecherry)

On top of the server being on that UPS, I have some other items:
1x 24 port gigabit LAN switch
1x 8 port gigabit POE switch (this switch serves data+power to six 3 megapixel IP cameras)

So overall, I have my file/video surveillance server with 1 SSD and 5 spinning HDDs, along with two switches, one of which that's powering 6 IP cameras. Sure, I'd like to see that 81w be more like 18w, but all things considered, I wouldn't be without it. :D

---

