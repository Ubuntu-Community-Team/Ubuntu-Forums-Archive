---
title: "input not supported on new install of 20.04"
date: 2020-10-11
forum: General Help
---

### Post by jgw on 2020-10-11
I thought I would install 20.04 on a machine that was running fine with 18.04   I also wanted to not upgrade but install a whole new deal on this one.  So, I downloaded the .iso file and created a usb drive for the installation.  Then I started the installation.  It went along fine and was doing stuff and then decided to put up the "input not supported" thing.  That being said I think that its still loading because the usb stick is still blinking and the drive light blinks about every 4 second.  This may mean everything is actually dandy but I have no way of telling and don't want to start pressing keys so I thought I would ask for advise.

I left my machine on all night its doing the same thing.  I have now re-booted and went to advanced options.  Then I started on those options.  I did the dpkg thing, then checked the file systems.  This initiated a LOT of activity and then there were a LOT of updates and configuration stuff.  Then it told me that there was some kind of an update and if I wanted to do that.  I entered with a 'Y' and it took off again.  Its now stopped or doing:
update initramfs: generating /boot/initrd.img-5.4.0-48-generic.  The drive light is flashing every 4 seconds (give or take).  I think its just stopped but cannot tell.  I just pressed ^c and that generated a whole bunch of new stuff after saying it had been interrupted.  Then it told me I had some choices.  1)send report, 2 read report, etc.  I choose to send the report and then the screen filled up with a bunch of dots and the drive activity light went solid but is now back to blinking every few seconds.  At the end of the dots it told me ERROR: and then error no.13 and then said it couldn't update and then gave me I had the same choices offered 1)send report, 2 read report, etc.  I am going to re-boot and see what happens.  

From searching I think that the initial "input not supported" has something to do with my monitor and my display.  I also turned my monitor on and off to see if that made any difference.  It didn't.  I use this monitor on three different machines with no prolbem (up to now)  My display is an nvidia display card (galaxy nvidia geforce gt440 1gb ddr3 128bit).  I have never had this problem before this installation of ubuntu 20.04.1.  
I REALLY need some help on this one!

I have now restarted my system.  First it went directly to recovery mode.  Then I told it to fix the file stuff it tried and failed then I just gave up and told it to just boot into ubuntu and it came up!  its not right, keeps on telling me there is a problem, then it switched and told me to re-boot and I am about ready to do that.  There are also some logs but there are a pile of them  I have attached a partial photo of the list.  Too much, I think, to attach the whole folder.

Thank you.....................

---

### Post by jgw on 2020-10-12
bump

---

### Post by grahammechanical on 2020-10-12
I think that the input not supported message may be referring to the video range of your monitor. The Nvidia card might be outputting video at a resolution that is outside the resolution range of the monitor.

Try re-installing but do not tick the box to install third party software. The installer will use an open source video driver that may get you to a working desktop and there you can try installing a Nvidia driver using Software & Updates>Additional Drivers tab.

You will also be missing some third party audio and video codecs but they can be installed later as well. You could also go to System Settings>Screen Display and adjust Resolution and screen refresh rate. Base the adjustment on the specifications of your monitor.

From the Grub menu we select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. At the recover menu if we select Resume we may get to a desktop using a low resolution video mode and an open source video driver. And we have a working system where we can make changes.

Regards

---

### Post by jgw on 2020-10-12
Thank you for the reply. 

I have now re-booted as per the request last time.  It came up with a request to log in, which I did, and it booted right up!  Its pretty interesting.  First, no more of that not supported stuff.  The other thing is that I downloaded 20.04.1 and put it on a bootable memory stick and that is what it booted up on as it was blinking during entire process.  Now, however, it looks as if it upgraded instead of replacing everything so I have all the stuff I had when I was dealing with 18.04.5  (background, gnome stuff (turned off but there), etc.  I then got an advisory offering to install stuff for 18.04.4 and 18.04.3 which I ignored but thought strange.  I have no idea what, exactly happened!  I thought what I did would have just cleaned up the entire disk and then install 20.04.1  I should also mention that I had to update A LOT of stuff!  (the updates just kept on coming).  When I started with the usb stick I told the system to use that to boot up with as well.  

Anyway, I have this machine back and its running and no more not supported stuff but other oddities.  All that being said I am well on my way to success although I have absolutely no idea why or how (another case of computer mystery which I am pretty much used to due, basically, to my own lazy and ignorance).  I should also add that, during this install, the only question I ever saw had to do with my keyboard.  All past installs had a number of questions but not this time.  During this whole thing I was requested to submit at least 5 different reports on this and that and which I duly did.  I suspect that I did everything wrong.  I have one more machine to upgrade and I am going to do that by just letter the program upgrade the machine, I know that one works with no trouble.

Thanks again!

---

