---
title: "Can you convert a 64 bit version to a 32 bit version without re-install?"
date: 2013-09-10
forum: General Help
---

### Post by jesus-freak on 2013-09-10
I downloaded Ubuntu 13.04 64 bit for my computer and then when I went to install it on my wife's laptop I used the same install disc and forgot to check if her system could handle it. Well, after installing I noticed that while her computer does run it, it runs it quite slowly. So then after checking I found that her system is a 32 bit system and so I expect that is why it doesn't run so great. Now, here is my problem. Normally I would have just downloaded and burnt the correct install disc again and re-installed it, but her DVD drive died and there is no option in the bios to boot from any USB devices. So is there a way to switch from the 64 bit version to the 32 bit version without re-installing the whole thing? I don't have the money right now to buy a new DVD drive so any helpful suggestions that will help me out in the meantime would be appreciated!

---

### Post by brick2 on 2013-09-10
I do not know how to do this but it is not complicated at all, browse the net a litle bit and find a how to plenty of them out there.

Install it from your or another computer to hers. Or at least I think this could work.

Also something which I really have not tested but in teory it sounds like it could work, take out the drive fro myour wifes laptop put it in a external storage container plug it in another compuer and do the work there (I have not tested this and it might sound like something increadbly stupid thing to do but have some some simillar things like this all though I am unsure about the installation.

Hope it heaps.

---

### Post by jesus-freak on 2013-09-10
Could this be an option? [http://www.wikihow.com/Install-Linux-without-a-CD-or-USB-Stick-Using-UNetBootIn](http://www.wikihow.com/Install-Linux-without-a-CD-or-USB-Stick-Using-UNetBootIn) Install it to the hard drive using this and then once finished I assume that you would have two OS's on your computer since you installed one from within another. Then maybe just delete the original OS?


Or is there a way of actually using the installation that I already have and just changing the 64bit aspects of the OS to 32bit? I can't  seem to find anything about how to do this but most people I ask seem to think it's very possible.

---

### Post by The Spectre on 2013-09-10
Your wife's Laptop must be 64 bit otherwise the 64 bit version of Ubuntu would not have been able to be installed at all in the first place.

I suspect that your wife's Laptop would run the 32 bit version just as slow.

What are the Specs on that Laptop?

---

### Post by jesus-freak on 2013-09-10
Well I know it originally ran Vista 32bit so I assumed that it was 32 bit or maybe just a early 64 bit that can't handle modern 64 bit OS. Here are the details of her laptop.

[http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html](http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html)

---

### Post by The Spectre on 2013-09-10
> **jesus-freak said:**
> Well I know it originally ran Vista 32bit so I assumed that it was 32 bit or maybe just a early 64 bit that can't handle modern 64 bit OS. Here are the details of her laptop.

[http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html](http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html)
Her Laptop should be able to run it fine, I am running Ubuntu 13.04 64 bit on an even lesser Laptop with only 2 GB of RAM.

After installing Ubuntu 13.04 64 bit did you install _All_ of the Updates for Ubuntu?

If you haven't I would recommend doing that first before trying anything else.

I have installed Ubuntu on a couple of Systems and was running sluggish or flaky until after all the updates where installed.

---

### Post by jesus-freak on 2013-09-10
Maybe it should run it okay but it doesn't run it okay at all. Yes, it has been updated. She has had it for 6 months now and it's been updated regularly but still runs like junk.

---

### Post by ajgreeny on 2013-09-10
As The Spectre says, the machine is a 64 bit machine, but I suspect that the laptop in question does not have a graphic card (ATI mobility) that will run unity very well, and that this is the root of your problem.

One option is to use a different variety of the ubuntu family and add the **xubuntu-desktop** package which will then give the option of booting into a **xubuntu** session at login. This is much more likely to run successfully on that hardware.

If this is the case, and you want to remove unity and all the various gnome packages and libraries it can be done by following the details at [http://www.psychocats.net/ubuntucat/tag/pure-xubuntu/](http://www.psychocats.net/ubuntucat/tag/pure-xubuntu/) but you may find that the added gnome packages are useful, so if space is not a problem you can keep them; they will not slow the computer down as they will only run if you physically start them yourself.

---

### Post by jesus-freak on 2013-09-10
Yeah, I'm sure the graphics card isn't doing very well because in recent days when she starts her computer all she gets is a black screen, you can't see the option to go into bios and then you can't see the options when grub  loads up. We just wait for about 15 seconds when the grub screen would normally be up and then we press enter. Then it will start. So it's like doing it blind from the time you start up until you press enter.

---

### Post by Mark Phelps on 2013-09-10
Unfortunately, that Mobility Radeon x1250 is a very old chipset -- one for which AMD dropped restricted driver support years ago.

If the performance problem is that the desktop experience "lags", there is really nothing much you can do in terms of video drivers.  You could try using a less-graphics-demanding desktop like Xubuntu, or a lighter distro like Lubuntu.  Both of those would have snappier response than struggling with Unity.

---

### Post by coldraven on 2013-09-10
I have the same specs on my HP laptop except I have 4GB of memory.
I'm running 12.10, Unity is a little sluggish but quite usable with most effects switched off. (Experience: Standard it says in "Details")
It boots up fast and resumes from Suspend in a few seconds.
Try installing the Xubuntu desktop and select that at login.

---

### Post by jesus-freak on 2013-09-10
I see. I never even thought of that because you hear all the time about people installing Linux on old systems to give them new life, even 90s computers so I thought a computer from 2008 would be no problem. And also it was sold with the bloated graphics hog of Windows vista so I would never have thought that it couldn't run Ubuntu. Anyway, You mentioned being able to install Xubuntu by downloading and adding it to your ubuntu and then being able to delete the Unity and only use Xubuntu. Is this also the case with Lubuntu? When I seached for Xubuntu in Synaptic I see one called Xubuntu-Desktop, is that it? And when I search for Lubuntu I see Lubuntu-Desktop and also Lubuntu-core. I'm kind of leaning towards the lighter distro to insure that it will run good. But will both Lubuntu and Xubuntu run skype and libre office? These are 100% needed for her work. Oh, and far as my start up problem, do you think this would be fixed if I changed to one of these other OS's? Like I said when I start the computer it is a black screen. I don't see the screen to select the bios, I don't see the grub screen, nothing. I just have to wait for about 15 seconds and press enter when I think the grub screen is up to start Ubuntu and then from that point on it's fine.

The black screen thing just started happening about a week ago after having Ubuntu on her computer for at least 4 months now.

---

### Post by TenPlus1 on 2013-09-10
Both Xubuntu and Lubuntu (which I use) will run Libreoffice and Skype no problem although skype seems to be 32-bit only on linux at the moment but will still run by installing 32-bit compatibility libraries... 

[http://ubuntuforums.org/showthread.php?t=2139202](http://ubuntuforums.org/showthread.php?t=2139202)
[http://www.dedoimedo.com/computers/ubuntu-ringtail-skype.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-skype.html)

---

### Post by jesus-freak on 2013-09-11
Okay, I have a question. Since the computer in question has no DVD rom drive to do a clean install of a more suitable OS, Can I take the hard drive out of this[http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html]("http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4505-3121_7-33088925.html") and place it in this [http://www.pcmag.com/article2/0,2817,2370788,00.asp?tab=Specs]("http://www.pcmag.com/article2/0,2817,2370788,00.asp?tab=Specs") and install the OS then take it out and put it back in the original computer? Will this work?

---

### Post by coldraven on 2013-09-11
I think you need to find out how to get into the BIOS Setup screen so that you can boot from a USB stick or a memory card.
On my laptop I have to press F10 at startup time but yours could be different.

The black screen thing is a mystery, I would go for a re-install.
I use a 1GB SD card to do my installs, I have a built-in card reader.
I use Unetbootin to make the card bootable. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
You can also use "Startup Disc Creator" which should already be on your Ubuntu box.
Make a card or stick and try booting with it plugged in, you may be lucky and it is already set to do so.

Your idea with swapping drives might work but of course the install will have detected different hardware. It would be a chore to try and correct.

Edit: I put Xubuntu 12.04 on an eeePC 900 and it works fine on this tiny underpowered netbook.
Also my X1250 card in this HP laptop is OK if you don't use 3D stuff like games. (HP Compaq 6715b)

---

### Post by jesus-freak on 2013-09-11
The problem is that even if I can get into the Bios There is no option to boot from any USB device. So I don't have the option of installing from the CD or from a USB.

---

### Post by oldfred on 2013-09-11
Both my computers from 2006 boot from USB flash drives. One shows USB flash drive but the other will not show any USB devices as flash drive but has many USB boot options, but only by accident when changing boot to another hard drive and having flash drive plugged in did I see that it was under hard drives not USB devices.
Flash drive must be configured to be bootable and then look under hard drive boot choices.

---

### Post by jesus-freak on 2013-09-11
Nope, this one doesn't, tried everything. Tried a USB external DVD drive, tried a flash drive, it doesn't see any of them and doesn't give any options to select them.

---

### Post by jesus-freak on 2013-09-11
Anyway, I can't get into the bios at all to try anything new. The bad thing is that I'm pretty sure that I got into the bios BUT it was still a black screen. So you know at start up when the grub page loads it give a few options and if you don't select an option it will automatically select the first one, to load Ubuntu normally. Well I can't see any of this now but I can tell that it is happening because eventually Ubuntu loads. So when I first started the computer, when the screen to enter the bios would normally have been see, I pressed the key to enter the bios. I waited and waited and Ubuntu never loaded so I'm pretty sure I opened the bios settings BUT I couldn't see anything, still all black.

Since this thread was about simply changing from a 64 bit system to a 32 bit system I've started another thread to deal with the specific problem of the black screen at start up. Thanks for the help!

---

