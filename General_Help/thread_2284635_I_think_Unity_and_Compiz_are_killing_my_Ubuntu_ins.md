---
title: "I think Unity and Compiz are killing my Ubuntu install."
date: 2015-06-30
forum: General Help
---

### Post by bigsigh on 2015-06-30
This is an Intel quad core, 16gb ram on a supermicro board.
This install just runs Thunderbird and virtualbox vms, no day to day use at all, the display is always in standby, memory usage is not a problem at all.

Then;

Time:                    Fri Jun 26 10:26:00 2015 -0700
1 Min Load Avg:          34.22
5 Min Load Avg:          37.42
15 Min Load Avg:         41.67
Running/Total Processes: 5/637

root      1558 18.8  0.8 424140 139384 tty7    Ssl+ Jun11 4090:30  \_ /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1606  0.0  0.0 168304  3684 ?        Sl   Jun11   0:00  \_ lightdm --session-child 12 15
user      2218 61.6  2.3 2083780 384508 ?      Sl   Jun11 13394:20          |   \_ compiz

Now;

63.1  1991 user     compiz
29.8  4245 user     /usr/lib/virtualbox/VirtualBox --comment office30 --startvm 40661781-30e4-46b1-a2bb-7f4b859e3
27.4  1480 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
18.5  3079 user     /usr/lib/virtualbox/VirtualBox --comment server7 --startvm 91407402-559f-4d48-b6ee-5bd0151d7b
 6.0  2837 user     /usr/lib/virtualbox/VirtualBox --comment server9 --startvm 0106342b-fb73-4e79-a3a7-07cd35df1d

I've installed compiz settings manager and adjusted some settings based on posts on this forum and rebooted to no avail.

I'm wondering if the simplest option is to install lubuntu.

What I'd like to know is the process, if I apt-get install lubuntu (lxde) as the ubuntu install sets now, is it so simple as to install lxde, reboot, then select lxde and log back in?
Or is this going to destroy my installation with some config conflict?

Or, does anyone have any suggestions as to how to get compiz back into reality?

---

### Post by dino99 on 2015-07-01
the first place to glance at are the logs, you might have some usefull warnings/errors to dig around your issue.
changing DE can be a solution to know if 'unity' is the culprit (test gnome-shell for example)
switching to an other ubuntu (x/k/l) flavour will not resolved the problem, as it seems related to compiz (or some of its installed plugins, or some settings)
Compiz is badly maintained and only the default packages really works; you can test by purging the plugins one by one to find the faulty one; or reconfigure compiz

---

### Post by Bucky Ball on 2015-07-01
*Thread moved to **General Help**.*

How many VMs are you running at once and how much RAM is allocated for each? Installing another desktop environment to fix a breakage like this one will not achieve anything. This suddenly occurred by what you're saying. Not related.

If things were working fine previously, and from what I can gather they were, and something breaks, installing more stuff unless specifically instructed to because of a commonly known issue is not going to fix it, but may just compound the problem.

---

### Post by grahammechanical on 2015-07-01
Installing alternative desktops does complicate things and there is often a conflict with the configuration files. Furthermore, removing an alternative desktop completely is not so easy to do. I have tried it. I ended up re-installing as the quickest solution.

But do you need a complete desktop environment with all the utilities that come with it? Really? Perhaps you need a different window manager/compositor. From Ubuntu 14.04 onwards we can install gnome-session-flashback. Some like it because it has that old gnome 2 panel look. Where I find it useful is that we get two extra login sessions Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

I run the development version of Ubuntu (15.10) and if an update breaks Compiz or Unity I can login to the Metacity session and still get a working desktop. It is a handy fall back.

You might find it useful to run the Metacity session all the time. At least you will take Compiz out of the equation. And if the problem still persists? And gnome-session-flashback is easier to remove.

There are also other window managers that can be installed that do not use Compiz.

Regards.

---

### Post by bigsigh on 2015-07-01
I didn't realize lxde used compiz.

I really do appreciate the convenience of having a desktop environment for several reasons, and I say that having several active headless 14.04 servers running, the manuals never seem to have the exact syntax necessary for the commands and it's always a frustrating, time consuming struggle trying to figure out and search out the right way to write commands at the shell.

What's frustrating is that this is a bone 'stock' install, I do that one purpose, which is why I used lts, I didn't knowingly install any plugins.

