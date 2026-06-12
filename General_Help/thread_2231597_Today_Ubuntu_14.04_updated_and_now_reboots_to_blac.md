---
title: "Today Ubuntu 14.04 updated and now reboots to black screen?"
date: 2014-06-26
forum: General Help
---

### Post by SkOrPn on 2014-06-26
Why are fresh installs of Ubuntu keep crashing hours or days after being installed? I'm on day 2 of a fresh install and today software updater informed me of some updates, it was only 85 mb or so, so no big deal. So I let it update, and then I rebooted and now I get nothing more than a black screen. I tried using the shift key during boot so I can use the Recovery mode, but when I hit the shift key I only get the below. This is like the 5th time in the last two weeks that Ubuntu has up and died on me for no reason.

```
Environment Block
Press any key to continue...
```

And then nothing but blackness, no flashes, no sounds, no led's blinking, no response to key presses, just nothing. Is there any possible way to force this OS to always work? Or is the Linux security becoming so enforced that now we just have to sit and stare at the screen and day dream about using your computer? Should I just disable updates permanently? I have work to do and re-installing Ubuntu for the 6th time in just days is not something I have on the agenda today.

How can I fix this? Please... :p

---

### Post by LastDino on 2014-06-26
That is probably grub trouble, no need to re-install the whole thing.
I've seen that on Luanchpad, there is some solution too, but not sure if it works on 14.04 as it was confirmed on 12.04.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)
Other people might have better solution than mentioned there, so maybe wait for few more people to chip in.


