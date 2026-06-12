---
title: "Data recovery (I hope)"
date: 2008-06-13
forum: General Help
---

### Post by TheAJKMan on 2008-06-13
Okay, in [this thread]("http://ubuntuforums.org/showthread.php?t=827902") I described how I rebooted my machine and got GRUB errors 17 and 21. I have a working installation again and am hoping to recover the data that is on my 80gig hdd. I followed the various recommendations given in that topic, including the link provided to another thread that dealt with a related issue. I've had no luck thusfar. 

Essentially what happened was this, I installed 7.10 on the 40gig hdd. I later slaved the 80gig drive to it. I upgraded to 8.04 and had it install on the 80gig hdd. Today I noticed my system suddenly get unresponsive, Jukebox suddenly started greying out a few times, my browser started getting sluggish and I thought I'd just reboot the system. Upon reboot I got a GRUB error 17. I tried booting up off each hdd individually. I tried slaving each to the other, making each master and the other the slave. I made sure that the jumpers were adjusted accordingly. I kept getting GRUB error 17 or 21. Eventually I just reinstalled 8.04 on the 40gig hdd. The data I'm hoping to recover is on the 80gig hdd and consists of spreadsheets, assorted video clips, pics and wallpapers as well as a few hundred emails. If possible I'd like to recover it all, but if it isn't possible I can scrub that drive and just reformat.

AS I said, recovery is preferential. Hoping somebody can help me, I'm getting desperate now. Desperate enough to consider going back to Windows even. :(

Thanks in advance.
TheAJKMan

---

### Post by Deadheded on 2008-06-13
It sounds like the 80gig HD has gone bad.  If that is the problem you may never get anything off of it.  If the drive is good you should be able to just mount the drive.  If the info on that drive is that important you might try and see if you can download a copy of Hiren's Boot CD which has some tools that may help you recover the drive.

GLTY

---

### Post by pytheas22 on 2008-06-13
Photorec is a useful utility for recovering lost files by searching for remnants of their file headers, even if you can't mount the drive.  As long as you haven't written any more data to the 80 gigabyte drive since it crashed, photorec should be able to get most of your files back.  You can install it with:

```
sudo apt-get install testdisk

```

(it's packaged with testdisk, a partition-table recovery utility)

and run it with:
```

sudo photorec
```

---

### Post by TheAJKMan on 2008-06-13
Deadheded, I had considered that possibility, but both the hdd gave the GRUB errors, either individually or whether they were made master or slaved. 

pytheas22, thank you, you're suggestion seems to be working quite well, busy with it as I'm typing this out. WIll post results as soon as it finishes.

---

### Post by jimv on 2008-06-13
You might consider getting an IDE/SATA to USB adapter.  I can't tell you how handy these things come in when you have dead/dying harddrives.

---

### Post by TheAJKMan on 2008-06-13
jimv, would you be able to provide either a pic or link so that I can see what that looks like. It would make it easier to locate in my country as I'm pretty sure I'll be getting plenty of blank stares if I ask for it. Take for example my ISP, only one guy on the tech support desk can help anyone with a linux related problem connecting via them. And he's not always there. Lot of people working in the computer shops here aren't always as clued up as you'd need them to be, unfortunately.

---

### Post by TheAJKMan on 2008-06-13
Never mind, I jfgi and am considering bank robbing as a new hobby. Damn those things are expensive in this country. WIll shop around now that I have some idea of what it looks like.

---

### Post by Deadheded on 2008-06-13
> **TheAJKMan said:**
> Deadheded, I had considered that possibility, but both the hdd gave the GRUB errors, either individually or whether they were made master or slaved. 

pytheas22, thank you, you're suggestion seems to be working quite well, busy with it as I'm typing this out. WIll post results as soon as it finishes.

The Grub error does not mean you HD is not bad, it means that Grub can not see one of the HD's.  I had Grub 21 errors when I removed one of my IDE HD's even though it was just a storage drive using FAT32

---

### Post by TheAJKMan on 2008-06-13
What puzzles me is why it would suddenly not see both hdd when just seconds before I had been using both of them. All I had done was to reboot the system.

---

### Post by TheAJKMan on 2008-06-13
Okay, the recovery process is finally over. It seems as though it has recovered a fair bit of stuff and put it in this directory...... /home/theajkman/recup_dir.XXX Where XXX is the number of each particular directory. THere being 619 of them apparently. The problem however now is that when I try to go into each directory, I get this message ......"**The Folder contents could not be displayed.      You do not have the permissions necessary to view the contents of "recup_dir.xxx**""

Great, now what do I do to set it up so that I can give myself those permissions and see what exactly has been rescued :)

---

### Post by pytheas22 on 2008-06-13
You get that message because, since photoshop was run as root, only root has access to the files it wrote.  Type:
```

sudo nautilus /home/theajkman/
```

and you should be able to view the files.  Or you can use chown or chmod to change their permissions so that you could see them as a normal user too.

---

### Post by TheAJKMan on 2008-06-13
I'm busy going through the directories now and am finding whole chuncks of stuff, most of which is useless to me. .txt files, mp3's from games that I had installed under windows still. Thanks guys.

---

### Post by drs305 on 2008-06-13
To take ownership of the files:
```
sudo chown -R **username:username** /home/theajkman/
```

Glad to see you are getting some of it back :)

---

### Post by pytheas22 on 2008-06-14
> am finding whole chuncks of stuff, most of which is useless to me

FYI before you start the scan, you can tell photorec which kinds of files to look for (by default it looks for everything) so you can exclude any file types that you don't care about.

I hope you're able to recover everything you need.

---

### Post by TheAJKMan on 2008-06-14
That is good to know, though, by the time you'd posted your reply I was already underway with the recovery and, as said, recovered whole chucks of stuff that is useless to me. What looks to bits of code, either from games, webpages or even linux. I've found hundreds of mp3 from previous installations of age of empires games that I had when that disk was still being used as a windows disk.

So far though, nothing that I can use. Have gone through roughly 1/6th the "directories" it recovered and deleted the ones I've gone through. Now all I have to find out is how to get that drive fixed up and in working order again. *sigh*

---

### Post by pytheas22 on 2008-06-14
> That is good to know, though, by the time you'd posted your reply I was already underway with the recovery

Keep in mind that you can always just start a new scan using the options you want.  There's no limit on how many scans you can perform.

Also if you don't believe that the drive was physically damaged but that it's just a file system problem (as I think you said), you can use testdisk to see if it might be able to fix the errors.  It depends on where they are--testdisk is meant for fixing problems with boot sectors and partition tables--but if that's what went wrong, it could help.

---

### Post by greco8523 on 2008-06-18
SOrry bit late but this website could of helped you, but I'll post it to help others in the future: 

[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

---

