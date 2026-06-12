---
title: "Keyboard and mouse takes 2-3 minutes to detect on boot"
date: 2012-11-04
forum: General Help
---

### Post by jimbolad on 2012-11-04
Hi , 

this problem started randomly on a reboot as it was working fine before.

I get to the user login screen on ubuntu and the mouse icon appears but it takes a good 2-3 minutes for my USB keyboard (Razor Lycosa) and USB mouse to be recognised... 

I am running ubuntu 12.10 and have no clue why this has randomly started happening?

Any ideas? as its VERY annoying having to wait everytime , epsecially since I just bought a SSD to increase boot time

---

### Post by mardybear on 2012-11-04
Hi jimbolad...

Is your system up to date?

Have you tried booting to an older kernel in the grub screen? Any difference...

Did the problem appear at the same time you started using your SSD?

mardybear

---

### Post by flowerdealer on 2012-11-05
I also have this issue, this really sucks. For me it just not seem to work at all. Never had such a horrible bug with any other ubuntu release.

---

### Post by bjforesthowell on 2012-11-05
I'm having a very similar issue, only mine stops working after I log in. At the log in screen my keyboard and mouse work just fine (it does take some time to recognise the mouse). Afterwards though.... Crisis-lock-down. None of my keyboard shortcuts will work, and the ony thing that I can do is hard boot the computer

Everything worked fine during the live cd trial so that I could check for compatibility issues with my hardware, but once I starting installing and updating things went down hill really quick.

I've been using Ubuntu for years now, and this by far has been the worst upgrade experience between NVIDIA issues and now this.

People are experiencing the same issu on these two threads as well...

