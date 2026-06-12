---
title: "Wubi not safe?!"
date: 2008-05-11
forum: General Help
---

### Post by dreamsayer on 2008-05-11
After using wubi/Ubuntu last weekend fine, next day receive a busybox error. Magically that fixed. Got help on that.

This weekend after using wubi/Ubuntu yesterday most of the day, this morning I turned on my computer to boot Vista and I received a volsnap.sys error message. Luckily when I rebooted it went away.

Then I rebooted from Vista to wubi/Ubuntu, and was greeted with a error about gnome-settings manager!

I think this program to use Ubuntu without messing with partitions is cool and all, but IMHO I feel it is very risky and causing problems with the file system. People should be CAUTIOUS! 

I've never had any issues with Vista until using this program.

So it's bye bye Wubi! My recommendation to folks would be to use something like VirtualBox.
****

---

### Post by kk0sse54 on 2008-05-11
or just do a normal install and dual boot instead of using a virtual desktop that will become very very slow as you add/remove more and more programs and updates etc etc.

---

### Post by Thirtysixway on 2008-05-11
The only way I can think of wubi as being unsafe is if the power goes out or you hardboot while in Ubuntu, you can mess up your windows file system.

---

### Post by chorca on 2008-05-11
I'm not so sure you've got a Wubi issue there. Considering you're having issues in both linux and windows, that points to more hardware than software. I'm pretty sure the only change Wubi really makes is to add an entry into the boot.ini file and create a file on your windows drive while you're still in Windows, so there's nothing it's going to do that will break the filesystem. When you're booted to Ubuntu though, it is reading and writing to the loop file on the filesystem, so that's the only place that an issue could be had.

However, the fact that the problems go away when you reboot says that you should probably check your memory and look at the motherboard for bad caps. Usually intermittent issues like that are caused by hardware.

---

### Post by dreamsayer on 2008-05-11
> **chorca said:**
> I'm not so sure you've got a Wubi issue there. Considering you're having issues in both linux and windows, that points to more hardware than software. I'm pretty sure the only change Wubi really makes is to add an entry into the boot.ini file and create a file on your windows drive while you're still in Windows, so there's nothing it's going to do that will break the filesystem. When you're booted to Ubuntu though, it is reading and writing to the loop file on the filesystem, so that's the only place that an issue could be had.

However, the fact that the problems go away when you reboot says that you should probably check your memory and look at the motherboard for bad caps. Usually intermittent issues like that are caused by hardware.

Actually, I'm not having issues with Windows Vista. Never had. 

I think any issues I'm experiencing now are being caused by Wubi. Seeing all the other posts and reading today of a poor guys woe of loosing his XP leads me to believe otherwise. 

I think  as cool as you all think this technology is, at the same time you are being ignorant! How many PC's run some flavor of Windows in this world?;)

---

### Post by dreamsayer on 2008-05-11
> **Thirtysixway said:**
> The only way I can think of wubi as being unsafe is if the power goes out or you hardboot while in Ubuntu, you can mess up your windows file system.

Which I have never done BTW...

---

### Post by qamelian on 2008-05-11
> **dreamsayer said:**
> Actually, I'm not having issues with Windows Vista. Never had. 

I think any issues I'm experiencing now are being caused by Wubi. Seeing all the other posts and reading today of a poor guys woe of loosing his XP leads me to believe otherwise. 

I think  as cool as you all think this technology is, at the same time you are being ignorant! How many PC's run some flavor of Windows in this world?;)
No, you are the one displaying ignorance. You stated:
> This weekend after using wubi/Ubuntu yesterday most of the day, this morning I turned on my computer to boot Vista and I received a volsnap.sys error message. Luckily when I rebooted it went away.
This is almost definitely either a problem with Windows or a hardware fault. Considering that you also have experienced a problem in Ubuntu, I would lean toward impending hardware failure.

You really shouldn't be referring to people who are trying to help you as "ignorant". It's a good way to get otherwise helpful forum members to ignore you.

---

### Post by Danish989 on 2008-05-11
On a side note, I have a question of my own: how did you fix your BusyBox problem?

---

### Post by dreamsayer on 2008-05-11
> **Danish989 said:**
> On a side note, I have a question of my own: how did you fix your BusyBox problem?

