---
title: "C Drive"
date: 2007-09-21
forum: General Help
---

### Post by Major Crash on 2007-09-21
This may be a stupid question.  I'm new to Ubuntu.

Shouldn't I be able to see my C Drive?  I can see my external hard drive.  Am I missing something?

---

### Post by maybeway36 on 2007-09-21
The hard drives aren't lettered in Unix, they use a mounting system. Try looking in System>Computer for GNOME or System Menu>Storage Media for KDE.

---

### Post by Major Crash on 2007-09-21
I was able to see the drive when I was trying Ubuntu from the CD, but now that it's installed I can't see it.

---

### Post by Gremlinzzz on 2007-09-21
Click places then computer your c drive will be there just no letter

---

### Post by Major Crash on 2007-09-21
All it shows is my cd drive, my external hard drive, and filesystem.  Is filesystem the hard drive I'm looking for?

Also, I'm dual-booting with Windows Vista, vista installed first.

---

### Post by purplenite on 2007-09-21
> **Major Crash said:**
> All it shows is my cd drive, my external hard drive, and filesystem.  Is filesystem the hard drive I'm looking for?

Also, I'm dual-booting with Windows Vista, vista installed first.

Yes, filesystem is like your "C Drive"

---

### Post by maharbA on 2007-09-21
Welcome to Ubuntu!

The first thing I did when I installed Ubuntu is to put "Music" "Pictures" "Documents" and "Video" folders in my "home" folder (/home/<your user name>).

I basically treat my home folder as the "C" drive in Windows -- that's where I save everything so it's easy to backup.

Some applications like to put things elsewhere in the filesystem, so it's a good idea to get to know those other folders, but for now I'd keep to the home folder.

---

### Post by strabes on 2007-09-21
> **Major Crash said:**
> This may be a stupid question.  I'm new to Ubuntu.

Shouldn't I be able to see my C Drive?  I can see my external hard drive.  Am I missing something?

Are you talking about seeing the drive that contains your windows files? If so, it should be in the "Places" menu. If it's not, paste the output of this command: ```
cat /etc/fstab
```

If you're talking about the drive that contains your ubuntu files, that would be the "Filesystem"

If you wish to be able to write to your windows partition you should install the packages ntfs-3g and ntfs-config:```
sudo apt-get install ntfs-3g ntfs-config
```

You can access the ntfs-config program by running:```
sudo ntfs-config
```

---

### Post by bobjones2 on 2007-10-16
Hi, I am completely new to ubuntu.  Please be patient with me for hijacking this thread, but I had some more questions about how "C:" drive is mentioned under linux.

Like the parent poster, I also see a File System drive and my secondary windows drive.

I noticed that I can access all my files in my windows drive under ubuntu.  I also noticed that when i right click and hit properties for my windows drive, it tells me how much space it has and how much it's using.

Is there a way to find out this information on my Ubuntu drive?

Also, I noticed that although i can see my hard drive on Ubuntu, I can't see my Ubuntu drive under windows.  Is this on purpose for security reasons, or did I screw up on my Ubuntu installation?  

I installed Windows XP first on my E: drive (i know, i'm a novice).  then on my free C:drive I installed Ubuntu.

Once I figure out how to configure my wirelss adapter my windowless life will begin! :)

---

### Post by bodhi.zazen on 2007-10-16
> **bobjones2 said:**
> Hi, I am completely new to ubuntu.  Please be patient with me for hijacking this thread, but I had some more questions about how "C:" drive is mentioned under linux.

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

> Like the parent poster, I also see a File System drive and my secondary windows drive.

I noticed that I can access all my files in my windows drive under ubuntu.  I also noticed that when i right click and hit properties for my windows drive, it tells me how much space it has and how much it's using.

Is there a way to find out this information on my Ubuntu drive?

The Ubuntu drive is "file system" or /

> Also, I noticed that although i can see my hard drive on Ubuntu, I can't see my Ubuntu drive under windows.  Is this on purpose for security reasons, or did I screw up on my Ubuntu installation?

No, windows is lacking many many features, including drivers to read many file systems.

See this link : _For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

> I installed Windows XP first on my E: drive (i know, i'm a novice).  then on my free C:drive I installed Ubuntu.

Once I figure out how to configure my wirelss adapter my windowless life will begin! :)

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

	[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

	[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by bobjones2 on 2007-10-17
thank you!

---

