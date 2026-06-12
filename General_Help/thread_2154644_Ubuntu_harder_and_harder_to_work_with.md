---
title: "Ubuntu harder and harder to work with"
date: 2013-06-15
forum: General Help
---

### Post by Eric Buist on 2013-06-15
Hi,

Since I purchased Ivy Bridge based Core i7 computer last summer, I am experiencing more and more frustrating problems and instabilities with Ubuntu, from 12.04 to 13.04. One update fixes something but breaks something else and it now never stops, making user experience very bad and annoying. I got cracky sound in 12.04, fixed sound in 12.10, no sound at all in 13.04, sound back up after a kernel upgrade. I got no display at all in 13.04 after a kernel upgrade and a week later, back up again, but last kernel upgrade caused sluggish display in LWJGL-based applications such as Minecraft.

Mouse is erratic. Movement is VERY slow or just way too fast depending on the mouse, and no Unity settings have any effect. Mouse wheel is almost unusable, scrolling way too fast. If I try with arrow keys (from Google Chrome), sometimes it scrolls, sometimes I have to click to make it scroll (but the same scenario happens under Windows, so that one could be a Chrome issue).

Applications such as KeePass2 are now allowed to block the GUI completely and killall has NO effect on them; I now need to open a terminal, search with ps -aux | grep <app> and copy the PID to the kill command. KeePass2 was now showing up a contextual menu on screen and nothing could dismiss it. Alt-tab became ineffective and Escape, Alt-f4, click outside, all did nothing.

This is so random, so erratic, that one could suspect hardware failure! But the computer works well under Windows 7. I am not experiencing such erratic software behavior, so I am suspecting something in the Linux kernel not fully compatible with my system. Or quality of software on the Ubuntu repo degraded with time, because more and more junky software is made. Here I don't blame any particular people. I know Ubuntu developers are not responsible for all the pieces of software in the repos!

I am more and more constantly frustrated when working with my computer and starting to think about throwing the machine away and putting back the old one! But what will I do when that six year old machine will start having motherboard problems? I will be stuck with no solution! Ubuntu is now the only Linux-based OS I can use, because others are sticking to GNOME3 which is unusable for me. I have trouble following the mouse on screen and move it at top left when I loose the pointer, but GNOME3 just pops up a context menu in that situation, and there is no reliable way to turn that off other than distro and version specific changes in system scripts!

Could some of these problems be caused by the fact I set up a UEFI-based boot or because I made the stupid mistake of choosing the builtin Intel HD4000 graphic instead of a dedicated graphic card? Or could the fact that Ubuntu runs from a SSD be a problem. I know that many people are running Ubuntu on Ivy Bridge, from SSD, probably even with the same motherboard as me and I cannot believe they are experiencing all these difficulties and just considering that's normal.

My computer specs are the following:
- Intel Core i7 3770K
- Asus P8Z77-V LX
- 16Gb of DDR3 Corsair 1600MHz memory
- Ubuntu running from an OCZ Agility 3 SSD drive
- 1TB Western Digital hard drive
- Microsoft Comfort mouse

Thanks for any help

---

### Post by The Spectre on 2013-06-15
I have similar Hardware specks as you and my system is rock solid.

- Intel Core i7 3770K (O.C. to 4GHz)
- Gigabyte - Z77MX-D3H (UEFI)
- 16Gb of DDR3 G.Skill RAM
- OCZ Vertex 3 SSD
- Logitech Performance MX Mouse

Running Ubuntu from an SSD with the built in Intel HD4000 Graphic should not be a problem.

And I have had no issues with the UEFI Bios on my system so I dont think it should be giving you any problems either.

When you went from Ubuntu 12.04 to 12.10 and 13.04 did you do a Clean Install or did you do a Upgrade?

If you did an in place upgrade maybe that has introduced some system instability.

---

### Post by Mark Phelps on 2013-06-15
Couple of comments ...

I recently installed Linux Mint 15 on an SSD and can attest that presents no problems.  Since that is based off Raring (13.04), you should have the same experience on your SSD.

I'm really impressed by the Cinnamon desktop experience in Mint 15.  Don't know which version of Gnome that it, but you should think about giving it a try.  I was really impressed by how everything just simply installed and worked with Mint15.

---

### Post by BBQdave on 2013-06-15
Ubuntu Unity 12.04LTS - 64-bit is smooth and stable on Toshiba Satellite c655-s5503. Bought notebook new a little over a year ago, intel hardware with intel graphics - at this point, 12.04 *a year out* is a solid daily driver :)

May be worth a fresh install of 12.04LTS on your intel hardware.

---

### Post by Rebelli0us on 2013-06-15
Kernel 3.2 in Precise has random problems (and crashes) on z77 platform. You may need kernel 3.5 or later. HD4000 is very well supported though. If  GNOME3 is unusable try MInt Mate 13/14.

---

### Post by Eric Buist on 2013-06-29
Hi,

Thanks for the replies.

Thinking about it, the main problem is the blank screen at boot. Other problems are minor and just adding up. The latest kernel fixed the blank screen but made 3D acceleration poor. I admit this is not a problem for desktop use; it causes difficulties only when trying to run some 3D applications or games, which most people consider a Windows-only task. So bottom line, there is no general-purpose OS and I will have to spend my time rebooting and rebooting, or buy myself a second computer to run Windows and Linux side by side. The new machine will definitely have a NVIDIA graphic card.

Mouse problem is cross-platform. I have issues with the mouse wheel on Windows as well. But settings for mouse speed are working on Windows, while they have no effect on Ubuntu (relies on high end mice capable of adjusting their speed?). I am stuck to Microsoft or Logitech mice, otherwise the mouse does not work with Mac OS X without a 25$ third party tool.

Maybe I, again, did the wrong choice with KeePass2 and will have to manually transfer the passwords to some other software.

Doing a clean install may help. I will attempt it eventually, especially before throwing the machine away.

Bottom line, I will need to spend A LOT of time with trial and error to improve things.

---

### Post by Eric Buist on 2013-07-14
Just tried the clean install. I got no blank screen at boot since then, but Minecraft is still a bit sluggish. Seems slightly better than before the clean install, but the game runs smoother under Windows. Lesson learned, I will avoid integrated graphics for any future PC intended for non-Windows use, but for now, I am left with nothing except reboot, reboot and reboot. At least no more blank screen is a progress.

---

### Post by Eric Buist on 2013-07-16
Minecraft is definitely as awfully slow as before and the mouse wheel scrolls way too fast without any setting to change this. I cannot use the wheel at all now, have to fall back using the keybaord's arrow key. Other mice I tried are too poorly manufactured so the mouse wheel or buttons stop working after a month or two! At least I got no more blank screen after the clean install.

What  is the problem? Is it because Ubuntu is only for business and no gaming AT ALL, even no Java-based things? Then Windows is far more versatile, supporting business AND gaming! This is real shame. I need Ubuntu for fun but also for Unison; this is the only way I can sync directories between my main computer and HTPC without copying the full things each time (Windows-based sync tools do that, taking a huge amount of time just to figure out what changed!).

---

### Post by Eric Buist on 2013-07-16
At least I fixed the mouse wheel issue using resetmsmice. Found this on [http://ubuntuforums.org/showthread.php?t=2080597&highlight=Comfort+4500+mouse+wheel](http://ubuntuforums.org/showthread.php?t=2080597&highlight=Comfort+4500+mouse+wheel), tool is at [http://sourceforge.net/projects/resetmsmice/](http://sourceforge.net/projects/resetmsmice/).

---

