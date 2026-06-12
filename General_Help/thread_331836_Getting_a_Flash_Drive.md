---
title: "Getting a Flash Drive"
date: 2007-01-05
forum: General Help
---

### Post by Sef on 2007-01-05
I'm looking at getting a flash drive (usb key, thumb drive) and just want to check some things:

1) With Linux, I should just be able to plug it in and it should work.  (I need to transfer some files from one computer to another.)

2) With Windows, I might need to install some software to make it work.

3) I should right click and select eject before unplugging it.

4) Are there any one that work better or are they all about the same?

5) Any tips to spotting fake flash drives?

6) Any other advice concerning flash drives?

---

### Post by bernied on 2007-01-05
1 - yes, in ubuntu you get a desktop icon that takes you to the treasure. It will get mounted on /media automagically
2 - If you stick with the FAT32 filesystem, it will work seamlessly in both OSes (but no permissions with FAT filesystems), else you could use ext2/3. In my experience, when windows sees this (ext2 or ext3) it says it's not formatted and wants to format the drive, but installing ext2 software for Windows might solve this.
3 - Some do, some don't. I do. To do this manually, use umount.
4 - I understand that there is a new security feature available on flash drives but I don't know whether it works in linux.
5 - never heard of this - is this like one of those Swiss watches that you can buy in third-world countries with bamboo springs?
6- just do it - they're cheap. If you want a large one, look around on the forums to see which ones have been used.

---

### Post by bernied on 2007-01-05
About that security thing there's something called portable vault and something else called U3 - neither sounds very linux friendly to me, especially U3.

---

### Post by meng on 2007-01-05
1. I've not come across a problem with Linux recognizing the drive.
2. FAT32 is the best way to go IMO.
3. I recommend doing this, and in fact I even wait 10 seconds before removing it.
4. Data transfer rates are different for different makes, so if speed is an issue, look for a published lab comparison.
5. Never heard of fake ones, newegg is good if you want to buy online.
6. Don't bother with U3.

---

### Post by Sef on 2007-01-05
Thanks for the replies.   I will get one a few gigabytes.

---

### Post by nix4me on 2007-01-05
Just remember, FAT32 has file size limitation.  2GB i think.  So you wont be able to stuff a 3GB AVI on it.

nix4me

---

### Post by Doug11 on 2007-01-05
I know Sandisk has them out now with their own software built right into them. Unless it says right on the package that it's compatible with Linux,,I would stay away from those ones unless you can try it first.

---

### Post by bodhi.zazen on 2007-01-05
Happy New Year Sef :p

I don't have much to add ...

First I have used several brands of flash drives with Linux without problems. You plug it in and it works ....

Second I would echo the caution regarding U3 . U3 is not Linux compatible and will take up space on the drive. Windows users, however, love U3 because they can encrypt (I tink) data and programs easily...

You can see these sites for information on removing U3:

[http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

[http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)

Third, Most flash drives do not require you to install software onto Windows or Linux in order to use them. What software is this ? I would be careful, of course, if you are talking about drivers as the flash drive may not work on Linux ...  With that said, I use a set of flash drives that install software drivers when I plug them into windows without any problem on Linux (I do not know the manufacturer other then the devices are labeled with "Mobile Disk"). 

As far as overall performance, yes some dirves are better then others. Check the technical specifications as most drives will list the data transfer rates ...

Yes, eject/unmount before you remove the disk both with Windows and Linux. Failure to do so can result in data loss or data corruption. In **rare** cases you can toast the flash device (yes I have seen this on Windows, never Linux).

Last a word about fake flash drives. Oh they are very slick indeed. They look and feel like the real thing down to detailed packaging. I have seen several. The only way to identify them as fake was to run the serial number by the manufacturer.

The best protection against this is to buy from a reputable source in the first place. The only fake drives I have seen were purchased as "new" (complete with packaging) over EBay.

The last piece of advice I can give you is flash devices may have a more limited life span or limited numbers of writes.

Last, file system. You can format these flash devices with vfat, ntfs, ext2/3, jfs, reiserFS, and xfs (and likely more) without any difficulty other then cross OS compatibility.

HTH

---

