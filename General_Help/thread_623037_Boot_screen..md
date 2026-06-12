---
title: "Boot screen."
date: 2007-11-25
forum: General Help
---

### Post by diwas on 2007-11-25
When using the live cd option...the boot screen comes up but after i installed the OS, there is no boot screen, instead of that there is a pitch black screen. During that time when i press Ctrl+Alt+F1, No resume image or smthg like dat comes up.
What mite be the problem and what mite be its solution?

---

### Post by jken146 on 2007-11-25
Do you get as far as the GRUB screen? If so can you boot into recovery mode?
What are your system specs?
Boot up the live-cd and do the check for CD defects to see if the CD burned right, if not re-burn the CD at the slowest speed and try to install again.

---

### Post by erfahren on 2007-11-25
that's the usplash you're talking about
see this thread: [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by erfahren on 2007-11-25
I guess you mean that there's no Ubuntu boot screen, don't you?

---

### Post by jnorthr on 2007-11-25
sounds like your installation may have been faulty.  Try to boot up with the live CD in the machine and see if it boots up that way. If so, then your hardware is probably working correctly. While running the live CD, try to start up a terminal session. Can't remember but i think it's under administration tab.  Then with terminal session running, type [COLOR="Red"]dmesg [/COLOR]and go to the bottom. You may be able to find some messages  from the kernel to give us a clue as to what's up.

---

### Post by diwas on 2007-11-26
Yes the loadin screen after the GRUB appears. Well Im checkin the links that u guys gave me. I will reboot to linux right now as Iam using XP currently.

---

### Post by diwas on 2007-11-26
I just checked out the instructions in the links and followed it in LINUX, but the problem is not solved. But i have some new information. After i select ubuntu from the GRUB menu, the screen becomes black completly...and then during that time, if i press Ctrl.+Alt+F1 i get the following message in the screen:

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/2b88b156-d53a-4686-9581-61fb64589d45)=da7(8,7)
kinit: trying to resume from /dev/disk/by-uuid/2b88b156-d53a-4686-9581-61fb64589d45
kinit: No resume image, doing normal boot...
	*Reading files needed to boot...			[OK]

Now its the normal boot afterwards...

I think this can help u to help me...
Thank u...plz reply.

---

### Post by diwas on 2007-11-26
Hey by the way..the numbers might not be exact coz i took the picture of the screen wid my cell fone...it took a bit low quality image...
anyways help me out!!!

---

### Post by erfahren on 2007-11-26
Is the problem that Gutsy will boot but just takes a long time and just shows a black screen while it's booting? If so, that sounds like the same problem I had after first installing.

I aplogize, it was awhile since I dealt with that and forgot exactly what I did to fix it.

I'm sure I set the resolution in the usplash.conf file, I think I may have done what was here as well (see the thread)l: [http://ubuntuforums.org/showpost.php?p=3835909&postcount=30](http://ubuntuforums.org/showpost.php?p=3835909&postcount=30)

Anyway, I did do one other thing which may have been what solved it. I installed the startupmanager package and with it I set the display resolution (for the booting process) to 640x480 and 8-bits.

With that it booted normally and the usplash showed up (and looked normal despite the low resolution).

---

### Post by diwas on 2007-11-27
My monitor supports 1024*768 maximum res. size...it was 1280*smthg i dont remember...i changed dat to 1024*768 in the uspash.conf...but it didnt work. I will try lowe resolution...lets see what happens.

---

### Post by diwas on 2007-11-28
Yes!! and it happened. I changed the resolution to 640*480 and yeah it worked. But just a tiny little help...the boot screen comes till file size checkin option appears...after that normal the black screen wid the white letters appears. What is the problem?

---

### Post by erfahren on 2007-11-28
> **diwas said:**
> ...the boot screen comes till file size checkin option appears...after that normal the black screen wid the white letters appears. What is the problem?
does that happen *everytime* you boot? Once in awhile (like every 30 boots) Ubuntu will automatically check the file system (like a "check disk").  - It has like a textual "progress indicator".

If that's not what you mean, I should say that I have a brief part when booting (after the usplash) where text comes up on my screen as well. It booted faster and more normally after I did the fix so I never worried much about it.

Does the boot process seem faster now?

I actually just did a reinstall of Gutsy last night (for unrelated reasons), and the only thing I did this time was correct the resolution in /etc/usplash.conf and did: sudo dpkg-reconfigure usplash
(as described here: [http://ubuntuforums.org/showpost.php?p=3835909&postcount=30](http://ubuntuforums.org/showpost.php?p=3835909&postcount=30) )
and that worked.

(I also installed the startupmanager, but the resolution was already set to 640x480 8-bit in it. I'm not sure if that changed anything.)

---

### Post by diwas on 2007-11-29
This happens everytime. The file check thing comes everytime i boot up ubuntu.
Actually yes the boot is faster this time...i think i know what caused the boot to be slow...while bootin...ubuntu wants to display the boot screen but since the predefined resolution's screen cannot accompany one's system, it waits for some command. And if no commands are given for a long time...it concludes that no other image is there in the system and goes out for a normal bootin process. 
May be this is causin the system to start up slowly.

---

### Post by mwacky on 2007-11-29
> **diwas said:**
> This happens everytime. The file check thing comes everytime i boot up ubuntu.
Actually yes the boot is faster this time...i think i know what caused the boot to be slow...while bootin...ubuntu wants to display the boot screen but since the predefined resolution's screen cannot accompany one's system, it waits for some command. And if no commands are given for a long time...it concludes that no other image is there in the system and goes out for a normal bootin process. 
May be this is causin the system to start up slowly.

Yeah, I can confirm this, the boot was super slow with no splash, after I corrected the problem by editing /etc/usplash.conf the boot was much faster.

---

