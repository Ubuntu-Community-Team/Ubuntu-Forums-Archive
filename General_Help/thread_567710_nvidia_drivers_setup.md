---
title: "nvidia drivers setup"
date: 2007-10-04
forum: General Help
---

### Post by magikx21 on 2007-10-04
Okay I am attempting to install the nvidia drivers from the nvidia site and when I try to install it says I can't be running X during the installation. How do I close X to do this, as you can tell I am not that experienced with linux. I tried t boot into the fail safe and when i tried to run the setup it told me to run it on run level three. Well telling it to run on level 3 started X.

---

### Post by tj111 on 2007-10-04
Don't bother with any of that.  There's little documentation on it, and I was having the same problems.  Somehow I stumbled onto [this thread (see the update part)](http://ubuntuforums.org/showthread.php?p=1773584)  Run this command to open the nVidia built in driver GUI (similar to nView under windows).
> gksudo nvidia-settings

---

### Post by FuturePilot on 2007-10-04
Wouldn't it be easier to use the Restricted Drivers Manager? Unless your card isn't supported by the drivers in the repos.

---

### Post by themoebius on 2007-10-04
Yeah most likely you don't need to install the drivers from nvidia directly. Its much better if you use ubuntu's package manager because its easier to remove and when there's an upgrade, it will be done automatically. If you have an nvidia card it should have been detected by ubuntu automatically and if you open the Restricted Drivers Manager from System > Administration, it should be listed there. Otherwise, there are some nvidia packages you can install using apt-get or Synaptic or my favourite, Adept.

---

### Post by magikx21 on 2007-10-05
I used the restricted drivers utility on my PC running Kubuntu Gutsy, no problem; however, on the PC in question I'm running Kubuntu Fiesty x64 and am not sure how to get to the restricted drivers manager.

---

### Post by magikx21 on 2007-10-05
sorry for the double accidental double post.

---

### Post by raydar on 2007-10-05
So, magikx21, do I understand right that you're getting no problems with the restricted nvidia driver in Gutsy?  

I'm running the 32-bit Gutsy beta with Gnome, unlike your setup, and X won't start for me if I use anything but the (non-restricted) "nv" driver.  Thus I can use only 1 of my 2 monitors with my Nvidia GeForce FX 5600 card.  In the thread [http://ubuntuforums.org/showthread.php?t=564158](http://ubuntuforums.org/showthread.php?t=564158) , I was told the restricted nvidia driver for Gutsy isn't working yet.

I'd prefer to install drivers via Ubuntu's update & package managers rather than from the Nvidia site, and so I've pretty much been waiting for either Gutsy's "release candidate" version to arrive or news that the restricted driver is ready, whichever comes first.

When I enable the restricted nvidia driver via the Restricted Drivers Manager, Ubuntu installs "nvidia-glx" (after automatically un-installing "nvidia-glx-new," when I've tried using that) and X won't start properly until I edit xorg.conf to put the driver back to "nv."

---

### Post by magikx21 on 2007-10-05
Well I updated a 32bit Fiesty box up to the latest Gutsy and the restricted drivers utility came up and I installed the nVidia drivers and I had no problems yet. I haven't played around with it really but I have seen no errors. It is an older card though, it is a GeForce 2.

---

### Post by magikx21 on 2007-10-08
Ok, I got this all worked out the other day. I installed the restricted manager on my Feisty x64 box using apt-get then I launched it from terminal all setup my drivers. It seems the restricted manager just isn't right in front of me like it was when I upgraded my other box to Gutsy and it poped up when I logged in.

tj111, I kind of forgot about your reply with nvidia-settings. I will try that when I get home.

---

### Post by CulleyS on 2007-10-08
I manually downloaded the drivers from Nvidia as well.  When I used the Restricted Driver Manager, it didn't automatically register my second monitor.

I'm on the latest development branch of gutsy as well for x86 64: Ubuntu gutsy (development branch), kernel 2.6.22-13-generic.  However, each time I go to a new release I have to recompile my nvidia driver.  I shouldn't say each time, but going form .12 to .13, I did have to go through this process.  When I'd tried to boot into .13 (after installing the nvidia drivers on .12) I'd get a message like NVIDIA driver kernel not recognized.  Sorry, don't remember the exact message.

Perhaps installing through the restricted driver manager would rectify this, but as I said, when I installed that way, my second monitor wasn't automatically detected.  So, either way, I'd have to do some manual configuration.

---

### Post by raydar on 2007-10-08
I've seen a few things with the number 2.6.22 go by in the updates, but nothing newer than 2.6.20-16 has shown up in my grub menu, either when I upgraded to Gutsy beta or afterward.  I've got one Ubuntu 7.10 beta hard disk and one up-to-date UbuntuStudio 7.04 hard disk in this box, and those are the only two OSs that show up in my menu.

However, only the most recent kernel shown (2.6.20-16)  in my 7.10 beta section wants to boot; the two or three previous versions give a file not found error when I try to boot them.  (That installation has been upgraded since the very end of Dapper.)

Do I need to be booting something different here--maybe that's why the "nvidia" driver won't work for my Geforce FX 5600 & 2nd monitor?  Starting to suspect I have a "stale" grub . . . though I have seen ati and I think ibm video drivers come down the update pipe recently; should I still just be waiting for the hen to produce an nvidia egg?

---

### Post by raydar on 2007-10-19
Something was (and is) indeed not behaving like it should in my straight Ubuntu installation, 'cause I did a Feisty-->prerelease Gutsy upgrade to my other Ubuntu installation (UbuntuStudio as opposed to straight Ubuntu) and everything turned out fine, i.e., new kernel showed up in the grub list and the Gutsy version of the nvidia driver, once it was released and came down the pipe, let me use both monitors.  I have no idea why the new kernel wouldn't show up in my straight Ubuntu installation's grub menu, but I still suppose the inability to boot the new kernel kept the video from functioning properly, since the new video driver was probably coded to take advantage of something specific to the new kernel.

In short, I've abandoned the straight Ubuntu installation since my UbuntuStudio installation is now working find under Gutsy.  See [http://ubuntuforums.org/showthread.php?t=573186](http://ubuntuforums.org/showthread.php?t=573186) for more specifics if you're curious.  Thanks for everyone's assistance!

---

