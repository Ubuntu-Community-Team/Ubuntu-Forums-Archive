---
title: "Help!! used  rm -rf !(0|constant|system) in home folder instead of desired directory"
date: 2016-10-04
forum: General Help
---

### Post by babakflame on 2016-10-04
Dear Fellows

  I was doing a simulation that used to create lots of files during simulation. So, I was using rm -rf  !(0|constant|system) to delete un necessary files. However, once, I was unaware that I am running this command on home folder. Now, My Desktop folder and some of other folders are gone. I used CTRL+c as soon as I realized I am in the wrong directory. However, I have lost lots of files. Is there any way to at least return Desktop folder  or other files?   :(:(:(:frown:

---

### Post by babakflame on 2016-10-04
I tried ```
sudo apt-get update
```. however, still dont have Desktop Folder

:(:(

---

### Post by Jimysbil on 2016-10-04
If you have photos or other necessary files and you want to give them a chance to get saved STOP immedeatly the use of the specific hard disk.
Boot from USB or CD/DVD and use [COLOR=#ff8c00]testdisk[/COLOR] or [COLOR=#ff8c00]photorec[/COLOR] tool in order to get your files back (or what left from them).
The command [COLOR=#ff8c00]apt-get update[/COLOR] is probably the worst command you could use because if it has download new packages and it has replace files on your system the most possible senario is to have overwrite your deleted files.

---

### Post by ajgreeny on 2016-10-04
You should stop using your OS immediately, boot to a live USB/DVD, and try testdisk and photorec which may be able to find your deleted files.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
The more you use the disk the more likely you are to overwrite the space where the removed files were, which could make them impossible to recover.

Or, of course you could simply restore everything from the backups that you make regularly.
What's that; you don't have backups!  A lesson learned, hopefully not the very hard way with irrecoverable files.

---

### Post by babakflame on 2016-10-04
I didn't make any backups.  So, First I think I am gonna go for live usb of Test disk.

 I stopped the command after some seconds  [CTRL + C]. so , basically I just lost some folders including Desktop and files inside Downsloads.

---

### Post by babakflame on 2016-10-04
I used testDisk software. however, nothing was found.
  Then, I used photorec, a lot of files was found and I assigned the Downloads directory to be put there. Is there any way to recover Desktop in the correct route which is ~/Desktop.

  I really want to have my Desktop back.:(:(

Now,
The desktop shows the contents of home folder i.e. ~.

---

