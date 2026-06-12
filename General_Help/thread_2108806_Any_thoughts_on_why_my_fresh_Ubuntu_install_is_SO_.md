---
title: "Any thoughts on why my fresh Ubuntu install is SO SLOW?"
date: 2013-01-25
forum: General Help
---

### Post by Sheepish on 2013-01-25
Hi guys, its been a while coming, 6 years in fact, but I've finally made the full switch to Ubuntu after toying with it for a long time to get the windows software I needed working through wine (all that seems to have been sorted now!)

In the past Ubuntu was as rapid as can be, but this new install of the latest version on my laptop seems to very numb.

The main issue is the system is stable, but very slow to respond. If I click my home folder I have to wait for up to six seconds for it to open. The same problem for applications, obviously it can vary for apps.

I have always ditched Ubuntu's new window manager and gone with Gnome, which is just my preference. However I have tried this with XFCE, KDE and LXDE too, with the same issues. Opening multiple apps can take minutes. 

I'm used to double clicking an icon and it opening  instantly on the second click, even in Windows 7.

I'm thinking that maybe its a configuration or driver issue, maybe even a duff image, but I always check the media before install. I thought it may be the driver for the graphics chipset, but 3d performance is better than windows in some of my steam games and the eye candy in Gnome 3 is silky smooth.

**I'm running an 2nd gen i3 @ 2.2GHz, 8GB RAM, Intel HD3000 graphics, 500GB HDD**

On thing I have done differently is that I asked for my home folder to be encrypted, I shouldn't see this being the problem as I was under the impression that the encryption takes place on mount/unmount and I'm not too bothered about boot time.

I've also uninstalled Ubuntu and reinstalled W7 and it's perfectly fine, as I was worried about the health of the drive.

Lastly, again with the HDD, are there certain filesystems that are faster than others? I just used the guided installation to do it for me.

I'm a bit lost really, finally Ubuntu can do everything I need it to and it's suddenly slow.

Your thoughts, advice and input would be appreciated.

Many thanks,

Joe

---

### Post by jatos on 2013-01-25
My thoughts: because it seems to someone or some of the people on the dev team are doing a really shoddy job.

I would make sure you get rid of Ubuntu's native package manager and use apt-get or install Synaptic

I had a similar issue on my 3GHZ Core 2/3GB Ram/512 graphics setup, and doing the above sorted a lot of issues out very quickly!

On a sidenote, the lag caused by the package manager is something the Ubuntu devs must sort if Ubuntu is to grow!

---

### Post by TheFu on 2013-01-25
If is isn't some hardware going bad ... which it could still be, then until you check the log files, there is no way to know what the issue is.
Look in 
* dmesg
* syslog and 
* all the log files under /var/log/
for errors and warnings.

I'd check the process table to see what was using all the RAM and all the CPU too.

I've seen where the network setup removed l0 - the loopback device - and that cause extreme slowdowns too.

Without facts and data, we are shooting blind.

---

### Post by Sheepish on 2013-01-25
Thanks for the fast reply my friend. That really is something I'd never considered. I noticed that it was very slow when installing software, but I just figured that to be down to the fact that I have to disable the N functionality of my wireless card and router and it was causing slowdown. But using it now, I can tell that its taking a chunk of my resources. 

If I can find a way to remove Ubuntu Software Centre do you think it'll help that much? I'm pretty well versed with Synaptic/Apt-get so I have no issues with installing that way.

I've had and Ubuntu Server running the last few years on a 1999(I think) Dell Dimension with 512MB RAM, and that would out drag this setup any day!

---

### Post by thnewguy on 2013-01-25
Sounds to me like a driver issue. Running with an encrypted home folder should only slow down access to your own files, not the system's files (as happens when you launch an application) and then the slow down is only about 10%. The Software Centre isn't the problem unless you always have it open. The Software Centre can only slow you down when you're using it, but it sounds like your machine is always slow.

My guess is it is a driver problem, that will kill performance in a big hurry. Check to see if there are updated drivers for your version of Ubuntu. I found 12.10 was a lot slower on my hardware compared to 12.04 and it seems to be an X/driver issue.

Another thing to check is to run the "top" command and see what is gobbling up all your CPU. Alo check the "wa" (wait time) when you run top, it may be that your Os is waiting on slow read times for some reason.

File systems can be a big bottle neck for IO, but ext3/ext4 are usually fine. You probably would only notice slow downs if you were using Btrfs.

---

### Post by Double.J on 2013-01-25
> **thnewguy said:**
>  You probably would only notice slow downs if you were using Btrfs.

Exactly where I was going... Not sure what version/kernel support there is for BTRFS  currently, but I had the exact same issue installing OpenSUSE12.2 before the update. It was totally unusable. It's been fine for the last several months though, but likeI say I'm not sure of the versions involved here. 

In terms of the hardware, there can't be a spec issue; I have it on old netbook; 1.6 atom n270 2gb ram, intel gma950' 

Recommend checking the disk for errors? It definitely sounds like slow disk access?