I have spent some time searching through the logs, syslog, lightdm logs, kern, Xorg, gpu-manager, etc, for terms like compiz, lightdm, error and nothing returns that I can use to further troubleshoot.

Currently this is the machine's state.

65.6  1991 user     compiz
29.2  4245 user     /usr/lib/virtualbox/VirtualBox --comment office30 --startvm 40661781-30e4-46b1-a2bb-7f4b859e3de8 --no-startvm-er
26.2  1480 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
16.2  3079 user     /usr/lib/virtualbox/VirtualBox --comment server7 --startvm 91407402-559f-4d48-b6ee-5bd0151d7bbb --no-startvm-err
 5.4  2837 user     /usr/lib/virtualbox/VirtualBox --comment server9 --startvm 0106342b-fb73-4e79-a3a7-07cd35df1db6 --no-startvm-err
 4.6  3905 user     /usr/lib/virtualbox/VirtualBox --comment win7prosp1Don --startvm 2892963a-b582-4c0b-8e76-3de5227aed1d --no-start
 2.7  3362 user     /usr/lib/virtualbox/VirtualBox --comment server14 --startvm fcd1daf3-5149-4173-b33a-37b3301ec2e3 --no-startvm-er
 0.5   476 root     [kipmi0]
 0.4  2766 user     /usr/lib/virtualbox/VBoxSVC --auto-shutdown
 0.4 13289 user     /usr/lib/thunderbird/thunderbird

08:47:12 up 1 day, 20:25,  2 users,  load average: 3.15, 2.32, 1.98

            total       used       free     shared    buffers     cached
Mem:         16007       8518       7489         25        338       1619
-/+ buffers/cache:       6561       9446
Swap:         1999          0       1999

Filesystem      Size  Used Avail Use% Mounted on
/dev/md0        459G  276G  160G  64% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.9G  4.0K  7.9G   1% /dev
tmpfs           1.6G  1.4M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  556K  7.9G   1% /run/shm
none            100M   56K  100M   1% /run/user




@grahammechanical
gnome-session-flashback sounds very useful, I'll going to look into it.

---

### Post by bigsigh on 2015-07-01
Can I just turn off 3d? Is that a question that makes no sense because of the way the de is built?
If so, how?
I haven't any use for that level of graphics, my 12.04 default installs are stated as unity-2d-shell. 
I've been looking but haven't spotted anything of the like.

Even my desktop installs, I have 6 pieces of hardware that won't run unity on 14.04, and I had to fall back to 12.04 on them, this is Ubuntu's idea of an lts?
smh.

---

### Post by Bucky Ball on 2015-07-01
Depending on the specs of the six pieces of hardware, they may not be capable of running it. Did you try something lighter like Lubuntu or Xubuntu on them or straight in with Ubuntu, didn't work?

---

### Post by mattharris4 on 2015-07-03
> **grahammechanical said:**
>  But do you need a complete desktop environment with all the utilities that come with it? Really? Perhaps you need a different window manager/compositor. From Ubuntu 14.04 onwards we can install gnome-session-flashback. Some like it because it has that old gnome 2 panel look. Where I find it useful is that we get two extra login sessions Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

I run the development version of Ubuntu (15.10) and if an update breaks Compiz or Unity I can login to the Metacity session and still get a working desktop. It is a handy fall back.

You might find it useful to run the Metacity session all the time. At least you will take Compiz out of the equation. And if the problem still persists? And gnome-session-flashback is easier to remove.

There are also other window managers that can be installed that do not use Compiz.

Regards.

When I was running Edubuntu I liked Metacity better than Unity or Compiz (that OS comes with all three options).  Unity in particular was not the smoothest running DE for me but I was running Edubuntu 14.04 on an old Pentium 4 computer, running either Ubuntu or Edubuntu on a newer computer with a faster processor should give better results.  At some point I will install a Buntu (probably dual-boot with Win 10) on my replacement but I don't want to do that until I am comfortable that I won't need to use the computer warranty. 

Lubuntu works better on slower computers but with your equipment you should not have to go there (a mid line or better quad-core CPU with 16GB of RAM should run any Canonical OS -- actually that much RAM is unnecessary, I haven't ever topped three GB RAM usage in heavy use even with Edubuntu, even Windows 7 RAM usage tops out at about 3.5GB in heavy use).  If the exact specs of the computer (try the command ```
sudo lshw
```) can be posted we might be able to assist more but unless that CPU is an Atom, a Celeron or an older Pentium I don't see where a slow CPU is the problem here.

---

