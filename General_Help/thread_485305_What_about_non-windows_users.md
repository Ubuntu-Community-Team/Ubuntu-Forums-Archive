---
title: "What about non-windows users?"
date: 2007-06-26
forum: General Help
---

### Post by happysmileman on 2007-06-26
I thought this was a good idea, until I saw that it would be made an official installer for Ubuntu and I can see many problems...

First of all, and most importantly, it basically encourages the belief that Windows is needed to do everything, and treats Linux just like an extra program installed, and even makes it harder to perform a **proper** install (Yes, I am calling this a half-assed install)

Secondly, it's slower... you can say it's not going to be slower unless your drive is fragmented but it quite obviously will be slower... And everyone I know who can de-fragment a drive can also successfully install Ubuntu as it is... Everyone else will let their drives fragment, Linux will become as slow as Windows and they will switch back...

Thirdly, is this eventually going to surpass proper installs? I don't want to come onto the forums here with a problem about installing and just receive the answer "Use Windows XP to install with Wubi"...

Fourthly, what about the fact that Ubuntu is about helping people make the transition FROM Windows TO Linux, it's not about making Linux part of Windows and having it deleted whenever you get a Windows virus (Viruses I've gotten on Windows XP: 4, Viruses I've gotten on Linux: 0)...

I use Ubuntu because it's easier and seems to be the best distro out there... If it eventually becomes dependent on Windows, or the encouraged method of install is to make it part of Windows, while telling people it's **probably** as fast as long as you de-fragment your hard-drive regularly (which no-one who needs a Windows installer does)

PS: I'd actually like responses to these points, and hopefully I've misunderstood... but a simple "You're wrong" reply or a link to an FAQ isn't a proper response

---

### Post by Epilonsama on 2007-06-26
Sir, you are wrong in one thing, this isn't going to be the only install method for Ubuntu,  Wubi is going to be a method for new ppl to linux like me to test Ubuntu and see if they like it, like me, and they can later on transform the loopmount partition into a real one.

---

### Post by acowboydave on 2007-06-26
Hello, you made some points. But I'm a new person to the Linux system and new to Windows. Does it matter how we get to our destination as long as we get there. To me Wubi opened another path for anyone to use Linux. It has it's problems but they are being solved. If it wasn't for Wubi I wouldn't be writing this in Ubuntu.

---

### Post by ago on 2007-06-26
> **happysmileman said:**
> First of all, and most importantly, it basically encourages the belief that Windows is needed to do everything
Nope, lupin (the back-end) does not depend on windows. In fact I do not even have windows and do most of my tests on Linux. Wubi is only a frontend for windows. We have already a linux frontend called lubi which can install Ubuntu within a Linux partition, and hopefully will have a mac frontend soon. 

> and treats Linux just like an extra program installed
Nope you get a complete dual boot system, not a windows application. The fact that it is as easy to install as any other application does not mean that it requires windows to run once installed... 

> and even makes it harder to perform a **proper** install
Hardly so, once you have a partition ready you can use lvpm to migrate. Wubi postpones the partitioning/bootloader hurdle to the moment when the user has accumulated enough goodwill, which, IMO, is a far better approach... Ever tried to convince someone to install Linux just to see the discussion dropped as soon as you mention the word "partitioning"? Well that is exactly where the discussion ends for 80% of the people out there.

> Secondly, it's slower...
Most people will not notice the difference, even with a fragmented disk. Yeah maybe it would be even faster if they defragmented, and even faster if they had a real partition for it. So what? People that would not bother to defragment would probably not bother to change their partitions either. Hence a slightly slower Ubuntu is far better than no Ubuntu at all. And since disk fragmentation is only one of the reasons why Windows gets slower over time, Ubuntu would steel feel quite faster in most cases...  Finally if you wanted to have people to try out Ubuntu before partitioning what other alternatives are out there exactly? Live CD? VM? Want to talk to me about performance?

> Thirdly, is this eventually going to surpass proper installs?
It's a different installation, targeting people that have no idea about what a partition is. Which is about 95% of the users out there. It does not replace the other installations, so if you are happy with ISO burning and partitioning you will always be able to get things done with the usual tools, but there is no reason to force those tools to other users. That said the Live CD installer will still be the recommended installation method. Wubi will be made available as a sort of short-term installation. 

> "Use Windows XP to install with Wubi"...
Yep most people do have an OS already, and I do not see the problem in using that OS to launch a simplified installer. But maybe you prefer to explain to people how to change the BIOS in order to boot the CD-Rom...

> Fourthly, what about the fact that Ubuntu is about helping people make the transition FROM Windows TO Linux, it's not about making Linux part of Windows

Try this: install Ubuntu with Wubi, then delete C:\WINDOWS\*, then try to boot Ubuntu... Guess what? it will boot. So much for windows dependency. 

Yep our image file is hosted inside ntfs, but it could just as well be hosted inside ext3, reiser or any other fs. That's about the only dependency you get and if that is not bearable you can migrate the virtual disk to a real partition and nuke any trace of windows. 

>  and having it deleted whenever you get a Windows virus (Viruses I've gotten on Windows XP: 4, Viruses I've gotten on Linux: 0)...
True, a windows virus could delete the wubi folder, but it could just as well zero a partition, so you are not much safer by running Linux in a dedicated partition as opposed to running Linux within a windows file.

---

### Post by ago on 2007-06-28
I have "reorganized" my thoughts on the topic in my own blog: [http://agolb.blogspot.com/2007/06/why-wubi-is-important-for-linux.html](http://agolb.blogspot.com/2007/06/why-wubi-is-important-for-linux.html)

---

### Post by Lord Illidan on 2007-06-28
I've never used Wubi, but I remember from my days as a noob, that I never had partitioned a harddrive in my life before I installed Linux. The very idea was alien to me..

---

### Post by Tahi_Kiwi on 2007-06-28
I'm using the free VMPlayer 2.0 running on Windows XP (host) to run various Linux distros (guests). This means you need plenty of RAM for both Windows and the distro.

The reality for many people is that we still need Windows, and we can run Linux or Unix.

I'm shy to try out wubi because of reported performance and crashing problems. I wonder how representative wubi problems reported on this forum are when compared to the number of wubi users out there?

---

### Post by ago on 2007-06-28
> **Tahi_Kiwi said:**
> I'm shy to try out wubi because of reported performance and crashing problems. I wonder how representative wubi problems reported on this forum are when compared to the number of wubi users out there?

We have about 100000 users at the moment. Most of the crashes where reported for previous versions and should be fixed. Performance issues are very rare and usually only affect people with < 300MB memory and/or esoteric sata controllers. The only thing to avoid are hard reboots, for the rest you should be fine. If you do not like it you can simply uninstall it.

---

### Post by Henrik on 2007-06-29
> **happysmileman said:**
> Secondly, it's slower... you can say it's not going to be slower unless your drive is fragmented but it quite obviously will be slower...

It will be a bit slower than a full install but it will be faster than any other alternatives, including: Live CD, Vmware/virtualbox install, Qemu, using XP or using Vista ;)

> Thirdly, is this eventually going to surpass proper installs?No, it won't.

> Fourthly, what about the fact that Ubuntu is about helping people make the transition FROM Windows TO LinuxUbuntu is about promoting Free Software, about making computing accessible to to more people regardless of social situation, language, disability, etc. Moving people from Windows is really just a side effect of this goal. Wubi is a great way to introduce software freedom to more people.

---

### Post by happysmileman on 2007-06-29
I suppose I misunderstood a few things about it... Thanks for answering my questions...

---

