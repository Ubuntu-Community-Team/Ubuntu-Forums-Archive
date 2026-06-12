---
title: "Clonezilla errors sector"
date: 2015-05-22
forum: General Help
---

### Post by RobGoss on 2015-05-22
Hello everyone, I'm  running 32 but version of Ubuntu 14.02 LTS. I wanted to start making backups regularly but I'm not sure what would be the best methods.

I was trying to use Clonezilla but each time I place the live DVD or USB drive in and try to boot in to Clonezilla I get a error saying something  about missing sector. If anyone has any idea's  on why this occurs please let me know.

Oh and I did download a 32 bit version of Clonezilla as well.

If anyone has a better backup method please advise.

Thanks so much

---

### Post by monkeybrain20122 on 2015-05-22
Use fsarchiver. [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

It just copies the file system, much more flexible (can restore to smaller partition as long as large enough to hold data) and can do the imaging while using the computer. Install it from the repo.
[http://ubuntuforums.org/showthread.php?t=2221842](http://ubuntuforums.org/showthread.php?t=2221842)

---

### Post by RobGoss on 2015-05-22
Hello and thanks so much for responding. How accurate is thisomething method for backing up the whole system?

I want something that will work good and I can count on. Thank you

---

### Post by leunam12 on 2015-05-22
What is the exact error that Clonezilla gives you?

---

### Post by monkeybrain20122 on 2015-05-22
I don't know about clonezilla, but Fsarchiver is simple to use and has been reliable, it just copies the file system, compresses it and then restores. Clonzilla seems to be more complicated and more restrictive because it record other unnecessary info pertaining to the sectors I think(so must restore to bigger partition even if original is mostly empty)

I don't know if fsarchiver works with uefi-gpt type set up though, never tried it and have heard conflicting reports.

---

### Post by efflandt on 2015-05-22
I don't know if Clonezilla has any methods yet to image or copy a partition other than sector by sector, but when I tried to use it on a failed laptop drive, it hung when it got to a bad sector it could not read at all. But that was a Windows drive on someone else's laptop, so I resorted to using a free version of Acronis from wdc.com to image file by file to put it on a Western Digital drive (Seagate also has a free copy if you have Seagate or Maxtor drive).

So when the Linux partition at the far end of my desktop drive started failing, I used Acronis to image my Win7 partitions (after shrinking Win7 to make more room for Linux), then reinstalled Ubuntu and copied over my home from the failing drive. Only a few Linux Steam game files had been corrupted, but checking integrity of game cache with Steam was able to replace those files.

I guess I should look at fsarchiver to see how if or how well it works, especially with a failing drive or Windows partitions. I still have that bad drive that I could try with a drive caddy that connects with eSATA or USB.

When upgrading from 12.04 to fresh 14.04 without a separate /home partition, I simply used cp -r to copy my home to a USB drive, then did the same to the new system after installation. But that was from/to same good drive, not a failing drive.

---

### Post by RobGoss on 2015-05-22
Thanks for the reply's but there must be better methods for backing up your Linux system. The ones mentioned here are ok but it seems they have problem and are harder then they look. I was hoping Clonezilla would work but it does not for some strange reason. I'm sure there is someone here who has a better approach and method, for keeping our systems safe.

---

### Post by monkeybrain20122 on 2015-05-22
I don't see how it is difficult to use fsarchiver. It is just one command and no sector by sector stuffs. Attach a medium where you want to store the backup. Say you want to clone the your /partition which is /dev/sda1 to /media/username/backups and the file name is ubuclone.fsa

```
sudo fsarchiver -v -j4 savefs -A -a /media/username/backups/ubuclone.fsa /dev/sda1
```
 
The options -a -A allow you to do to cloning while you are using the computer

If you must there is a gui which you can install in a usb. [http://sourceforge.net/projects/qt4-fsarchiver/](http://sourceforge.net/projects/qt4-fsarchiver/)

---

### Post by RobGoss on 2015-05-22
> **monkeybrain20122 said:**
> I don't see how it is difficult to use fsarchiver. It is just one command and no sector by sector stuffs. Attach a medium where you want to store the backup. Say you want to clone the your /partition which is /dev/sda1 to /media/username/backups and the file name is ubuclone.fsa

```
sudo fsarchiver -v -j4 savefs -A -a /media/username/backups/ubuclone.fsa /dev/sda1
```
 
The options -a -A allow you to do to cloning while you are using the computer

If you must there is a gui which you can install in a usb. [http://sourceforge.net/projects/qt4-fsarchiver/](http://sourceforge.net/projects/qt4-fsarchiver/)

Thanks so much my friend I was able to get Clonzilla to boot up I just downloaded a fresh copy. I will also look in to the one you recommended.

---

### Post by VMC on 2015-05-22
Look into "/var/log/*partclone*.*log". *that's where CZ puts its error results.

---

