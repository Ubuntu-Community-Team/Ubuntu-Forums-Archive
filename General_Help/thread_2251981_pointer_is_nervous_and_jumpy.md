---
title: "pointer is nervous and jumpy"
date: 2014-11-08
forum: General Help
---

### Post by gufghur on 2014-11-08
Hi all,

I use the mousepad to get things done on my computer, but since a week or so, the pointer reacts very jumpy to my manipulations on the mousepad, with the continuous result that a lot of stuff is happening that I don't want to happen. It frustrates the hell out of me: submenus keep popping up, the cursor in Word relocates itself, the internet browser pages back or forward, the sidebar with preferred software doesn't open, or if it does, programs open that I don't want, etc...

In system settings, I've checked and changed mousepad options, but that doesn't fix the problem. Also universal access offers no solace.

Anybody has a solution?

Thanks in advance.

---

### Post by Bucky Ball on 2014-11-08
Wish I could offer help. Sounds rotten. Which release are you using?

PS: you are not still using 11.04 I hope?

---

### Post by gufghur on 2014-11-08
Nope. I'm on 14.04

I've been writing (or trying to write) in Word ever since my post, and the problem is only getting worse. In somehow, I have the feeling the mousepad reacts on static electricity coming from my hands? Does that make sense?

---

### Post by grashdur on 2015-03-19
I'm having the same problem. And when I type text, there's often a delay before the text appears on screen (in Chrome, LibreOffice, WPS Office, etc.). At first after installing, music was also cutting out intermittently while playing in Rhythmbox. Lately that hasn't been happening (but I recently switched to Clementine after Rhythmbox kept changing my song and album tags at random -- I don't know if that could be related). 

It's been happening ever since I reinstalled my Ubuntu 12.04. (I'd love to use 14.04 instead, but on those later versions my touchpad moves the pointer too fast across the screen [not fixable with the Mouse and Touchpad settings, nor with the Pointing Devices app from the Software Center, nor with xinput].) 

So, this is a fresh installation. These problems occur off and on at any time, regardless of how many things are open at the time. I have a dual-core AMD Athlon processor (II X2 250), and 8 GB of RAM. It's a 64-bit computer, a ZaReason system built for Linux. As far as I know, the only difference between my current system and what was running before is that all the updates ran at once (right after installing) instead of little by little over time. 

Any ideas?

---

### Post by stephen_ward on 2015-03-20
Check the settings on control panel and check mouse properties it needs to be changed. Sometimes its just a minor fault like change in settings. Hope it helps :)

---

### Post by grashdur on 2015-03-23
I tried fiddling with my pointer settings as suggested, but it doesn't help. I may have not posted this in the best place, since my issue is not only with the pointer.

---

### Post by craige2 on 2015-03-23
Hi, I don't know if it's the case, but I had same problem with my previous mouse and keyboard. Just to say in advance, it is not a sophisticated attempt to solve the issue and more important, when this solution was suggested to me, I laughed in first place, but it worked out for some very weird reason and then laughed even more! :)

Hope would be the same case for you, if not, best luck.

1st case: I was using microsoft mouse and keyboard, while I was logged on, I unplugged the usd for both mouse and keyboard and then plugged it back in after 5 secs. After that, worked like charm. I was doing this every fresh install for only 1 time, then was fine.

after months, 

2nd case: I switched usb gates. The usb was over heating after while and in another occasion, it was jammed ( was moving more than it should )

That was the case for me, hope would be so simple for you as well.

Best of luck

---

### Post by dragonfly41 on 2015-03-23
Re: your earlier question on interference

> 
In somehow, I have the feeling the mousepad reacts on static electricity coming from my hands? Does that make sense? 

Some discussions found ...

[http://superuser.com/questions/76649/laptop-touchpad-works-incorrectly-when-on-power-supply](http://superuser.com/questions/76649/laptop-touchpad-works-incorrectly-when-on-power-supply)

[http://ask.metafilter.com/245653/Laptop-touchpad-is-jumpy](http://ask.metafilter.com/245653/Laptop-touchpad-is-jumpy)

[http://rog.asus.com/forum/archive/index.php/t-35635.html?](http://rog.asus.com/forum/archive/index.php/t-35635.html?)


I would try disconnecting power supply unit (from mains socket) and try running your PC in battery only mode (that is, if if you have battery only mode of running).  Otherwise you could try an alternative power supply unit or from another mains socket.

Do you see the same erratic behaviour when ..

(a) you run in Ubuntu guest account or create a new account

(b) you run Ubuntu LiveCD or LiveUSB?

These steps (changing the status quo) should eliminate the question of possible interference.

---

### Post by grashdur on 2015-03-23
I tried unplugging the touchpad-keyboard, waiting five seconds, and plugging it in again. No difference.

I unplugged my touchpad-keyboard from the keyboard switcher (for switching between two computers), and plugged it directly into the computer's own USB port. No difference. 

Also, when I log into the Guest account, the problem remains. When I boot into the Live CD for 12.04, the problem is still there but less severe. When I boot into 14.04 (I left it installed in a separate root partition), the problem is there too (though I still have the problem that the pointer is out of control in that version). 

And now I just unplugged my usual Lenovo Thinkpad touchpad-keyboard, and plugged in a GearHead touchpad-keyboard. The jumpy pointer movements, and the delayed text entry are still happening. Actually they're even worse. I tried booting into Ubuntu 14.04 with this other keyboard, and I have the same jumpy movements and delayed text entry, although not quite as severe. 

This seems to be happening regardless of the keyboard, and regardless of the Ubuntu version. It's an Ubuntu problem. Why is this not affecting anyone else? And why was it not happening to me on my previous installation on this computer?

---

### Post by grashdur on 2015-03-25
It seems to have been a problem with the driver for my 25" HP LP2475w monitor: The newer, "preferred" driver causes jumpiness and delayed text entry, instead of making the Unity interface go invisible at random moments.

---

### Post by grashdur on 2015-05-11
I finally found a solution that worked for me:

For my Lenovo ThinkPad keyboard with a touchpad, versions of Ubuntu after 12.04 were unable to work well the touchpad: There was no way to control pointer speed with the standard settings (¨Mouse and Touchpad¨), and it was not fixable with the ¨Pointing Devices¨ app available in the Software Center, nor was it fixable on the command line using xinput.

Today I found [this webpage]("https://mydevelopedworld.wordpress.com/2013/11/30/how-to-configure-new-lenovo-x240-touchpad-on-ubuntu-13-10/comment-page-1/#comment-1038"), which offered a solution involving adding some lines to a file located in /usr/share/X11/xorg.conf.d/

After making this change and rebooting, the pointer was moving too slowly, but then it was easily fixable with the standard pointer settings. Now I'm finally able to use Ubuntu 14.04. Wonderful!

---

