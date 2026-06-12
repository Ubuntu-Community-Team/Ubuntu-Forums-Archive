---
title: "I removed my video card and now my ubuntu is stuck at a flashing login screen! Help!"
date: 2013-05-29
forum: General Help
---

### Post by thydeus on 2013-05-29
I'm using a dual boot computer with windows and ubuntu. 

Recently my computer has been blue screening and it seems to be caused by my video card so I removed it and it stopped the blue screen of death. 

However when I boot up my ubuntu, it doesn't go to the ubuntu desktop but a black screen asking for my login and then password.

I can't type my login and password to it because its lagging and it's not typing my inputs correctly also the texts on the screen keeps flashing black and white.

What could've caused this and how do I fix it? :o

Any help would be greatly appreciated. 

Thanks!

---

### Post by thydeus on 2013-05-29
I'm using Ubuntu 9.10 (Karmic Koala) btw!

---

### Post by ibjsb4 on 2013-05-29
And you want support on something that reached end of life two years ago?  Time for a fresh install :)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by thydeus on 2013-05-29
> **ibjsb4 said:**
> And you want support on something that reached end of life two years ago?  Time for a fresh install :)

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Thanks!

I want to reformat my dinosaur age ubuntu partition with the  latest version. However my (really really important) passwords are  stored on there so I need to fix this without wiping out the partition.

It  would be awesome, if anyone knows a way to fix this without deleting my  data and then maybe updating it to the latest version without losing  data?

---

### Post by ibjsb4 on 2013-05-29
How did you store these passwords?  Did you use some sort of program.  I ask because it may be possible to retrieve the file using the install CD (Ubuntu live CD).  Also what are your computer specs?  The new ubuntu takes a lot more resources these days, you may need to go to Xubuntu or Lubuntu. This is my last post till this evening, just letting you know I haven't gave up, just wont be around :)

---

### Post by grahammechanical on 2013-05-29
May I suggest that you try booting into Recovery Mode and then using Failsafex? Without a video card you should expect a very different user experience. You will be back in text mode.

---

### Post by thydeus on 2013-05-29
> **ibjsb4 said:**
> How did you store these passwords?  Did you use some sort of program.  I ask because it may be possible to retrieve the file using the install CD (Ubuntu live CD).  Also what are your computer specs?  The new ubuntu takes a lot more resources these days, you may need to go to Xubuntu or Lubuntu. This is my last post till this evening, just letting you know I haven't gave up, just wont be around :)

