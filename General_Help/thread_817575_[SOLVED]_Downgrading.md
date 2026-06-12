---
title: "[SOLVED] Downgrading"
date: 2008-06-03
forum: General Help
---

### Post by Powerman2442 on 2008-06-03
I am planning on downgrading from 8.04 to 7.04, mainly because the program I used to install ndiswrapper and a Windows driver for my Broadcom wireless card does not work on 8.04. Could anyone tell me how to switch back to the Windows Vista bootloader, because once I format the Ubuntu partition and reinstall 7.04 it may not let me into Windows.

Or could I just format the Ubuntu 8.04 partition and boot from the 7.04 LiveCD and use the 7.04 bootloader? Not 100% sure how this will work out. Last time when I had to uninstall Ubuntu 7.04 because of the desktop effects getting messed up and being unable to find the LiveCD to fix it (didn't label the CD) I formatted the 7.04 partition which cause me to not be able to boot into Windows, since the Ubuntu bootloader no longer existed, to figure out which CD was my LiveCD.

If you need any clearing up on this let me know. I am fairly busy but I wanted to figure this out when I had the time to post the question.

Thanks

---

### Post by pytheas22 on 2008-06-03
> Or could I just format the Ubuntu 8.04 partition and boot from the 7.04 LiveCD and use the 7.04 bootloader?

Yes, I don't see why this wouldn't work.  The installer for 7.04 should just detect Windows and configure grub appropriately.

If you wanted to switch back to the Windows bootloader, however, booting to the Windows install CD and running fixmbr should allow you to rewrite a Windows boot loader (at least, it does from the XP install CD).

But before you do any of this, I'm wondering how hard you tried to get your wireless card working.  If you tell us which kind it is (use the lscpi command if you don't know), maybe we can tell you how to make it work in 8.04 and avoid all of this reinstallation.

---

### Post by EXCiD3 on 2008-06-03
If you just format the 8.04 partition and then promptly reinstall Feisty you will have no different of a setup than you currently have. It will automatically detect the OS's you have installed and you will be able to boot into Windows just like you have been donig.

Since you've got a broadcom card definitely check out this thread: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)
Ayuthia is a good friend and he could probably get your card up and running in no time. He's like "the broadcom god" Make sure you tell him i said that ;)

---

### Post by Powerman2442 on 2008-06-03
pytheas22 - I spent about 2 weeks trying to get 7.04 to work with my card and I finally found a file on the forum... (bcm43xx-0.3.2-offline.tar.gz) and it works perfectly with 7.04. (Well almost perfectly)

The only problem is when I try to use that with 8.04 it tells me that to contact the author to have them compile the ndiswrapper and Windows drivers for my current version of Ubuntu.

They gave two e-mail address, which I did e-mail them both, but I still have yet to get a reply back.

Not sure I want to go through this again with 8.04. Really I don't have the time right now, plus it is summer so I am on the computer less and less.

EXCiD3 - I will check out that link and see if I can figure anything out. I might play with it some more before switching back, although I am really tired of messing with Broadcom and Linux. :(

Broadcom support and problems with my ALSA have haunted me since I started with Ubuntu. But I did get into it to "play" with it. At certain points it isn't fun anymore.

Thank you both for the info and I will see if I can get it to work with info from that link. If all else fails back to 7.04.

---

### Post by Slim Odds on 2008-06-03
Just remember that support for 7.04 ends October 2008

---

### Post by pytheas22 on 2008-06-04
> I am really tired of messing with Broadcom and Linux. 

There was a major change in the Broadcom driver between 7.10 and 8.04--Ubuntu now uses the b43 driver by default, instead of bcm43xx, which was used in earlier versions.  If you got your card working in 7.04 but can't in 8.04, this is probably the reason.  Fortunately, it's easy to switch back to the old Broadcom driver.  Just type:
```

sudo gedit /etc/modprobe.d/blacklist
```

and look for the line that says "blacklist bcm43xx."  Delete that line, and add a new line that says "blacklist b43"  Reboot (or use modprobe to switch drivers) and you'll be using the more stable Broadcom driver.  b43 is supposed to provide more features but still has a lot of bugs.  I wish they'd waited a little while longer before making it default.

I just thought this information might be useful if you haven't read it already.

---

### Post by Powerman2442 on 2008-06-05
Okay I did an lspci -nn and I found this... or something similar.

Broadcom Corporation BCM4311 (rev 01) [14e4:4311]

I took a screenshot from Ubuntu and saved it to my Windows partition but I can't view it in Windows. However, it did say something along the lines of what I posted above.

Look at this link [http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692) the author clearly says "Chipsets known not to be working in Ubuntu with b43/b43legacy(you can check by typing lspci -nn at the terminal):
14e4:4311 rev 01
14e4:4312 rev 02"

But when I go to another link [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) It says that bcm4311 rev 1 / bcm4312 are supported.

Might have my wireless up and running by 9.04. :(

I even tried the blacklist thing. It said...

#replaced by b43 ssb.
blacklist bcm43xx

and I changed it to...

#replaced by bcm43xx
blacklist b43 ssb.

When I rebooted it didn't even start my wireless card. Did I change the blacklist file correctly?

Looks like I have to go back to ndiswrapper? This is what really makes me not want to use Ubuntu. I like it and everything but how can I get rid of Windows Vista when I can't connect without wires? It is a laptop... I guess it wouldn't be a problem if it was a desktop.

I am going to keep looking into this but sitting in a hot room, rebooting from Windows to Linux and vice versa is annoying me.

Thanks,
Powerman2442

---

### Post by pytheas22 on 2008-06-05
I helped someone with a 4311 card last week.  We concluded that even though some places on the Internet say that it should be supported by the bcm43xx driver, it probably won't work reliably yet.  If you want to try, you would need to install the firmware first, and add the line "blacklist b43" to /etc/modprobe.d/blacklist (you added "blacklist b43 ssb"...this might work but I'm not sure; I would add another line without the ssb).  Run:
```

sudo apt-get install bcm43xx-fwcutter
```

and when you're asked if the firmware should be automatically installed, click yes.  If this works, after a reboot, your wireless will work again.  But I wouldn't get my hopes up.

A more reliable solution is ndiswrapper.  There's a guide [here]("http://ubuntuforums.org/showthread.php?t=760568") for getting it working with your card.  I think it's your best bet.  The guide is pretty comprehensive but if you run into trouble, post here.

---

### Post by EXCiD3 on 2008-06-05
Ayuthia just release a Broadcom configuration tool to setup your broadcom wireless for you in Hardy if you are having troubles. Its definitely worth a shot: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by Powerman2442 on 2008-06-05
pytheas22 - I added b43 ssb because the line above Blacklist bcm43xx said "#replaced by b43 and ssb." So I thought I would blacklist b43 and ssb. I know I used ndiswrapper for 7.04 but I also found that easy to use .tar.gz file. Doesn't work with 8.04 like I said. :( I will the code along with a few other options I ahve gathered from the forums. It is hard cause I need to switch between Vista and Ubuntu to read this, copy it down, and then try it.

EXCiD3 - I will check out the config tool. Thanks a bunch.

---

