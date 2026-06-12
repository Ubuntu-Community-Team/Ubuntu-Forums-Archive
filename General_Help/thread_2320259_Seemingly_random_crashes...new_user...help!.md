---
title: "Seemingly random crashes...new user...help!"
date: 2016-04-12
forum: General Help
---

### Post by Allen_Hundley on 2016-04-12
I'm just a lowly web developer. I have been working in electrical engineering as a hobby for quite a while, but I'm just barely beginning to learn about the stuff in the middle of the hardware and the high level programming languages that I use every day. 

I own my own company, and recently bought into the open-source movement. All of our servers have been moved over to Debian, all of our machines are running Linux distros, and all of our company software is open-source. I'm just having problems with my personal machine after moving over to Ubuntu. 

I have Ubuntu 14.04 installed on this machine...a Dell Inspiron 3000 2-in-1. I don't mind that the accelerometer doesn't work, or the host of other missing features for 2-in-1s. Frankly, I don't really care or want those features. The problem that I'm having is that I can't rely on my computer anymore, and this makes work a huge problem. I've been dealing with this issue for a couple months. It's just annoying enough to seriously tick me off, but not quite enough to make me abandon my ideals on open-source. 

The problem is that at seemingly random intervals, the computer will seize. I'm not talking about a Unity crash, I'm talking about some kind of OS thing. My computer just freezes completely. I've done memory tests, and the RAM definitely isn't the problem. It almost seems like it's the CPU, but my temps are normal and I reloaded Windows temporarily to see if I could bring on a similar failure. 

Psensor says my CPU temp max is 54 degrees Celsius, but it also says that my processor fan is at over 5000 RPM, which I'm fairly certain it isn't unless it's talking about a completely silent fan that I'm not aware of. (And I've been inside this PC.) 

I'm not sure what logs I would need to provide, or if I need to give out any more information, but I'd be happy to help you help me. Haha. 

The only consistency in the crashes is their inconsistency. There seems to be no correlation between resource use, or program use that causes the crashes. Although, I think it might happen marginally more when I'm watching any kind of video. (This could just be my imagination though...I watch video a lot and it tends to annoy me more when it happens during a video.) 

Any help would greatly be appreciated...I'd like to be able to work at home reliably again.

---

### Post by mörgæs on 2016-04-12
Hi, welcome to the fora.

Which releases of Ubuntu have you tried?

---

### Post by TheFu on 2016-04-12
All the logs are in /var/log/ - look in there for errors and warnings. Use **grep**. The real issue is that the logs that show hardware failure are overwritten every boot, so if the system locks up, you'll have to boot from alternate media to view the logs on the HDD.  That means you'll have to mount that storage manually to see them.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

How much did the "bought into the open-source movement" cost? ;)

Do you have any real monitoring setup - munin, cacti or something like that?  I'd start there. Gathering facts and data is the beginning to understanding, right?  Engineers know this.  We don't want to guess, we want to KNOW.

I'd also setup logwatch, so that you'll be notified about small issues that don't cause a crash daily, but still should be corrected.  Logwatch will email daily reports, if you let it.

If the CPU fan isn't working, **any** effort will cause a lock up for almost any CPU. I have a fanless CPU in a chromebook, but haven't seen that CPU used in any Windows system.

How do you watch videos?  Video websites aren't all the same.  Flash is brutal on Linux systems with no GPU support for playback, but h.264 with HW support isn't.  I think Windows always uses HW support - adobe makes flash use it on Windows - but don't quote me about anything windows related. I'm just a 15 minute/day user of Windowz and haven't really touched it much since 2007.  If video is the issue, check that you are using the best/correct video drivers for your specific hardware.  Life is easier that way, for me. ;)

How is EE a hobby?  No degree?

---

### Post by Allen_Hundley on 2016-04-12
> **mörgæs said:**
> Hi, welcome to the fora.

Which releases of Ubuntu have you tried?

I tried 15.10 first, but it was slow and extremely buggy. I moved to the LTS release. 

