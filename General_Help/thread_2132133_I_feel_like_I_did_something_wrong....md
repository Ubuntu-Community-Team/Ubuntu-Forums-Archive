---
title: "I feel like I did something wrong..."
date: 2013-04-03
forum: General Help
---

### Post by TAChimpo on 2013-04-03
About three years ago I decided to start using Ubuntu when I had to get a Linux+ cert for my job. Shortly after I ended up changing jobs and ended up sharing a home/work laptop and was forced to use Windows due to some annoying company policies that no longer exist. Because of just me being lazy, I've just used Windows since on other computers as well. So I know ubuntu/linux somwhat, but it's been a while. 

Naturally once I was able to, I couldn't wait to switch back to Ubuntu. So I re-backuped all of my important info/data and decided to just do a clean install of Ubuntu 12.10. The first install didn't seem to go to well, as each time it would hang on startup. I have two HDD's (a 250g SSD and a 2tb HDD), so I pulled my HDD and installed only on the SSD. It all installed fine, but it takes a good 1-2 minutes to boot compared to the 5-6 seconds it took Windows. Once I am able to log in, it is very sluggish. An example of this would be Steam taking a good 45-75 seconds to start. So I feel as though I did something wrong, yet again...

That being said, in Windows I had my two HDD's set so that I had the OS installed on the SSD and most other programs installed on the HDD. I know there is a simple way to set up the hard drives like that in Ubuntu, but it's been a while and I can not remember how.

So... what am I doing wrong in the install that's causing all of these errors? Is it something I'm not doing after the install? Or am I installing incorrectly? And how do I setup the two HDD's properly? Since all my data is backed up I don't mind doing another clean install if it will help.

I'm running a Asus G75V Laptop, if that matters/helps. 

Thanks in advance for the help!

---

### Post by d0006 on 2013-04-04
I have never heard of a 2TB internal HDD for a laptop.  Is this an external drive?  This maybe part of the delay in booting.
You can partition the SDD to contain the "/ ", "/boot", and swap partitions. I use 30GB (more than enough) for the "/ " partion, 4GB for the "/boot" partition and the swap partition should be 1.2 - 2 times as big as your RAM.   The HDD can contain the "/home" partition.

What filesystem are you using?  If the system will be Linux only I recommend ext4.  You may also want to use GPT partitioning.  If you do you should search how to make a "BOOT-BIOS" partition.

---

### Post by TAChimpo on 2013-04-04
You're right about the 2tb, that was a typo and it is actually 1tb and it is OK internal. The delay is there even if the 2nd HDD is removed.

I never thought about making the 1tb into /home... I knew it was a simple fix lol. 

I'll reinstall in the morning with these settings and be sure its ext4 (99% sure it is). Hopefully all issues will be gone, but I'll post back either way

---

### Post by Ice On Fire on 2013-04-04
Please keep us updated - would be nice to know if this solves the issue.

---

### Post by TAChimpo on 2013-04-04
So after a few hiccups, it appears as though most things are now working properly. 

I reinstalled Ubuntu 12.10 with the / , /boot , and swap partitions on the SSD and /home on the HDD. Everything was ext4 as suggested. After rebooting I was then met with an error: File not found followed by a "grub rescue>". So I booted into live, ran Boot Repair and rebooted again. After the reboot it still took a good 2 minutes to boot. After login I ran a software update and did a sudo apt-get update and a reboot. This time the boot time was about 45 seconds, so better but still not great. 

After that I dug around and found that there was no instaled nvidia driver, so I installed the newest and rebooted. Sure enough, it booted in about 10 seconds and the computer doesn't seem to be sluggish like before.

Not sure why that was the problem, but it seemed to have fixed it.

However, I started running into a new problem after install (even before installing the nvidia driver) which is upon login I'm met with an error. "System program problem detected; Do you want to report the problem now?" If I report or close I'm met with "Sorry, Ubuntu 12.10 has experienced an internal error." 

It does this everytime I log in. Thoughts on what may be causing this or how to find out?

---

### Post by pfeiffep on 2013-04-04
I had problems with [COLOR=#000000][FONT=Ubuntu Mono] Linux 3.5.0-26-generic x86_64, when I reverted to -24-generic the [/FONT][/COLOR]> [COLOR=#000000]Sorry, Ubuntu 12.10 has experienced an internal error." [/COLOR] disappeared. My system was HP tower so this solution might not apply to you

---

### Post by d0006 on 2013-04-04
I read in another thread that it may not be a good idea to put the swap partition on the SDD. Sorry.
This thread may have some info on your error messages: [http://ubuntuforums.org/showthread.php?t=2127997](http://ubuntuforums.org/showthread.php?t=2127997)
There is a new version that may correct your problem.

---