For me it just fixed itself on it's own. But you may need to do a chkdsk /r from within Windows. There is another thread in this forum that may help: [http://ubuntuforums.org/showthread.php?t=784592]("http://ubuntuforums.org/showthread.php?t=784592")

---

### Post by dreamsayer on 2008-05-11
> **qamelian said:**
> No, you are the one displaying ignorance. You stated:

This is almost definitely either a problem with Windows or a hardware fault. Considering that you also have experienced a problem in Ubuntu, I would lean toward impending hardware failure.

You really shouldn't be referring to people who are trying to help you as "ignorant". It's a good way to get otherwise helpful forum members to ignore you.

Please, I do not mean to offend anyone..  I just feel that this technology has not been tested thoroughly enough to know any potential problems or implications that could arise. I seriously doubt I have any impending hardware failures. 

It's funny though how you are so quick to blame it on hardware or Windows. That is so typical... 

IMHO, I do not believe that using Wubi is "Completely safe!" It's more like: "Use at your own risk!"

---

### Post by chorca on 2008-05-12
It's not being quick to dismiss a certain software package as being the culprit, it's simple troubleshooting.

Yes, software needs to be tested in many environments to be sure that it works properly before it's put into production, and yes, there can be bugs in software. However, you yourself are jumping to the conclusion that Wubi is the problem, and that people should avoid it. If anything, avoiding a software which depends on user input to locate and resolve bugs will only worsen the problem, as there will be less people to test it.

Two people who have replied, myself and another, have both stated our opinions that it may be a hardware issue. This is stemming from simple troubleshooting techniques that nearly any technician would have.
The fact that Volsnap.sys was causing an issue indicates that either a driver or hardware is crashing or preventing it from starting properly. Wubi does not run resident at all in windows, therefore, it would be highly unlikely that Wubi would be the cause. The fact that Ubuntu also was experience an issue in the form of an application crash also gives a clue that there may be something wrong with hardware, as linux does not use the same software as windows, preventing it from being a software problem. Finally, the fact that an error such as that "went away" after a reboot makes it all the more suspicious that hardware is to blame.

Obviously this isn't an absolute resolution, as I don't have your machine in front of me to work on and find the root cause of the issue. All that's trying to be said is that we shouldn't dismiss a software if someone finds an issue, we need to learn more about the problem and try to find the cause to help improve the software as a whole.

---

### Post by Sockerdrickan on 2008-05-13
People shouldn't blame other software when Windows acts like, you guessed it, Windows.

---

### Post by ago on 2008-05-14
Mostly the issue is with unclean shutdown. That can happen if people turn off from ubuntu keeping the power button pressed for a few secs, or if you reboot just after starting ubuntu, maybe because you just remembered you had to go into windows instead of Ubuntu, and so on. 

See also [https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a](https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a)

---

### Post by jimv on 2008-05-14
Hmmm things get broken, files are missing, reboot fixes the issue....

Your hard drive is dying, and it has absolutely nothing to do with Windows or Ubuntu.  Get a replacement drive soon.

Have a nice day.

---

### Post by ago on 2008-05-14
> **jimv said:**
> Hmmm things get broken, files are missing, reboot fixes the issue....

Hardware can be one reason, but that is also often because the windows Dirty Flag is set. This flag is not cleared until you shutdown cleanly from windows. And wubi will refuse (for obvious reasons) to boot when the filesystem is marked as dirty. When booting and rebooting from within Windows the dirty flag is reset and that is why all of a sudden things start to work...