---

### Post by gifford on 2013-01-25
Synaptic is always faster for installing. As for the slowness in opening folders, I assume that you have already changed your mouse and touchpad settings to speed them up. What version of Ubuntu are you using? 12.04 LTS or 12.10? Running Top will show what is taking up your system resources and might help pinpoint some problems.

---

### Post by Sheepish on 2013-01-25
Thanks again for the great replies, so I've checked all my logs, nothing untoward there apart from a compiler crash last night that was caused by this mysterious slowdown. I keep USC closed most of the time, in fact I hardly use it, but it seemed a legitimate suggestion. 

My running processes don't reach over 1% and a spike of 30% when launching an app. RAM wise, Thunderbird is using the most at 3.9% In windows, when launching an app it uses as much as possible to carry out the task as fast as possible, 30% seems off, but again it could be a Linux thing.

Even with these low usages, its still painfully slow. I've checked for driver updates and they're all the current versions. I've just ran Fedora (yes, I know! Shh) with Gnome 3 on the Laptop and it's running as I'd expect, damn fast.

I think its looking like a driver issue, maybe an incorrect driver rather than out of date. Is there a way to rescan my hardware?

---

### Post by Sheepish on 2013-01-25
**Quick update:** I've just tested the HDD and its passed all the tests and the file system is Ext4 which is what I'd have chosen if I'd have done it manually.

I've heard talk of people updating kernels and it 'solving all their problems' on SUSE forums, but as an IT Technician who primarily works with Windows and meddles with Linux in my spare time, I wouldn't know where to start with this.

---

### Post by TheFu on 2013-01-26
> **Sheepish said:**
> **Quick update:** I've just tested the HDD and its passed all the tests and the file system is Ext4 which is what I'd have chosen if I'd have done it manually.

I've heard talk of people updating kernels and it 'solving all their problems' on SUSE forums, but as an IT Technician who primarily works with Windows and meddles with Linux in my spare time, I wouldn't know where to start with this.

On Windows, you use the Event Viewer to see issues, right?
On Linux, you use the log files in /var/log/ to see issues.

Look for warning and errors in those files. Seriously, the cause of the issue is there, I'm 99% certain.

$ sudo egrep -i 'error|warning' /var/log/*

How hard is that?
To learn about sudo or egrep commands, use **man {command}**.
Also check **dmesg** for warnings and errors.  
$ [B]dmesg | egrep -i 'error|warning'
[/B]Simple.

---

### Post by Sheepish on 2013-01-26
Thanks for the commands! I've just found an issue with thunderbird, following this advice :) 

I will use them in future a great deal I'd imagine.

Ok, I seem to have fixed this. For any other folks that have similar issues I've done the following;

[B]Reinstalled Ubuntu (so I know its not some settings I've messed up, and that its still slow) Chose not to encrypt my HDD from the partition manager, but to encrypt my home folder on the subsequent steps of the install.

Switched to Cinnamon instead of Unity (this helped a great deal)

Diabled a load of bloat processes that I have no need for.

Installed Preload, a pretty nifty bit of kit that does a good job of reading your mind.

Updated everything I could.

Found Thunderbird doing some weird recurring error jobby and writing to the log A LOT.
[/B]
It seems to be running a lot better, not as fast as say Debian + XFCE, but a massive improvement!

A big thank you to everyone that has had some input, I've always said Ubuntu has the best support community!

Cheers again.

Joe

---

### Post by TheFu on 2013-01-26
> **Sheepish said:**
> Thanks for the commands! I've just found an issue with thunderbird, following this advice :) 

I will use them in future a great deal I'd imagine.


**grep** is very powerful. 
**man** is very powerful too.

I run encrypted partitions without any noticeable performance issues - perhaps 2-3% is all. Something seems to have gotten borjked up on your first attempt.

Did you look for warnings BEFORE you reinstalled to find the true root cause or did you just reinstall and call it fixed?  I haven't needed to reinstall in years. The error and warning logs have been enough to find and correct any issues for me.

---

### Post by Sheepish on 2013-01-26
Uh Oh! Sorry to unsolve this, but its happened again. HOWEVER I've nailed it down to a rogue process, it happens intermittently, but it stuck at it for a while this time which enabled me to catch it in the act.

Gnome-Settings-Daemon is taking up like 90% of the CPU.

I killed the process which instantly brought the CPU and temps down (the fan was really going for it)

 I followed another threads advice that had a similar problem when connecting through VNC. It appears to be an issue with hotkeys on the keyboard. In my case, I can almost guarantee that it'll reoccur if I use the fn+volume keys or the numlock. It also goes a bit mental when typing and the cursor chooses a new home, in the middle of another paragraph...

The thread mentioned that removing the keyboard config file for gnome-settings-daemon in usr/lib

I sudo'd right in and moved the file to my desktop. the problem hasn't occurred since. I don't know if this is a permanent fix, but I hope so.

Fingers crossed! Hope this helps someone else!

Joe

---

