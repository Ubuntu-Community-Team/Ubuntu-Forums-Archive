---
title: "Computer completely freezes for no apparent reason"
date: 2007-04-10
forum: General Help
---

### Post by modafokaxx on 2007-04-10
Hi
ok, I know this doesn't sound very precise, and it isn't really, which doesn't help to solve the problem.

I'm running Edgy Eft on a 1.35ghz athlon, with 384 mb of ram, GeForce 2 MX graphics card.

What happens is my computer simply freezes, completely and utterly. Everything gets stuck, including the mouse, and I can't restart gdm with ctrl+alt+backspace, I can't access virtual terminals with ctrl+alt+F1, and if there is sound running, it gets stuck too, in a very very annoying "uiiiiiiiiiiiiiiiii" noise.

I thought it was an issue with amarok's collection scanner at first, but since it has now happened when various software was open (opera alone, gaim and opera, just nautilus browsing some files after startup), I figure it's something deeper.
I read someone mentioning possible problems with the screensaver, so I disabled it, but no success.

I tried looking into /var/log/syslog and /var/log/dmesg but I can't see anything special (or maybe I don't know what to look for).

I know that one of my hard drives is probably going to die soon, so I've tried unmounting it right after startup so that it is not accessed. Maybe I should try removing it temporarily from fstab? or even physically unpluging it to see a real difference? But I know it's been failing for a while now, and the freezes are only recent..

I also had a power failure the other day, and my computer wouldn't reboot for a few minutes. Could it be related?

I can't recall installing something new lately that could be responsible for this..
I did mess up my home directory by chmoding all of it recursively in 777 (dumb move, can't even remember why I did it), but I think the freeze started happening earlier.

If anyone has ideas, logs to view or crash files to attach that they can think of, I'd gladly comply, any help would be much appreciated!

Cheers

axel

---

### Post by gjtoth on 2007-04-10
> **modafokaxx said:**
> Hi
ok, I know this doesn't sound very precise, and it isn't really, which doesn't help to solve the problem.

I'm running Edgy Eft on a 1.35ghz athlon, with 384 mb of ram, GeForce 2 MX graphics card.

What happens is my computer simply freezes, completely and utterly. Everything gets stuck, including the mouse, and I can't restart gdm with ctrl+alt+backspace, I can't access virtual terminals with ctrl+alt+F1, and if there is sound running, it gets stuck too, in a very very annoying "uiiiiiiiiiiiiiiiii" noise.

I thought it was an issue with amarok's collection scanner at first, but since it has now happened when various software was open (opera alone, gaim and opera, just nautilus browsing some files after startup), I figure it's something deeper.
I read someone mentioning possible problems with the screensaver, so I disabled it, but no success.

I tried looking into /var/log/syslog and /var/log/dmesg but I can't see anything special (or maybe I don't know what to look for).

I know that one of my hard drives is probably going to die soon, so I've tried unmounting it right after startup so that it is not accessed. Maybe I should try removing it temporarily from fstab? or even physically unpluging it to see a real difference? But I know it's been failing for a while now, and the freezes are only recent..

I also had a power failure the other day, and my computer wouldn't reboot for a few minutes. Could it be related?