See also: 
[https://bugs.launchpad.net/lupin/+bug/226622](https://bugs.launchpad.net/lupin/+bug/226622)

---

### Post by jimv on 2008-05-14
I don't think I've ever had Windows fail to boot from shutting down improperly...and then start working again after shutting it down improperly a second time.

---

### Post by ago on 2008-05-14
> **jimv said:**
> I don't think I've ever had Windows fail to boot from shutting down improperly...and then start working again after shutting it down improperly a second time.

That is because windows can fix the dirty flag (and often it does so silently), while Ubuntu does not (yet) have the necessary tools to do that. Of course we could simply ignore the dirty flag, but I do not think it would be wise for us to do so. That is why you need to boot into windows first to get the situation sorted out. Sometimes booting/rebooting into windows is sufficient, in other cases you need to run chkdsk /r. We will add a clearer error message though (see bug above), and in the long term we will work on having native chkdsk tools. Of course you would not have any such issue if you used a Ubuntu installation to dedicated partition.

---

### Post by jimv on 2008-05-14
> **ago said:**
> That is because windows can fix the dirty flag (and often it does so silently), while Ubuntu does not (yet) have the necessary tools to do that. Of course we could simply ignore the dirty flag, but I do not think it would be wise for us to do so. That is why you need to boot into windows first to get the situation sorted out. Sometimes booting/rebooting into windows is sufficient, in other cases you need to run chkdsk /r. We will add a clearer error message though (see bug above), and in the long term we will work on having native chkdsk tools. Of course you would not have any such issue if you used a Ubuntu installation to dedicated partition.

I'm talking about Windows failing to boot, not Ubuntu.  I thought the OP said that Windows didn't boot initially.

---

### Post by ago on 2008-05-14
> **jimv said:**
> I'm talking about Windows failing to boot, not Ubuntu.  I thought the OP said that Windows didn't boot initially.

That depends on what files get inaccessible because of fs corruption. If it is some file involved in the boot process it can happen that windows cannot boot. In such cases it is necessary to run chkdsk /r from the windows CD or similar recovery CD.

---

### Post by dazift on 2008-05-15
i have used wubi maybe 10 times already with no serious errors, the only thing that i encountered is that if u start windows and end it without shutting down u get an error when u try to boot ubuntu

---

### Post by ago on 2008-05-16
> **dazift said:**
> i have used wubi maybe 10 times already with no serious errors, the only thing that i encountered is that if u start windows and end it without shutting down u get an error when u try to boot ubuntu

Which is expected since in that case windows will turn the dirty flag on for the file system  and we do not boot in such cases.

---

### Post by Crossroads on 2008-05-16
> **ago said:**
> Mostly the issue is with unclean shutdown. That can happen if people turn off from ubuntu keeping the power button pressed for a few secs, or if you reboot just after starting ubuntu, maybe because you just remembered you had to go into windows instead of Ubuntu, and so on. 

See also [https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a](https://wiki.ubuntu.com/WubiGuide#head-ba8242d659938a2a8293e4b77c8733eae7334a0a)

Understood. For me, some apps running in Windows sometimes lose track of my keyboard so my only option is to reboot by holding the power button down for 5 seconds. So far, touch wood, I have not had NTFS corruption problems.

Now, if the same problem happened when running Ubuntu (installed using Wubi):
- would the NTFS corruption be likely to occur?
- and would a chkdsk /r sort it out?

Presumably after a chkdsk /r some files may be lost, possibly the  Wubi virtual hard disk file too.

[Apologies if I have misunderstood, as i have not used Wubi yet, i'm just exploring]

---

### Post by ago on 2008-05-16
Hard rebooting is a bit like a russian roulette. In most cases all is good and it is only the dirty flag to be sorted out. So that you will not even notice it (when you boot into windows the dirty flag is cleaned out automatically), in other cases chkdsk /r can sort things out, only in rare circumstances you may have data loss and/or files "vanishing".

Whether you hard reboot from windows or from Ubuntu it does not change matters. 

There are 2 differences though on how things are handled AFTER the hard reboot event. 

Windows is capable of fixing a corrupted filesystem and clean a dirty flag(and often does so automatically so that people do not even notice). We do not have yet this capabilities in Linux (when it comes to windows filesystems), so that you have to boot into windows first to sort things out.

Second difference is that there is a distinction between data loss and journal loss (the latter being far more annoying). Journal loss in the windows filesystem is extremely difficult, even if data loss can happen. Provided you have an intact journal you can bring the filesystem to a consistent state even if you may lose the very latest writes. 

But data loss in windows might imply a journal loss in a nested filesystem (Ubuntu), since a journal in a nested filesystem is treated as data in the host filesystem. So it might happen that after a hard reboot ntfs gets fixed but the ubuntu filesystem does not. This is not a deficiency of Ubuntu, it is an intrinsic problem of a nested filesystem setup. We have minimized such dangers by reducing cache times, but it is unlikely we can eliminate them alltogether.

---

### Post by Crossroads on 2008-05-16
ago,
Thank you - good, clear explanation

---