[QUOTE=[COLOR=#000000]TheFu[/COLOR]][COLOR=#000000]All the logs are in /var/log/ - look in there for errors and warnings. Use [/COLOR][B]grep. The real issue is that the logs that show hardware failure are overwritten every boot, so if the system locks up, you'll have to boot from alternate media to view the logs on the HDD. That means you'll have to mount that storage manually to see them. [http://blog.jdpfu.com/2013/02/11/lin...-101-log-files]("http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files")

How much did the "bought into the open-source movement" cost? :wink:

Do you have any real monitoring setup - munin, cacti or something like that? I'd start there. Gathering facts and data is the beginning to understanding, right? Engineers know this. We don't want to guess, we want to KNOW.

I'd also setup logwatch, so that you'll be notified about small issues that don't cause a crash daily, but still should be corrected. Logwatch will email daily reports, if you let it.

If the CPU fan isn't working, **any** effort will cause a lock up for almost any CPU. I have a fanless CPU in a chromebook, but haven't seen that CPU used in any Windows system.

How do you watch videos? Video websites aren't all the same. Flash is brutal on Linux systems with no GPU support for playback, but h.264 with HW support isn't. I think Windows always uses HW support - adobe makes flash use it on Windows - but don't quote me about anything windows related. I'm just a 15 minute/day user of Windowz and haven't really touched it much since 2007. If video is the issue, check that you are using the best/correct video drivers for your specific hardware. Life is easier that way, for me. :wink:

How is EE a hobby? No degree?[/B][/QUOTE]

Buying into the Open Source movement actually cost me quite a lot in employee hours spent moving machines over, and the time it took employees to get used to Linux. I usually watch videos on Youtube in Chromium, I'm not sure exactly what codec that is, but I also watch Netflix on Chrome...I don't think that's Flash either. 

I'll check out the logs after work and check back here. 

EE is a hobby by being just a hobby. Haha. I printed out and bound all of the All About Circuits textbooks, you should check them out if they're not familiar. They're college level textbooks...the project I'm working on right now is pretty complex; a peer-to-peer HTTP server based on homemade radios.

---

### Post by mörgæs on 2016-04-13
It's worth the while to test 16.04 in a live boot for comparison.

---

### Post by Bucky Ball on 2016-04-13
> **mörgæs said:**
> It's worth the while to test 16.04 in a live boot for comparison.

I'd second this, particularly if the machine is reasonably new. 16.04 LTS is due for official release in nine or ten days (five years support), so if it works better for you, install and just keep updating/upgrading it.

(PS: Even though, unless I'm mistaken, that machine has 4Gb of RAM, with that Pentium processor it would fly on Xubuntu or, even better, [Xubuntu-core]("http://xubuntu.org/news/introducing-xubuntu-core/").)

---

### Post by dragonfly41 on 2016-04-13
Launch Applications > System Tools > System Monitor and look in Processes Tab.

Sort cpu% column so that highest loaded process is at top of list.

Next time you encounter a freeze in Chromium / Video look for the top process and click on usually named "chromium-browser --type= ... "  then click "End Process" to close frozen Chromium.

This avoids having to reboot but does not answer the root cause.
I get freezes from time to time (on a much older Dell) and I have to live with this although there are references I've found re: Chromium issues/bugs.

---

### Post by coldraven on 2016-04-13
On this six year old dual-core laptop running 15.10 Chrome is extremely buggy. Every time I close it there's a window beneath telling me that Chrome had crashed. Also get a "WebGL has stopped" message on one particular web-site. It's a bank so for security reasons I won't name it.
I mostly use Firefox but as I have it locked down some sites just will not work nicely and I'll fire up Chrome.

Edit: Apologies, I should have welcomed you to the forum. Consider yourself very much welcomed :)

---

### Post by Allen_Hundley on 2016-04-20
Sorry for the long wait. I installed 16.04. Every possible thing is better about this release...except I still have the same problem of random complete crashes. 

I'm still unsure what logs I need to be looking at...let alone what I'm looking for. I found this post...

[http://www.techsupportforum.com/forums/f64/solved-how-to-identify-cause-of-linux-system-freeze-556981.html](http://www.techsupportforum.com/forums/f64/solved-how-to-identify-cause-of-linux-system-freeze-556981.html)

It sounds pretty similar to my problem. Perhaps my problem is similar to his? His problem seemed to be with the CPU clock. I'll be messing with the BIOS until I figure out what else I can do, I don't really understand the process they used to diagnose the issue in that forum post.

---

### Post by QLee on 2016-04-21
> **Allen_Hundley said:**
> Sorry for the long wait. I installed 16.04. Every possible thing is better about this release...except I still have the same problem of random complete crashes. 

It sounds pretty similar to my problem. Perhaps my problem is similar to his? His problem seemed to be with the CPU clock. I'll be messing with the BIOS until I figure out what else I can do, I don't really understand the process they used to diagnose the issue in that forum post.

Your problem also seems similar to the problem with the so called "Bay Trail"processors. And when I look back at your posts, yes the N3530 in your system is one of the "Bay Trail"

The "Bay Trail" processors and MBs that have them embedded at the present time often need to disable some of the powersaving features in order to not have those random freezes. The kernel developers are working on the problem. [https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051) Some BIOS have a setting where you can disable the cstates and you could do it there if your MB will allow it. Remember what you have done so you can remove it once they deal with the problem.

If you encounter random freezes on a board that has one of those processors try adding intel_idle.max_cstate=1 to the GRUB line that boots your system. I wouldn't use it on any other family of processor. You can find a list at: [http://ark.intel.com/products/codename/55844/Bay-Trail](http://ark.intel.com/products/codename/55844/Bay-Trail)

For example: in the file /etc/default/grub  
change the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1" 

and then ```
sudo update-grub
```, reboot to use it. Test by opening a terminal and entering: ```
cat /sys/module/intel_idle/parameters/max_cstate
```, it will return a number.


It will make your system use a bit more power and thus likely generate a bit more heat but not a huge difference.

Remember what you have done so you can remove it once they deal with the problem. <----------

---

### Post by Allen_Hundley on 2016-05-01
It's been a while since I applied your solution, I wanted to see if it was truly fixed, or I was just on a crash-free streak (which would happen) I have not had a single crash since and can now rely on my computer again! Thanks. It definitely sucks more power on battery now, but that's fine...it's barely noticeable. 

Where can I find the progress on this bug so that I know when to switch my settings back? Thanks you so much!

---

### Post by Bucky Ball on 2016-05-01
Can't help with your current question, but please mark this thread as solved to help others as the original issue is fixed. See 'Thread Tools' at top-right of this page or second link in my signature. Thanks. ;)

---

### Post by QLee on 2016-05-01
> **Allen_Hundley said:**
> It's been a while since I applied your solution, I wanted to see if it was truly fixed, or I was just on a crash-free streak (which would happen) I have not had a single crash since and can now rely on my computer again! Thanks. It definitely sucks more power on battery now, but that's fine...it's barely noticeable. 

Where can I find the progress on this bug so that I know when to switch my settings back? Thanks you so much!


It's good that now your system works without freezing. It's only going to make a small difference because you've only turned off power saving features that come into play when the cores are not working hard. When they are busy it doesn't apply.

The simple answer is, it is the responsibility of the system administrator to monitor the situation and make the changes when necessary. In the case of a single user system the admin is you. 

I don't know of any place where "someone", (who?), is going to post an easy answer for us.

What I do to monitor, is to test if the boot parameter is still needed after each kernel upgrade on my "Bay Trail" system. You can do that at the GRUB line by entering "e" and edit out the parameter then boot, if it freezes then you just reboot to the GRUB line as it is and continue.

You could also add yourself to to the bug report, maybe the Ubuntu one on Launchpad (I think there is one) so you'd be able to keep up with progress. Or you could add to or monitor the bugzilla report or use a search engine to scan the Internet.

---