Yes, I use KeepassX to store my passwords. :(

I also want to save a couple of files on there if it's possible.

Specs:
E7400 2.8ghz C2D - CPU
Gigabyte GA-G31M-ES2L - Motherboard
9800GTX - (Fried) Video Card - (I'm using onboard video at the moment.)
2GB - Corsair Dual XMS2
1.5 TB - HD
500w - CoolerMaster PSU

---

### Post by thydeus on 2013-05-29
> **grahammechanical said:**
> May I suggest that you try booting into Recovery Mode and then using Failsafex? Without a video card you should expect a very different user experience. You will be back in text mode.

Thanks.

I tried recovery mode and it just went back to the same flickering/lagging login screen after a reboot.

What is Failsafex?

---

### Post by coldraven on 2013-05-29
Why not put the card back in, do a backup, get your data and then think about a fresh install?

---

### Post by thydeus on 2013-05-29
> **coldraven said:**
> Why not put the card back in, do a backup, get your data and then think about a fresh install?

Thanks.

That was actually the first thing I tried to do to recover my data (I have a 1TB external HD) but unfortunately, I could only go to the ubuntu loading screen before it suddenly turns off and dies.

---

### Post by Mark Phelps on 2013-05-29
Yo are able to install apps when running from a LiveCD or LiveUSB, it just installs them to a RAMDisk, and when you restart, they are gone.

IF you can get to a desktop this way, and install the app you need, you might then be able to recovery the data.

---

### Post by thydeus on 2013-05-29
> **Mark Phelps said:**
> Yo are able to install apps when running from a LiveCD or LiveUSB, it just installs them to a RAMDisk, and when you restart, they are gone.

IF you can get to a desktop this way, and install the app you need, you might then be able to recovery the data.

Thanks. 

What application are you talking about?

---

### Post by thydeus on 2013-05-30
Bump.

---

### Post by Irihapeti on 2013-05-30
Any chance of removing the hard drive, putting it in an enclosure and plugging it into another computer? You could get your data off that way.

---

### Post by thydeus on 2013-05-30
> **Irihapeti said:**
> Any chance of removing the hard drive, putting it in an enclosure and plugging it into another computer? You could get your data off that way.

Thanks.

I don't have a hard drive enclosure. 

I do have 2 hard drives in my computer, drive C: & D: and both Ubuntu and Windows are stored in drive C:

Will I be able to get my files and data from the Ubuntu on drive C: if I install another Ubuntu on drive D: ?

---

### Post by Irihapeti on 2013-05-30
If you can get something to boot so that the screen is readable, then you should be able to mount the drive and just copy the important files off.

It doesn't have to be Ubuntu. In fact, it might be worth your while getting something like Parted Magic, which is a rescue distro. They have versions for 64 bit, 32 bit and also an i568 version for older computers. See [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads) The downloads are less than half the size of an Ubuntu iso.

---

### Post by thydeus on 2013-05-30
> **Irihapeti said:**
> If you can get something to boot so that the screen is readable, then you should be able to mount the drive and just copy the important files off.

It doesn't have to be Ubuntu. In fact, it might be worth your while getting something like Parted Magic, which is a rescue distro. They have versions for 64 bit, 32 bit and also an i568 version for older computers. See [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads) The downloads are less than half the size of an Ubuntu iso.


Thanks! 

I'm downloading Parted Magic right now, it should be done in a couple of mins.

Is it okay if I boot Parted Magic with Unetbootin? and will I still be able to copy my files on Ubuntu that way?

---

### Post by pqwoerituytrueiwoq on 2013-05-30
that will be fine, what was your old video card (nvidia, amd, or ati)
and what is your current one (intel, nvidia, amd, or ati)
you probably just have to delete [FONT=courier new]/etc/X11/xorg.conf[/FONT] and uninstall a driver to get your old install to boot properly

---

### Post by Irihapeti on 2013-05-30
If you're going to delete /etc/X11/xorg.conf, also look out for a file called /etc/X11/xorg.conf.failsafe If it's there, delete it as well, or you may end up wondering why deleting your xorg.conf has changed nothing.

I once spent several days tearing my hair before I figured that out. :confused:

---

### Post by thydeus on 2013-05-31
I'm getting this error when I try to boot up Parted Magic.[B] 

Kernel panic - not syncing: Attempted to kill init!  [/B]

---

### Post by Irihapeti on 2013-05-31
I take it that you're using a version that is suitable for your computer. I don't know enough about hardware to tell if your machine is 32 or 64 bit, or how old it is.

You could try booting with some of the other boot options. There are several of them. I think you have to go to another menu screen from the first one.

---

### Post by thydeus on 2013-05-31
> **pqwoerituytrueiwoq said:**
> that will be fine, what was your old video card (nvidia, amd, or ati)
and what is your current one (intel, nvidia, amd, or ati)
you probably just have to delete [FONT=courier new]/etc/X11/xorg.conf[/FONT] and uninstall a driver to get your old install to boot properly

Thanks.

My old video card is Nvidia and I'm currently using my motherboard's onboard video.

How do I uninstall my Nvidia drivers if I don't have access to the terminal?

---

### Post by thydeus on 2013-05-31
> **Irihapeti said:**
> I take it that you're using a version that is suitable for your computer. I don't know enough about hardware to tell if your machine is 32 or 64 bit, or how old it is.

You could try booting with some of the other boot options. There are several of them. I think you have to go to another menu screen from the first one.

Okay! I think I'm going to try Linux mint. 

I hope I don't get the same error cause that would mean I have a hardware problem or maybe it's because of GRUB? When I boot my computer I get the GRUB menu first and then the Windows or Unetbootin menu. 

I'll try to boot up Linux mint and see what happens.

---

### Post by Irihapeti on 2013-05-31
Ah! You've reminded me that there has been some funny stuff with the unetbootin menu, at least in the past. But it's too long since I had that problem, so I don't remember the details. I do know that it behaved much better on a CD.

It pretty much doesn't matter what distro you use, as long as you can get into your system and copy or change things.

And you still have the option of taking the drive out. My son's old laptop died completely &#8211; I'm talking about seriously dead motherboard here &#8211; and I got the files off by removing the drive and mounting it on my own PC.

---

### Post by thydeus on 2013-05-31
[SIZE=7]**SOLVED!**[/SIZE]

I got my data back and I have also kinda fixed my Ubuntu! *(The folders buttons aren't responding and I can't move or close it but I was able to backup my data so all is good!)* :)

Installing Linux Mint didn't work, I also tried Puppy Linux and that didn't worked either. What I did was delete the [FONT=courier new]/etc/X11/xorg.conf and Nvidia drivers[/FONT] by accessing root shell in recovery mode. 

The commands that I use were:

> mount -n -o remount,rw /
apt-get purge nvidia-current
rm /etc/X11/xorg.conf
reboot now

Thank you all for all the help and suggestions!

---

### Post by Irihapeti on 2013-05-31
Great! I get a huge buzz out of seeing a problem solved.

Now can you mark the thread solved?

---

