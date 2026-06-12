---
title: "Windows XP dual boot won't load setup.."
date: 2008-01-11
forum: General Help
---

### Post by IOA on 2008-01-11
Well, I tried dual booting Windows XP with ubuntu. I had previously had Windows Vista, but about 2 months ago switched to Ubuntu. I decided that I needed at least XP to run my games, so a few hours ago I partitioned my hard drive. Now I have a 180 gig Linux drive and a 110 gig FAT32 formatted drive for Xp to go on. I went to go put in my Windows XP disk. I went into the boot screen in my BIOS, and I chose the CD. Instead of booting the Windows XP setup, it just brought me to the normal Ubuntu login screen. 

Also, I am using an original disk, NOT a copy. Help is much appreciated.


Thanks in advance.

-IOA

---

### Post by IOA on 2008-01-11
Bump...

Can someone please help me? I'm really dying to use XP and Ubuntu in a dual boot.

---

### Post by jken146 on 2008-01-11
If I remember correctly the XP install CD asks you to press any key to begin the installation, otherwise it boots from the 1st hard disk.  You get about 5 seconds to do this I think.

---

### Post by IOA on 2008-01-11
Okay, I'll try that.

---

### Post by IOA on 2008-01-11
Okay, I put in the disk and booted up again. Once I booted off the CD, it ran just like I had restarted Ubuntu. It said the whole "Verifying DMI Pool Data" And then "Booting From CD"

But after that, it ran just like it was running Ubuntu.

Is there something I need to do or some sort of program to boot this up?

---

### Post by IOA on 2008-01-11
Bump again.

I did a bit of googling and found nothing.

Does ANYONE have an idea on how this would work?!

---

### Post by Sef on 2008-01-11
Please don't bump more than once every 24 hours.  More can get you an infraction.

Let's check your partitions:

Applications > Accessories > Terminal

then type this code:

```
sudo fdisk -l
```  (Small L)

---

### Post by IOA on 2008-01-11
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23809   191245761   83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda3           23810       38156   115242277+   b  W95 FAT32
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris
```


That's what it said.

Sorry about the bumping, I was just really anxious to get this Windows XP working. The issue is not the partitions, they're formatted correctly. The issue is getting the Windows XP Setup working. It's not booting off the disk, it's booting off of my hard drive even when I select the disk.

~EDIT~

OHHH, was I supposed to have the FAT32 one start at 1?

---

### Post by RedPandaFox on 2008-01-11
So are you trying to run Ubuntu then install XP? Because Windows dosnt like being the second boot. I had lots of problems trying to install XP on my system after Linux and it didn't work, I had to wipe my two HDD's and start again by running windows then Linux. Its a bit extreme I know but thats the only way I found I could duel boot windows and anything else

---

### Post by IOA on 2008-01-11
Alright. What directories should I back up though, besides Documents and Pictures? I have tons of CDs left, it's just that I don't want to waste them.

---

### Post by strabes on 2008-01-11
> **IOA said:**
> Alright. What directories should I back up though, besides Documents and Pictures? I have tons of CDs left, it's just that I don't want to waste them.

Although a pain in the butt, it's possible to install windows after ubuntu. You'll just have to [reinstall grub](http://www.sorgonet.com/linux/grubrestore/) after installing XP. I don't understand what you're asking. Just back up everything you normally do like you data and important files.

---

### Post by IOA on 2008-01-11
I was asking for help. For some reason, Windows disks are not being booted off of when I tell them to be. I went into my boot device manager and set CDROM to the first priority with the Windows XP disk in there. Then, I even went into a boot loader and booted the CDROM. Instead of booting it, it goes directly to the Ubuntu splash screen and starts Ubuntu normally.

~EDIT~

OHH, yeah, I missed the point of your post there. You were talking about what I should back up, why I was asking you.

I heard there was a directory of debs that I could backup onto a CD and just run them again to reinstall all my stuff.

---

### Post by strabes on 2008-01-11
> **IOA said:**
> I heard there was a directory of debs that I could backup onto a CD and just run them again to reinstall all my stuff.

I've never heard of such a directory, but what I have is a file in my documents folder that has a list of all the things that I do after a fresh install. It contains bug workarounds, package installs, etc. One of its lines is the following:```
sudo aptitude update && sudo aptitude dist-upgrade -y && sudo aptitude install -y w32codecs ubuntu-restricted-extras vlc lostirc easytag gtkpod gnomebaker soundconverter lame libdvdcss2 gnome-vfs-obexftp audacity kdebase amarok
```

So it just updates the system and installs everything I need. You could just make a list of all the packages you installed and compile them into a command like I have done.

Regarding your windows CD booting problem, I have no idea. Does an ubuntu live CD boot? Good luck.

---

### Post by RedPandaFox on 2008-01-12
I generally don't worry backing up my files basically because I don't have anything really important. Every 6 months I just wipe it all and start from scratch to get rid of any clutter from random junk but thats just me. 
Most stuff you will probably have you can get again if you need it besides important files etc but if you have done anything to your OS such as edit you Xorg etc take a copy of that? And I'm unsure as to how bout if you can save your updates that would save some bandwidth when you reload it all, but as I say, I'm not sure as to how you could do so, or if possible.

---

### Post by boyofford on 2008-01-12
just to clarify, you can't get your system to boot from cd/dvd at all? even with a say a ubuntu livecd?

---

### Post by IOA on 2008-01-12
No. I can boot anything BUT a windows CD. I've booted the Ubuntu Live CD numerous times. When I tried booting up Windows XP, it just went right to Ubuntu. It said it was booting from the CD, too, which was weird. I'll try to videotape it sometime when I find my memory card.

---

### Post by RedPandaFox on 2008-01-12
I have had a look around, it sounds like you have the same problem as I did but as of yet I still cant find a solution, I guess windows doesn't like being second to anyone.
No one I know can offer any other suggestion but to wipe Ubuntu and load windows then Ubuntu again.
When I had this problem I even tried wiping one HDD (I have duel HDD) and loading windows on one and Ubuntu on the other then reload the GRUB but that didn't help either. 
I am really interested in knowing if there is another way because I need to reload my windows but I don't want to have to dump all my stuff right now.

---

### Post by IOA on 2008-01-13
Okay, I'll do that then :\.

But if XP still fails to load up anyway, I'll just re-install Ubuntu too. I'm currently in the process of backing up my data. 

Thanks for the help anyway.

---

### Post by IOA on 2008-01-20
Sorry for this huge bump, but I finished backing up my files. I went into the Partition Editor on LiveCD and formatted it to Fat32, not deleted, but just formatted. There's still a 110 gig EXT3 Linux thing hanging around there. And now Windows XP disk STILL isn't booting up. Do I seriously need to wipe everything clean, including the recovery drives?

---

### Post by RedPandaFox on 2008-01-28
Why not just save your recovery files to a disk or something? I think windows just likes being second to none.

---

