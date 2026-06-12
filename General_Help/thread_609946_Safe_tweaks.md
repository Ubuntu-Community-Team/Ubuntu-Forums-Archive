---
title: "Safe tweaks?"
date: 2007-11-11
forum: General Help
---

### Post by Chriswaterguy on 2007-11-11
There are many things I like about Linux, and about Ubuntu, but one thing I find frustrating: there are many modifications that I would like to make, but I don't know if they're safe, and I can't find anything about tweaks in the official or semi-official (wiki) documentation. Just blogs and forum posts, and sometimes they don't give good advice, nor support when things stuff up. 

If it's a matter of changing a setting in a GUI, I feel fairly safe, e.g. turning off desktop effects. 

However, for a lot of tweaks, (editing the /etc/hosts file, reprofiling bootup, setting the system to recognize the dual core processor, [tweaking for broadband]("http://ubuntuforums.org/showthread.php?t=251509&highlight=faster+tweaks")) the user has to use *sudo *and fiddle with system files. I don't know which of the tweaks are actually safe, and I don't know whether they're applicable to the version I'm running. 

I did some tweaking when I was running Xubuntu 7.04 (reprofiling boot and recognizing dual core), so I know they can work, but I also had found my install of Xubuntu very buggy, and I don't know if the tweaking contributed to it. I want to find out more before I start doing anything that might destabilize my current install of Ubuntu 7.10. 

I looked up tweaks in the [Community Ubuntu Documentation]("https://help.ubuntu.com/community/") wiki, but there's no page dealing with this (just assorted mentions of tweaks). I'd love to see a page dedicated to safe tweaks, and would contribute to it myself as I'm able. 

Have I missed something?

---

### Post by Chriswaterguy on 2007-11-12
So... should I conclude that no tweaks are endorsed by the Ubuntu development team? For safe use should we not tweak at all? 

Puzzled.

---

### Post by roderick on 2007-11-12
Generally, unless you know what you are doing, or are comfortable with recovering a failed system, you really shouldn't mess with the "SANE" defaults that the packagers/developers have built into your system.

If you try some performance tweak, without understanding the potential conflicts, then you could cause more damage down the road. Imagine a fix that works now, but a new core update conflicts with this tweak, and renders your system unusable. You think it was the fault of the update and blame the packagers...

So, unless you want to be a "mechanic", I suggest you leave fine tuning the engine to the professionals. If you truly want to be able to tweak a system, you should look into some of the Linux Administration courses, or perhaps one of the Hacking Ubuntu books which can guide you through making changes and provide you the proper warnings. In any case, read more about Linux System Administration, and file systems and packaging before you make any rash changes :)

Cheers.

---

### Post by mcduck on 2007-11-13
It's hard to say, without actually knowing what exactly you are planning to do. Some things are safe, some are not and nobody can really say that _everything_ people might decide to do with the setting files is absolutely safe.

But if you do a bit of research about what are you actually doing, and create a backup of any setting file before editing the original, you should be quite safe tweaking your system.

For those things you suggested, editing the hosts file is quite safe, as long as you don't remove the localhost entry. At worst your network may fail to work, but that's why I said you should make backups of files before editing them. I really don't know what you mean with "reprofiling bootup" so I can't say anything about that. As long as you are running one of the last 3 Ubuntu releases all multi-CPU/multi-core systems should be supported out-of-the-box, no need for any tweaks there. Tweaking network settings is as safe as the hosts-file. In worst case your network fails to work, but if you have a backup of the original file you can just copy it back and everything is fine again.

There are so many things that can be tweaked and changed in Linux, that the only possible thing to say about their safety is that everything you do you do with your own responsibility, and as long as you know what you are doing and use some common sense you should be fine.

And always make backups. From setting files you are going to change, and from all important files you ave on your machine. At least you should have backups of any important files anyway.

---

### Post by bingoUV on 2007-11-13
Just backup the configuration file you are editing, and you should be fine. At worst, the system will be unbootable. Then, just boot from a live CD, and restore the file from backup.

Reboot after any dangerous changes. Not to make it come into effect, but to ensure that these changes do not mess up the boot process.

best of luck

---