[http://ubuntuforums.org/showthread.php?t=2059135&page=2](http://ubuntuforums.org/showthread.php?t=2059135&page=2)

[http://ubuntuforums.org/showthread.php?p=12337832#post12337832](http://ubuntuforums.org/showthread.php?p=12337832#post12337832)

---

### Post by idoitprone on 2012-11-05
> **jimbolad said:**
> Hi , 

this problem started randomly on a reboot as it was working fine before.

I get to the user login screen on ubuntu and the mouse icon appears but it takes a good 2-3 minutes for my USB keyboard (Razor Lycosa) and USB mouse to be recognised... 

I am running ubuntu 12.10 and have no clue why this has randomly started happening?

Any ideas? as its VERY annoying having to wait everytime , epsecially since I just bought a SSD to increase boot time
Never buy your mouses from that company-Razer

[http://www.overclock.net/t/1323093/razer-razer-synapse-2-0-used-for-always-on-data-mining](http://www.overclock.net/t/1323093/razer-razer-synapse-2-0-used-for-always-on-data-mining)

They do weird things.

---

### Post by bjforesthowell on 2012-11-05
I just did a fresh install, and it's not the updates I downloaded. Now, when I log in the screen flickers, it logs me off, and I can see the mouse again while I'm at the log in screen. Whenever I move the mouse the screen flickers more. I'm not dual booting so I don't get the grub screen in order to put myself into the CLI. Do you know how to interrupt the boot so that I can try to fix it from there?

---

### Post by jimbolad on 2012-11-05
> **mardybear said:**
> Hi jimbolad...

Is your system up to date?

Have you tried booting to an older kernel in the grub screen? Any difference...

Did the problem appear at the same time you started using your SSD?

mardybear

Hi, my system is definate ou up to date.
I have been using my SSD for about a week now so that shouldn't really be a cause as it just started . One thing I will say is I was fiddling about with trying to mount my raid drive and on a tutorial it said to go though and add a startup application , having said that there are no application running on startup as far as I can see?

As far as the grub goes no I haven't tried a older kernel and if I'm honest I wouldn't know how to, I've been using Linux for about a week and still overcoming the simple problems

---

### Post by jimbolad on 2012-11-05
Just tried a PS/2 keyboard and it worked fine... I've had a look round for drivers for both the keyboard and mouse and it doesnt wanna work?

---

### Post by mardybear on 2012-11-05
Hi jimbolad.

Even my old single boot Ubuntu has a grub menu...i don't know how to select another kernel otherwise but it sounds like this is a much bigger issue.

Sorry i'm not of much help, but i feel your pain :(  Based on what i'm reading on the forums, i'm reluctant to upgrade my 10.04 install as it works perfectly (not rubbing it in).

At least you found a workaround (PS2 mouse and keyboard), although not an optimal solution.

Good luck,

mardybear

---

### Post by flowerdealer on 2012-11-05
Would it be possible that this is a grub issue? Funny thing, I also have a 12.04 install of ubuntu on the same machine, and since the 12.10 updated I also get the same behaviour on that install...

---

### Post by mardybear on 2012-11-05
> **flowerdealer said:**
> Would it be possible that this is a grub issue?
I don't think it's a Grub issue. Grub just allows you to select which linux kernel to boot as it could be a kernel issue, which provides hardware support.

mardybear

---

### Post by jimbolad on 2012-11-05
> **mardybear said:**
> Hi jimbolad.

Even my old single boot Ubuntu has a grub menu...i don't know how to select another kernel otherwise but it sounds like this is a much bigger issue.

Sorry i'm not of much help, but i feel your pain :(  Based on what i'm reading on the forums, i'm reluctant to upgrade my 10.04 install as it works perfectly (not rubbing it in).

At least you found a workaround (PS2 mouse and keyboard), although not an optimal solution.

Good luck,

mardybear

Thanks for the reply , and yea it's very annoying , don't really wanna have to get rid of my keyboard as its a razor lycosa and I like it haha. Out of interest how easy is it to downgrade tocsin 12.04 to see if it works?

---

### Post by mardybear on 2012-11-05
Hi again.

Hopefully someone with more experience will be able to provide additional advice - anybody ???

If you are thinking about installing 12.04 i would recommend backing up any personal data onto a CD/DVD or other drive and then doing a full drive format and fresh install. Lots of users on this forum have encountered update issues between various releases.

If you don't need the latest/greatest, Ubuntu 10.04 will still be supported for a while longer, has most of the bugs fixed and seems to run rock solid.

Good luck,

mardybear

---

### Post by bjforesthowell on 2012-11-06
Does anyone else's system work fine while running off of the live CD?

---

### Post by jimbolad on 2012-11-06
> **bjforesthowell said:**
> Does anyone else's system work fine while running off of the live CD?

yep :/

---

### Post by bjforesthowell on 2012-11-06
I've got an NVIDA vido card and this worked for me after working with NikTh (nick-athens30) on launchpad....

During boot you're going to see a purple screen with no Grub options if you're not dual booting. When you see that purple screen hold the [SHIFT] key until grub menu appears and select "Advanced settings".

At this point, you're going to want to select the kernel with the recovery mode options and just hit enter at the next screen.

Once I was in recovery mode I had my input devices and everything was gravy. I was able to run the software update then, while I was in I installed drivers with the directions from this site...

[http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

Now my global menu and launcher aren't coming up, but this shouldn't be a problem to fix now that I've got input devices.

I hope this helps...

---

### Post by bjforesthowell on 2012-11-07
If you've got an Nvidia video card here's how you get your top menu and launcher back after you have access to your input devices...

[http://askubuntu.com/a/202587/104413](http://askubuntu.com/a/202587/104413)

---

### Post by beameup on 2013-01-31
My mouse never gets detected. Once it boots up, I have to unplug it, then plug it back in and it works fine after that.
Trackpad works fine. No issues at start up but have to use trackpad.

Mouse is an IOgear Optical calling Mouse.
Laptop: Acer Aspire 5517 64bit with ATI Radeon 3200 graphics
Ubuntu 12.10 64 bit

Not using proprietary graphics driver. 

Any troubleshooting I can do?

---

