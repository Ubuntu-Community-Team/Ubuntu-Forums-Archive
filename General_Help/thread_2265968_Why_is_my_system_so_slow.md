---
title: "Why is my system so slow?"
date: 2015-02-18
forum: General Help
---

### Post by lordfkiller on 2015-02-18
I am running Ubuntu 14.04 LTS 64-bit on a Sony VAIO laptop, processor Intel Core i7 CPU M 620 @ 2.67GHz × 4, memory 4GB, GeForce GT 320M (dedicated RAM). To me, that sounds more than enough to run vim or Chrome smoothly, but that is far from what's happening. My system is terribly slow. Opening any program can take 20 seconds or more (especially for the first time) and the whole thing is just sluggish all the time. Most of the time only <10% of my CPUs is being used and >1GB of the memory is free. I have installed proprietary NVIDIA driver too.

Can anyone please help me find out what is wrong?!

---

### Post by nadarockyraccoon on 2015-02-18
Has it always been slow, or is this a recent occurrence? What driver are you using for you nvidia card? That would be the most likely culprit aside frm hardware issues. Using 3 of your 4 gs of memory seems like a lot more is being used than should be really, I have 3 of my 4 available. This would explain slow load times as something is eating your memory so it can't be used to load other programs. In this situation I would run a memtest (available on the boot menu of a live install disk), just to check and make sure you don't have a bad stick. When that comes back ok (as it likely will)  check to make sure your graphics card is using the right driver. I like lshw in a command line, it will tell you what the card is and what driver is being used for it. It could be that xorg is defaulting to vesa or the open-source driver because the proprietary driver installed isn't correct or correctly installed, this would result in a very slow system.

---

### Post by lordfkiller on 2015-02-19
It's been like this since I installed the OS. Previously I was using Windows and it's much faster on Windows.
I just double checked the driver - it's using NVIDIA proprietary driver.
memtest is okay.

---

### Post by dino99 on 2015-02-19
a few things might be checked:
- is it your hdd/sdd becoming full ?
- is your swap partition used ? and how large is it ?
- how are the powersaving settings set ?
- is the ram fully loaded/used ? (check the bios settings)
- and last but not least: logs are your best friends to find something usefull (warnings/errors)

---

### Post by pfeiffep on 2015-02-19
@lordfkiller - I'm certainly not an expert, but I suggest you investigate how your [swap (file or partition)]("https://help.ubuntu.com/community/SwapFaq") is being used. With 4gb memory simply running vim or a web browser probably wouldn't need to swap - especially right after start up - but you also don't want to eliminate swap completely. 
This command will tell you how your swap is being used
```
cat /proc/swaps
```
Read more [here]("http://www.cyberciti.biz/faq/linux-check-swap-usage-command/")
Check how swap is configured ```
cat /proc/sys/vm/swappiness
```
Probably your system should be about 5 - 20
Guidance how to change [swappiness]("https://sites.google.com/site/tipsandtricksforubuntu/system-tips/swappiness")

[Examine start up programs]("https://help.ubuntu.com/community/ShowHiddenStartupApplications") 

Try gnome flashback for an alternate desk top environment. (Available in software center)

Insure that your system is up to date using these commands:
```
sudo apt-get update
sudo apt-get upgrade
```

[Test your hard drive]("http://askubuntu.com/questions/38566/how-can-i-check-the-health-of-my-hard-drive")

Post back with questions or success

---

### Post by nadarockyraccoon on 2015-02-21
Just out of curiousity which Nvidia driver is being used? Just because additional drivers says it is installed doesn't mean it is being used. It's been a while since I've used a nvidia card,but I remember when I did that the additional drivers tool didn't always get it right, in which case it would fall back on the vesa driver. This in turn would eat a lot of ram and cause the system to run very slow, especially when trying to play flash videos or do anytning with any kind of graphical intensity. Admitedly I do not use Unity or compiz(makes pretty graphics on the desktop) so my memory usage should be lower than yours, but none the less using three out of four gigs of ram seems like a lot even for unity with full effects. 

To find out what driver is being used type in a terminal:
```
sudo lshw -c video | grep 'configuration'
```
also:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to make sure xorg was apropriately reconfigured after the driver was installed

---

### Post by Ruben_van_Smirren on 2015-02-24
You should test your harddisk! there might be a SMART status which indicated the disk is broken. But there can also be bad blocks on the disk. Also try to monitor the average performance of the machine!

---

### Post by kjohri on 2015-02-28
You can run the [htop]("http://www.softprayog.in/tutorials/htop-command-in-linux") command to see how the system resources are being used.

---

