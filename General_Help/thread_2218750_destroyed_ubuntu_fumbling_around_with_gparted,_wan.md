---
title: "destroyed ubuntu fumbling around with gparted, want to reinstall w/o destroying win7"
date: 2014-04-21
forum: General Help
---

### Post by arnicainthemembrane on 2014-04-21
Hi, I completely mangled the ubuntu partitions fumbling around with gparted, and now i'd like to do a reinstall without touching the win7 partition, as I have crucial documents and programs there. 

Any advice?

---

### Post by sammiev on 2014-04-21
Backup all your data and maybe your full OS first and then post a image screen of gparted.

---

### Post by ibjsb4 on 2014-04-21
Yes, get backup in place.  You can mangled the whole HDD with gparted without even trying hard :)

I beleive the ubuntu live DVD has the option to install on top of the existing install.  Provided the installer can still recognise the current install.

If it cannot, then you could manually delete the ubuntu partitions (just turn it into free space) and reinstall.

I believe thats the way the live installer works, haven't used it in a long while.

---

### Post by yamabushi336 on 2014-04-21
> **ibjsb4 said:**
> Yes, get backup in place.  You can mangled the whole HDD with gparted without even trying hard :)

I beleive the ubuntu live DVD has the option to install on top of the existing install.  Provided the installer can still recognise the current install.

If it cannot, then you could manually delete the ubuntu partitions (just turn it into free space) and reinstall.

I believe thats the way the live installer works, haven't used it in a long while.

Yes do back up of your system as lbjs has said and then just go through the process as normal and it will give you the option to reinstall. I had to do this couple of times on later versions of ubuntu.

---

### Post by Mark Phelps on 2014-04-21
I would advise AGAINST reinstalling Ubuntu, as folks have been reporting here that doing so, in some cases, has resulted in erasing the entire contents of their drives, including the former Windows installation there.  Apparently, in some cases, reinstall is treated the same as Use Entire Disk -- resulting in reformatting of the disk.

You should us the free version of Macrium Reflect in Windows to do an image backup of your Windows partition(s) before attempting a reinstall.

---

### Post by arnicainthemembrane on 2014-04-22
On top of figuring out a scheme to re install Ubuntu (as a fully partitioned and fully accessible OS) I'd like to figure out how to access files which are on my HD but not accessible cause I'm not sudo on the thumb drive OS... any advice on that front? Or should I give up on it and wipe everything out then reinstall?

---

### Post by arnicainthemembrane on 2014-04-22
gparted screenshot. pardon the manglement...

---

### Post by sammiev on 2014-04-22
I would boot from a live DVD/USB and just keep your NTS partitions. I would delete the rest and let the installation DVD/USB on a fresh boot handle the installation from there. It's a little bit of a mess how it stands now.

---

### Post by arnicainthemembrane on 2014-04-23
I'm happy to reinstall but i don't want to "lose" win7 cause I'm not it's licenced user (I bought the computer used with w7 packaged) and I need various win dependent programs for work. Thus far I haven't heard of any useable "hacked" versions of w7. So i can back up all the data, but wouldn't be able to replace the OS. And I'm not gonna buy a new one! 

When I look for advice online I'm given a series of procedures intended to prevent issues with windows when booting into a dual partitioned system. . .  what are the dangers of doing a fresh install while leaving the w7 partitions intact? 

Also, is there some way I could simply use the usb thumbdrive linux as an OS, but consolidate the rest of the free space with gparted and use it as a backup storage drive?  Just a thought. . . . 

thanks

---

### Post by sammiev on 2014-04-23
Your in the wrong place with a hack version of Win7. You will find little help here doing that.

---

### Post by arnicainthemembrane on 2014-05-05
I don't have and I'm not looking for a hacked version of Win 7. For my work I need to have a Windows OS on my computer as there aren't Ubuntu versions of the majority of the programs I use at work. All i was tryin to say is, I'd like to figure out how to reinstall Ubuntu so i can continue to use it when I'm not using Windows. And I'm not gonna go out and buy a new Windows OS if I should happen to destroy it in the repartitioning process cause I don't want to support them financially if I can avoid it. In eight years of coming to this forum for advice this is the first time I've been told that I can't get any help here, what gives?

---

### Post by sammiev on 2014-05-05
> **arnicainthemembrane said:**
> I don't have and I'm not looking for a hacked version of Win 7. For my work I need to have a Windows OS on my computer as there aren't Ubuntu versions of the majority of the programs I use at work. All i was tryin to say is, I'd like to figure out how to reinstall Ubuntu so i can continue to use it when I'm not using Windows. And I'm not gonna go out and buy a new Windows OS if I should happen to destroy it in the repartitioning process cause I don't want to support them financially if I can avoid it. In eight years of coming to this forum for advice this is the first time I've been told that I can't get any help here, what gives?

That is not allowed here.

---

### Post by QIII on 2014-05-05
*Thread reopened after closer reading.*

If I understand that you are trying to figure out how deal with a messed up Windows 7 installation after having attempted to install Ubuntu, then Mark Phelp's suggestion may be your best bet for that.  If your Windows came pre-installed from the factory, then it is ***probably *** legal***.***  You can confirm this by the holographic sticker on the case.  If there isn't one, then the legality of the installation is dubious -- but not necessarily illegal.  In that case, we can make no judgment beyond your word.

However, if it has been destroyed and you do not have install media, then you will be obliged to purchase a new copy.  That is just how it is, unfortunately.

If this thread has gone seriously off track and you never intended to suggest that you were planning to hack or break Microsoft's EULA, please post such immediately and make your intent clear.

---