Might as well look at these as they seem to be more explained.
[http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)
[http://ubuntuforums.org/showthread.php?t=1285098](http://ubuntuforums.org/showthread.php?t=1285098)

---

### Post by SkOrPn on 2014-06-26
> **LastDino said:**
> That is probably grub trouble, no need to re-install the whole thing.
I've seen that on Luanchpad, there is some solution too, but not sure if it works on 14.04 as it was confirmed on 12.04.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)
Other people might have better solution than mentioned there, so maybe wait for few more people to chip in.

Thank you LastDino (love the user name lol), I wish there was a "Thanks" button here, like most other forums, but there isn't. Anyway, not sure why Grub would spontaneously break like that. There's no excuse for that to happen. 

I guess I will launch the live USB session AGAIN, and see if maybe boot repair will solve it, although that only seems to work half the time. Maybe I get lucky today.

EDIT: Just had an idea, I wonder if I can have two Ubuntu setups on two different hard drives and neither point to the other? I mean each Grub being independent and unaware of each other. One I can use as a quick backup with a known working setup and the other as the daily experimenter, lol... Or is that what Live is for mainly?

EDIT2: Removed the angry text of mine, because I need to stay calm. Sorry...

---

### Post by LastDino on 2014-06-26
Well, try the solution given there first. I don't have that issue so I can't say if it can be fixed with boot repair.


Having backup/spare install/clone of working install is definitely good idea though.

---

### Post by SkOrPn on 2014-06-26
> **LastDino said:**
> Well, try the solution given there first. I don't have that issue so I can't say if it can be fixed with boot repair.


Having backup/spare install/clone of working install is definitely good idea though.
Thanks, I removed some angry text in my previous post that I been gritting my teeth all week to post. lol I keep typing out angry stuff, only to remove it before posting but today I have had it and couldn't help posting it. Anyway its removed and please forgive me. I'm trying to run a business here so please understand where my anger comes from. I'm a very kind soft spoken person otherwise...

Will report back if Boot-Repair fixes it. I did not see any solution in that thread from 4 years ago that would help with Ubuntu 14.04 to overcome a broken update in June of 2014. Will look at it again though. Thank you

---

### Post by LastDino on 2014-06-26
[http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

It is for 12.04 yes, but there are common factors like grub and grubenv file. Its worth a try IMO. At worst, you might be back to where you're now.

---

### Post by yancek on 2014-06-26
One thing that may have happened is a kernel upgrade.  Usually, update-grub is run if there is a kernel upgrade so you would need to watch the output of the updates.  This is usually at the end of the update.  If it doesn't update grub after a new kernel, run it manually BEFORE rebooting.  Not sure that this was the problems in your case.

> Just had an idea, I wonder if I can have two Ubuntu setups on two different hard drives and neither point to the other?  

Yes.  Simply install Grub to the master boot record of its hard drive.

---

### Post by craig10x on 2014-06-26
There was a kernel update in 14.04 today, by the way...just wanted to mention (3.13.30 i believe) ;)

---

### Post by SkOrPn on 2014-06-26
Hmm, interesting. I tried pressing the "e" key and I now get this. Anyone know what this is trying to tell me? At the bottom of the screen it lets me do a normal boot, but I just get a black screen.

[IMG]http://i.imgur.com/uHhUlFZl.jpg[/IMG]
[IMG]http://i.imgur.com/y0ucuNil.jpg[/IMG]

---

### Post by SkOrPn on 2014-06-26
> **LastDino said:**
> [http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](http://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

It is for 12.04 yes, but there are common factors like grub and grubenv file. Its worth a try IMO. At worst, you might be back to where you're now.
I tried everything listed on that page, and kept getting errors. I still have not tried Boot-Repair and probably wont, just to be safe. I think I will just use Windows for now and wait to see if anymore Ubuntu users encounter the same problems after updating. Maybe the solution is just a day or two away, who knows. And I was very much enjoying it. Unity has come a long way over the last few years.

---

### Post by yancek on 2014-06-26
> Anyone know what this is trying to tell me? 

That is your menuentry line in the grub.cfg file for your Ubuntu install which shows it is on the first partition of your sixth hard drive.  Generally, at this point one would enter any additional parameters to the linux line or initrd lines.

>  			 		 	 I tried everything listed on that page, and kept getting errors

You didn't post the errors so we have no idea what they are.  Have you tried the suggestion at the link below?

[http://ubuntuforums.org/showthread.php?t=1285098](http://ubuntuforums.org/showthread.php?t=1285098)

---

### Post by SkOrPn on 2014-06-26
> **yancek said:**
> That is your menuentry line in the grub.cfg file for your Ubuntu install which shows it is on the first partition of your sixth hard drive.  Generally, at this point one would enter any additional parameters to the linux line or initrd lines.



You didn't post the errors so we have no idea what they are.  Have you tried the suggestion at the link below?

[http://ubuntuforums.org/showthread.php?t=1285098](http://ubuntuforums.org/showthread.php?t=1285098)
Well just got home and decided to try again, but this time when I boot Ubuntu I get a quick purple flash and then nothing. Pressing the "e" key no longer does anything and neither does the Shift key. In fact, as far as I can tell no key on the keyboard does anything now. All from a simple update. This just teaches me to never trust updates again.

I'm going to try one last attempt at using Boot-Repair from the Live USB and then if that don't work I am giving up on Ubuntu. It does me no good if it will not stay running and re-installing once or twice or 5 times a week is just not acceptable... I think I like Unity better than all the other UI's, however it does not like me one bit :(

---

### Post by monkeybrain20122 on 2014-06-27
> **yancek said:**
> One thing that may have happened is a kernel upgrade.  Usually, update-grub is run if there is a kernel upgrade so you would need to watch the output of the updates.  This is usually at the end of the update.  If it doesn't update grub after a new kernel, run it manually BEFORE rebooting.  Not sure that this was the problems in your case.


No, if it is that then you just end up booting into the old kernel.

---

### Post by SkOrPn on 2014-06-27
> **monkeybrain20122 said:**
> No, if it is that then you just end up booting into the old kernel.

It could have been my problem, it did do a kernel update. However, I didn't know it was necessary to watch out for kernel updates. I left the updating system at defaults, so I would expect the defaults to be safe. I no longer have any input working on the keyboard when trying to boot to that Ubuntu. So, I will need to figure out how to fix it from the Live USB. Maybe if I can boot to the previous working kernel and it does boot to it then I have my culprit.

The whole reason why I gave Ubuntu its very own SSD to do with how it pleased and in AHCI mode, on its very own non-shared SATA controller no less, was because I thought that was possibly the most stable way to do it.

Does Ubuntu or Debian have issues with my hardware maybe?

Rampage III Extreme Intel x58 system (LGA1366)
Intel XEON Hexa-Core X5650 (6C12T)
4GB x 3 = 12GB of 1600 MHZ RAM in TRI Channel-Mode
AMD Radeon HD 5870 Video Card

2 x Samsung 840 Pro's in RAID0 (Intel FakeRAID)= Windows
2 x Crucial C300's in RAID1 (Intel FakeRAID)= Temp DATA Drive
1 x OCZ Vertex in AHCI Mode (Marvell Controller)= Ubuntu 14.04 LTS (Unity)

NOTE: My motherboard has BIOS only (NO UEFI), so I use "F8" during boot to simply select what drive I want to boot to. This gives me the added benefit of not letting the OS's mess with one another. If Windows breaks it will not take down my Linux install. And, if Ubuntu breaks than it will not affect my Windows install. If a OS goes down, I simply reboot into the other working OS and do the research to fix the broken OS. This was the idea anyway...

And I installed Ubuntu on a OCZ Vertex Barefoot drive, with no other OS sharing it. Its only a 30GB drive but it has not had many writes to it. So should be absolutely perfect for Ubuntu. Does Ubuntu have any known issues with this combination of hardware? Windows runs amazing on this system, so if there is a hardware problem it must be a Linux issue. Unless you guys think I just got updated to a corrupted Kernel? That would be a first for me, lol...

---

### Post by LastDino on 2014-06-27
The only thing I can think of is that ''maybe'' updated kernels are not compatible with your dedicated graphic card. Now you're not even able to get into grub so I'm not sure if you can do nomodeset and check that. But try hitting F6 while booting to see if anything shows up,  maybe it wont work as pressing ''e'' is not working but worth a try.

---

