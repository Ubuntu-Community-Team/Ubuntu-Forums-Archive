---
title: "Display errors after 13.04 security update"
date: 2013-05-16
forum: General Help
---

### Post by type5keith on 2013-05-16
On the day Raring Ringtail came out, I upgraded my 12.10 desktop to 13.04 and have been very pleased with it.  This morning I saw the notice that security updates were available popped up, so I allowed it to download and install these updates.  The updates required rebooting.  Upon reboot, the computer went into a low-res, 640x480 mode with my display defaulting to a 'laptop'. I have been unable to figure out why and how to return my settings back to their original 1920 x 1080 settings.  I just want to get my computer back to the way it was before these security updates were installed. Can anyone help me? 

Thanks in advance for your help.

---

### Post by philinux on 2013-05-16
Just done the update and rebooted. All ok here. Intel onboard graphics.

What gfx card have you got.

---

### Post by type5keith on 2013-05-16
Nvidia - I had been using the Nvidia proprietary drivers because of a some quirky intermittent issues... but for the most part it worked well with the standard ubuntu drivers.

---

### Post by grahammechanical on 2013-05-16
Have you tried going into System Settings>Software & Updates>Additional Drivers tab and experimenting with another video driver. The video driver may have been deactivated. The need for a reboot might indicate that there was a kernel update as part of the updates. That sometimes brings conflicts with installed video drivers that require a re-activation of a driver.

You also at the Grub menu select Advance Options for Ubuntu. It is a sub-menu that lets you select the previous kernel and boot into that.

Regards.

---

### Post by type5keith on 2013-05-16
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1087323_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1087323") 				 				 					 						 	[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"), I restarted with the previous kernel and that brought me up in 1920x1080, but Unity is missing.  Do you have any ideas on how to bring that back?

---

### Post by twk3 on 2013-05-16
Having the same problems this morning with my macbook after the latest kernel update. It took forever to load up, and when it did load it was in a poor resolution, and the unity bar wouldn't render properly. Just a solid gray block. After restarting a couple times it appears to be working.

My desktop wasn't coming back up after the update either. Just hung on startup. It's working on the previous kernel though.

---

### Post by type5keith on 2013-05-16
I have tried many things throughout the course of the day to try and fix my issue.  Booting to a previous kernel solved the resolution problem, but Unity failed to come up at all and I was unable to get Unity to start.  So I backed up my home data and am about to do a complete reinstall of 13.04.  I have to admit that I am disappointed that this security update has caused this much trouble.  It should not have.  My computer was working wonderfully until this. This would be totally unacceptable in a Microsoft or Apple OS. Why is this seemingly okay to Ubuntu users? Canonical what gives?

---

### Post by totogwada on 2013-05-16
> **type5keith said:**
> I have tried many things throughout the course of the day to try and fix my issue.  Booting to a previous kernel solved the resolution problem, but Unity failed to come up at all and I was unable to get Unity to start.  So I backed up my home data and am about to do a complete reinstall of 13.04.  I have to admit that I am disappointed that this security update has caused this much trouble.  It should not have.  My computer was working wonderfully until this. This would be totally unacceptable in a Microsoft or Apple OS. Why is this seemingly okay to Ubuntu users? Canonical what gives?


I am having the exact same problem on 13.04, since the update. Very frustrating.
i tried different graphics drivers (including the nouveau driver) from the "software & update > additional drivers". I have tried loading earlier versions through the Grub. I have tried recovery modes...

I think I am left with the re-install option, which is frustrating to do on my (prior to Ubuntu's security update) perfectly functioning work desktop.

i want to try installing the nvidia drivers again, but without unity I can't run firefox. The only way I was able to access the settings menu is through right click, change desktop image, all settings...

My graphics card is nvidia quadro 600

---

### Post by caughran on 2013-05-16
Same problem. /etc/X11/xorg.conf is not there.

---

### Post by totogwada on 2013-05-17
Hi have done a new install of 13.04, keeping my /home partition intact as it was in a different partition than /
I have the exact same problem: no unity!
Although now I can connect as a guest (which I am using right now).

Does that mean I need to backup and format everything, and re-do my partitions? I thought having a separate /home partition was the solution to do easy re-install without going through backups...
Anyway I will now backup, and do a real clean install.

In any case, I thought that information would maybe guide someone trying to help, as after a fresh format and OS install on the / partition, the problem persists.

Cheers

---

