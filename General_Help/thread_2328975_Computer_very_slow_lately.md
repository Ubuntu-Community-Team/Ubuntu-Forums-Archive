---
title: "Computer very slow lately"
date: 2016-06-26
forum: General Help
---

### Post by dorlow on 2016-06-26
I can't pinpoint what is causing my PC to be so slow lately.  Months ago, it was speedy.  When working, windows keep going dark in a not responding type state.  I run cronky constantly monitoring my resources.  Typically Firefox, Xorg and Java are among the top CPU hogs.  But my CPU is barely over 50% utilized usually.  Memory isn't being over taxed either.  Some info on my PC.

Ubuntu 14.04
Lenovo Y70
Intel i7 4720HQ at 2.6 x 8 cores
16 GB memory
Samsung 1 TB SSD (not a hybrid.. full SSD) hard drive

My PC has really nice specs.  It should be speedy.  It is extremely slow lately.  There has to be something I can do to speed it up.

---

### Post by X-RED_Tech on 2016-06-26
I would test it in a live session (16.04 which is also what I would use for your hardware).

---

### Post by TheFu on 2016-06-26
"Slow" is subjective. Can you post numbers or a link to some performance monitoring data?  Something like **monit** or **munin** will generate graphs that we can all understand. I don't know how to get conky to capture data that can easily be shared.

Systems performance comes down to shared use of:
* cpu
* ram
* network I/O
* disk I/O
If those things are below 80% utilized, then look towards misconfiguration or hardware faults.  For those - I'd ask, what do the system log files say?  A common reason for slowness is a failing HDD or cable or controller or bad switch port or failing router or .... failing RAM or ... you get the idea.  Sometimes the answer is simple - reseat the RAM, check all SATA connectors, run some RAM tests - sometimes 1 stick will fail, but in a 16G box, you'd never notice without checking the log files.
Sometimes a bad USB device can destroy overall performance too. Look for USB fault messages - or overheating or .... there are hundreds of possible answers.

So ... what do that log files say?  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by poorguy on 2016-06-26
Does this happen when you are using your firefox browser?

I sometimes get what you described "[COLOR=#0000ff]windows keep going dark in a not responding type state[/COLOR]" when I'm using firefox browser. 

It usually will resume itself in a matter of seconds although sometimes I've had to close my browser and then reopen it.  

I believe it is just typical firefox browser as that is the only time that this seems to happen.

---

### Post by banceu_sergiu_ione on 2016-06-27
Make sure is all up to date and clean it.
Open a terminal and run
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```
```
sudo reboot
```

Open the terminal again

```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
```
sudo reboot
```

Now lets clean a bit your SSD

Run GParted and sign 10GB as free space ( this is important for your SSD life and from 1T, 10 GB will not even notice you not use )

Open a terminal

check if trim is supported
```
sudo hdparm -I /dev/sda | grep "TRIM supported"
```output:        *    Data Set Management TRIM supported (limit 8 blocks)

if  is, the trim your SSD

```
sudo fstrim --all
```

Do not do nothing while trimming is running. The proccess will not show you nothing and will look more like it got stuck but do not close the terminal. You will notice its over once you have the possibility to run some other command again.
this will trim your SDD important for performance and life.

reboot

Run trim once more time after you log in. Does it run better now?

---

### Post by TheFu on 2016-06-27
Trim runs periodically (weekly) in all Ubuntu versions since 14.04. Can't hurt to do this. Check that there is a fstim entry in /etc/cron.weekly/

I've never seen cleaning up apt make anything faster ... unless the disk was over 95% utilized. A full root partition will slow things down on any Unix-like system. Would be interested to learn if this does help. Never know.  If there is a separate /boot partition and it gets filled, bad things tend to happen during kernel updates.

No reason to run apt **upgrade** *and* apt **dist-upgrade**. dist-upgrade does everything the other option would do.  "apt" is preferred over apt-get and aptitude these days, but this really doesn't matter 99% of the time beyond saving typing 4 extra characters from what I can tell. ;)  Only 1 reboot would be needed. Is there a specific reason for 3 reboots?  Please teach me.

---

### Post by HermanAB on 2016-06-27
It depends on what exactly you mean by 'slow'.  Since you mentioned Firefox, try installing 'noscript' and 'adblock' plus and see if it works better. If so, then the problem is bad scripts on the websites you visit.  The solution is to dump the habit and go somewhere else.

You can also use 'dig' to check the speed of your DNS.  It is possible that the first DNS in your '/etc/resolv.conf' is lame or dead, causing timeouts and fall back to the second DNS.  In this case, delete the top entry and add something else, for example a Google DNS.

---

### Post by banceu_sergiu_ione on 2016-06-27
> **TheFu said:**
> Trim runs periodically (weekly) in all Ubuntu  versions since 14.04. Can't hurt to do this. Check that there is a fstim  entry in /etc/cron.weekly/

I've never seen cleaning up apt make anything faster ... unless the disk  was over 95% utilized. A full root partition will slow things down on  any Unix-like system. Would be interested to learn if this does help.  Never know.  If there is a separate /boot partition and it gets filled,  bad things tend to happen during kernel updates.

No reason to run apt **upgrade** *and* apt **dist-upgrade**.  dist-upgrade does everything the other option would do.  "apt" is  preferred over apt-get and aptitude these days, but this really doesn't  matter 99% of the time beyond saving typing 4 extra characters from what  I can tell. [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]  Only 1 reboot would be needed. Is there a specific reason for 3 reboots?  Please teach me.

I know trim runs periodically, but if he have lots of read/write it may be not enough each 1 week. I had notice on my SSD that if i do lots of write, its slow on performance and my system slow down a bit too. After i trim it manually it look to be as back new.

If happen that he notice a performance improved after triming it manually, I was to suggest him to change the trim cron job to run often, if make sense.

I know that upgrading it not may improve the performance. But we also don't know how often he upgrade. Mine was just a recall in case he set to run update manually and forgot to do it for long time. If you not update, in long time can counter a slow in performance.

I had ask the 1st reboot in case there was done kernel upgrades. I usually see stuff like ' will be configure at reboot ' or something like that. Did not ask to run a clean soon after dist-upgrade, since I do not know if it may be possible that same, still needed libs, may be removed.
The 2nd and 3rd reboot, you're right, can be jump.

apt vs apt-get, well it does not matter for me. but then he only have to do apt upgrade.

Let me know if I wrong anywhere since I'm not an IT and may miss same stuff i don't know. Any appreciate  suggestions, since I too will learn how more about.

---

