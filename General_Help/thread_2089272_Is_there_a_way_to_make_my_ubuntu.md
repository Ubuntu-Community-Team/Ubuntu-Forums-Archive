---
title: "Is there a way to make my ubuntu"
date: 2012-11-28
forum: General Help
---

### Post by andreamillspaugh on 2012-11-28
Hi everyone I was wondering if I can make a livecd and install to hard drive. because im changing my computer and formating every thing on hardrive , but I don't what to losss all my files, can this be done I know windows can do that with some software so there hast to be one for linux? thanks:)

---

### Post by d.atanasov on 2012-11-28
Hello, 

So if I understand correctly, you want to install Ubuntu on your hard drive (HD) and not running it from LiveCd, but you don`t want to format the HD. I know that when installing Ubuntu and going through the installation you can choose "Advanced Option"m where you will find that on different partitions you can un-check the boc for formatting. 

hope this help you, 
cheers

---

### Post by westie457 on 2012-11-28
Firstly I suggest you back-up/copy the files you want to keep to another hard drive or or USB drive, or if not very many a few DVDs. 

Formatting a hard drive or partition wipes all files.

Assuming your hard drive has Windows on it you will lose everything because Linux OSes do not install to NTFS partitions.

Now the bad news has been delivered there are somethings that can be done to keep your files on the drive however you will have to do some work. Explain a bit better what you want to do and we can offer better advice.

---

### Post by andreamillspaugh on 2012-11-28
Hi, I dont have windows on my computers the only operating system I have is Ubuntu, its just i dont have a nother hardrive to copy everthing over to or anything, and these files i realy need, so theres no way at all that I can make my Ubuntu on dvd with my files and I want it to be livecd and beable to insall on hardrive that way I cant loos any thing and then if I trver some where All i have to do is insert the dvd and it boots up with my program still on there,

---

### Post by SeijiSensei on 2012-11-28
Go spend $10 and buy a [USB pendrive]("http://www.amazon.com/SanDisk-Cruzer-Flash-Drive-SDCZ33-016G-B35/dp/B005FYNSZA/").  These days I even see them for sale in drugstores.

---

### Post by MythosLegend on 2012-11-28
Like westie457 siad, there are more advanced options when installing ubuntu. Those options include resizing partitions. This could allow you to make another partition if you have enough space. Then you could install another OS on the new partition.

This leaves a lot of old system files. (That's why I have my own home partition for cases like this.)

---

### Post by markMDW on 2012-11-28
Okay, I'm reading this and figuring that you are upgrading your computer hardware and reformatting your harddrive.   But, you don't want to erase your data, programs or configuration--therefore you want to create a Live CD of "your personalized system" to install to your new hardware, and your reformatted harddrive, rather than installing from scratch, default settings empty Ubuntu.. AND you want your data, of course.

I think the answer is that YES, there is a way to do such a thing, but I understand it's not a simple process.   The tool you need is available from the Ubuntu Software Center, called:
**Ubuntu Customization Kit**



The simplist way though,  would be to just download a Ubuntu backup utility from the Ubuntu Software Center.  You backup your system then restore to your new reformatted drive.  These solutions should be much simpler, available from the software center :

Simple Backup Restore
Simple Backup Config

AND, last but not least, this one might be the one you want to experiment with:
**APTonCD**

> "**What is APTonCD?** 			 APTonCD is a tool with a graphical interface which allows you to  create one or more CDs or DVDs (you choose the type of media) with all  of the packages you've downloaded via APT-GET or APTITUDE, creating a  removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of  your .deb packages located in one especific repository, so that you can  install them into your computers without the need for an internet  conection. 
  			**With APTonCD you be able to...**

 				BackupBackup all downloaded packages (via apt-get, aptitude and synaptic) to restore later.TransportTake with you all your favorite packages, in a removable repository where you can install then all on anytime, anytime.DownloadGet an entire repository, or a specifc section. Simply  point-and-click, and in few time you'll have an CD(s) or DVD(s) with  entire main, restricted, universe, multiverse, contrib, etc.ShareShare your packages with your friends without Internet  conection. Also, send a meta-package for him to install the same set of  packages that you have.    " 

---

### Post by elliotn on 2012-11-28
backup your data in a USB or DVDs then use use Remastersys to clone your install to a LiveDvd then install to the new machine and restore your data

---

### Post by andreamillspaugh on 2012-11-29
thanks everyone for your help im going to try that now.:)

---

### Post by Bucky Ball on 2012-11-29
Remember, a DVD will only hold about 4Gb so your personal files will probably amount to more than that. 

You are really trying to do two things here as I understand it; back up your actual install so you keep the same programs/apps/setup, and backup your personal data which you will need to do to a USB dongle or other external media. 

Remastersys will create a distributable, LiveCD of your install exactly, retaining all programs/apps. Sounds like what you are after. From the [Remastersys Site]("http://www.geekconnection.org/remastersys/"):

> 1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.

---

### Post by markMDW on 2012-11-30
the link to the remastersys site isn't working for me, are you sure it's correct?

---

### Post by howefield on 2012-11-30
> **markMDW said:**
> the link to the remastersys site isn't working for me, are you sure it's correct?

Try it again.

---