I can't recall installing something new lately that could be responsible for this..
I did mess up my home directory by chmoding all of it recursively in 777 (dumb move, can't even remember why I did it), but I think the freeze started happening earlier.

If anyone has ideas, logs to view or crash files to attach that they can think of, I'd gladly comply, any help would be much appreciated!

Cheers

axel

did it happen after an update?

---

### Post by Jonne on 2007-04-10
Are you using the nvidia binary drivers by any chance?

---

### Post by john_spiral on 2007-04-10
Boot off the Ubuntu live CD, if it freezes while running off the LiveCD you have a hardware prob.

Also run the memtest off the CD rule out ram problems.

---

### Post by lhabjane on 2007-04-10
I'd say your mainboard is failing... Unplug all unnecessary hardware to see if something else is the problem

---

### Post by ae+ on 2007-04-10
> **Jonne said:**
> Are you using the nvidia binary drivers by any chance?

i have the exact same problems - and yes i am using the nvidia binary drivers....

i guess you are suggesting swap them for something else??

---

### Post by Jonne on 2007-04-10
I have random freezes too, and i've always suspected it to be the nvidia drivers. I need them because of Beryl ( ;) ), and the freezes are not so frequent to make me stop using them.

---

### Post by Gfy on 2007-11-12
In short:
My install of Ubuntu 7.10 freezes at random moments. (screen freeze and flashing caps lock led) 

After a fresh install, these were the big problems I had/have:
-Hibernate and sleep didn't work: fixed
-ctrl+alt+f1-f6 didn't work: fixed
-nm-applet can't connect to hidden networks
-switching nvidia binary drivers (trying to get the hibernate function to work) -> login screen was qwerty instead of azerty. One time it was azerty, special characters didn't work: I could not log in. fixed.
-I've been using Fusion, but after a half day my ram got full and the performance dropped enormously: disabled Fusion and it ran smooth.
-pyNeighborhood finds smb shares, but I can't always view them using the file manager because I can't always see the computers from workgroup. Still a problem.

I've been messing with all those things and now I have this problem:
Suddenly my screen freezes and the caps lock light on my laptop is flashing on and off. I see everything on my screen, but it isn't moving. Mouse and keyboard don't work.
It also happens when I'm not busy -> frozen screen saver.
Once, I tried connecting through a remote ssh connection, but it failed too.

Sometimes I can use Ubuntu the whole evening without a freeze and today I already had two freezes. At the beginning, the freezes didn't occur, or they where that rare I thought something else was the problem. But it is occurring more and more often and I think it didn't happen after I freshly installed Ubuntu.

I already switched back from the nvidia driver to the open source driver, but the freezes still occur.
As far as know, I can't find anything significantly in the logs.

This is the hardware of my laptop:
[Medion MD 41300]("http://www.google.com/search?client=opera&rls=en&q=Medion+MD+41300&sourceid=opera&ie=utf-8&oe=utf-8")

(Little) additional problem:
After I shut my laptop down (by pushing 4seconds on the power button), the icon of my external  ntfs disk appears twice on my desktop/locations list. When I dismount it, one icon disappears and the other stays. After a restart it is ok again.

Can somebody help me?


It's not a hardware problem. Windows works just fine ;)


edit:
I found my solution here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/51991/comments/48](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/51991/comments/48)
> Hani wrote on 2007-11-06: (permalink) 

I traced my problem to having bad sectors on an NTFS partition made slocate cause the total system freeze.
My problem went away after booting to XP and running chkdsk to fix the NTFS errors.
Another way to fix this is to add the NTFS mount path to the PRUNEPATH variable in /etc/updatedb.conf. This way slocate will never scan the NTFS folder.
This problem might not be what's causing all the freezes reported in this bug, but I thought I'd share my findings in case it helps someone in the same boat as I am.

I have a linked folder to an ntfs drive and that caused the crashing.
I added the dir to the prunepath variable, but the crashes still occured. Loading windows 3 times before Chkdsk did something at boot, but it eventually fixed my problem.

---

### Post by Endolith on 2007-11-29
This happens to me when memory and swap space are maxed out.  If you press Left Alt+SysRq+F it will kill the process using the most memory.

See [http://ubuntuforums.org/showthread.php?t=462488](http://ubuntuforums.org/showthread.php?t=462488) and [http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)

---

### Post by Gfy on 2007-12-11
> **Gfy]I found my solution here:[/QUOTE]

Nope, it wasn't a solution, but it took a while before the first hangups reoccured. They are not so frequent anymore. (max 2 times a day, but often just not)

[QUOTE=Endolith said:**
> This happens to me when memory and swap space are maxed out.  If you press Left Alt+SysRq+F it will kill the process using the most memory.

See [http://ubuntuforums.org/showthread.php?t=462488](http://ubuntuforums.org/showthread.php?t=462488) and [http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)

Thanks, I wil definitely try it next time.

---

### Post by Gfy on 2007-12-29
> **Endolith said:**
> This happens to me when memory and swap space are maxed out.  If you press Left Alt+SysRq+F it will kill the process using the most memory.

See [http://ubuntuforums.org/showthread.php?t=462488](http://ubuntuforums.org/showthread.php?t=462488) and [http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)

Neither Alt+SysRq+F nor 'Raising Skinny Elephants Is Utterly Boring' works.
Screen still frozen, mouse doesn't move and caps lock is flickering.

Now I've had a freeze while running the ubuntu live cd.

Could it be a signal that my harddisk is dieing?
badblocks gave nothing and the Windows check on my disk was fine too.

---

### Post by ari.maidana on 2008-03-07
I'm having the same problem and I think it's a motherboard issue :(

---

### Post by Gfy on 2008-03-11
My problem got solved by disabling hyperthreading in my bios.

It has to do something with the bios of my laptop. I read somewhere that there was an internal beta bios created by Medion that solved this problem, but it never got released.
I disabled the hyperthreading and never had a freeze since.

ah, found the link:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67110](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67110)

---

