---
title: "Start Up Issues, Errors"
date: 2016-06-08
forum: General Help
---

### Post by coinfuture on 2016-06-08
I have been trying to clean out my computer. Essentially restoring it to it's original, fresh state.   When I attempt to reboot the following happens:  Black screen, white text. Scrolls really fast all the way down the screen.   I did some research, and booted with pressing the shift button. Then updated grub. Then did the reconfigure package files.   The issues still persist.   (I am thinking about uninstalling, and installing lubuntu)  However, I am on a dedicated path to learning everything that I can about linux. I would much rather seek and find the answer to what is causing this issue, and fix is manually.   I keep searching, reading what I think will fix it, then it turns out this isn't fixing it.   I believe that I have some type of malware on my computer. Sometimes it will say on the network manager, that it is connected to some strange ethernet network - that I have never been connected to. I don't ever use ethernet on this computer.   Please, any and all help will be so greatly appreciated. If there is an intruder on my computer I want to find him.   Also, when I updated the grub boot loader, when going into "recovery mode", I noticed that there were 2 seperate versions of ubuntu. 1 normal and 1 recovery mode for each. Seems this could be just past updated versions?

---

### Post by ventrical on 2016-06-08
Can you still execute commands? Can you copy n' paste data from terminal. If so could you send up the results from :

```

inxi -Fxz

```

Regards..

---

### Post by coinfuture on 2016-06-08
Hey. At first it said I didn't have inxi installed, so I installed it and ran your command. I will post the results below.     One thing I want to mention first, I forgot to mention in my original post. I found a mysterious folder in my home folder, containing 790,000 files. They all were scrambled letters? (I have been using linux for approx. 1 year, and have been playing around with command line a lot - maybe this could have done it?)    Thank you so much for replying. Info you requested is below!  ```
System:  Host: jamz-Lenovo-G570 Kernel: 3.16.0-71-generic x86_64 (64 bit, gcc: 4.8.2)              Desktop: Gnome Distro: Ubuntu 14.04 trusty Machine:   
System: LENOVO product: 4334 version: Lenovo G570    
Mobo: LENOVO model: N/A Bios: LENOVO version: 40CN33WW(V2.19) date: 08/14/2012
CPU: Dual core Intel Pentium CPU B940 (-MCP-) cache: 2048 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3) bmips: 7982.04  
          Clock Speeds: 1: 808.671 MHz 2: 809.687 MHz     
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0            
  X.Org: 1.16.0 drivers: intel (unloaded: fbdev,vesa)  Resolution: 1366x768@60.0hz              GLX Renderer: Mesa DRI Intel Sandybridge Mobile GLX Version: 3.0 Mesa 10.3.2  Direct Rendering: Yes  Audio:     Card: Intel 6 Series/C200 Series Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0              Sound: Advanced Linux Sound Architecture ver: k3.16.0-71-generic  Network:   Card-1: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)  driver: ath9k bus-ID: 02:00.0            IF: wlan0 state: up mac:              Card-2: Qualcomm Atheros AR8152 v2.0 Fast Ethernet driver: atl1c ver: 1.0.1.1-NAPI port: 2000 bus-ID: 01:00.0            IF: eth0 state: down mac:  Drives:    HDD Total Size: 500.1GB (3.5% used) 1: id: /dev/sda model: HITACHI_HTS54505 size: 500.1GB temp: 37C   Partition: ID: / size: 455G used: 17G (4%) fs: ext4 ID: swap-1 size: 4.24GB used: 0.05GB (1%) fs: swap   RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present Sensors:   System Temperatures: cpu: 0.0C mobo: N/A              Fan Speeds (in rpm): cpu: N/A  Info:       Processes: 189 Uptime: 5:24 Memory: 2134.4/3896.2MB Runlevel: 2 Gcc sys: 4.8.4              Client: Shell (bash 4.3.11) inxi: 1.9.17
```

---

### Post by grahammechanical on 2016-06-08
Please use paragraphs and please place printouts from commands in quote tags. At the start of the block of text enclose the word QUOTE in square brackets and at the end of the block of text enclose /QUOTE in square brackets. Or select the block of text and click the speech bubble icon in the row of icons above the text input panel.

And please describe the problem. You say "startup issues" but you do not describe the issues. You are listing normal Linux/Ubuntu operations as problems. It is normal for Linux to print to the screen a list of tasks that are being run and have completed. And yes the printout does move very fast. It is normal for Advanced options for Ubuntu to list all previous kernels and for everyone one of them to present a normal kernel to load and a kernel with a recovery mode option. And depending on the version of Ubuntu being used we should also get a version of the kernel with an option to load with Upstart.

By the way, what version of Ubuntu are you using? What are you trying to fix? When we "play around" as you put it and we do not know what we are doing we perhaps learn what not to do. I learnt awhile ago that a fresh install is the easiest and fastest way to fix things. I also learnt to have more than one installation of Ubuntu. I have one installation for normal work and one for experimenting with which I re-install to clear up the mess I have made.

Regards

---

### Post by ventrical on 2016-06-08
> **coinfuture said:**
>   However, I am on a dedicated path to learning everything that I can about linux. I would much rather seek and find the answer to what is causing this issue, and fix is manually. 

We created this sticky in development version to help newer persons have some extra helps on the dedicated path eh.

[http://ubuntuforums.org/showthread.php?t=1970289](http://ubuntuforums.org/showthread.php?t=1970289)

---

### Post by coinfuture on 2016-06-08
I've been using ubuntu for over a year without this happening...that's why I suspect something is off. I tried formatting my post with HTML but it won't let me, it shows turned off in my options. I didn't try to hard to change them, I went to users then settings where it told me I need more than 10 posts to be able to change settings. I apologize if you don't like my question. No matter how I formatted my post it wouldn't </br> at the end of lines. I just figured out I have to allow certain scripts from the noscript extension for this to work.

For startup behavior to change, after 1 year of consistent behavior, is not normal computer behavior. Computers do not "spontanteously change". They change after being told to change. I'm trying to determine what is the root of the cause of this new behavior.

---

### Post by ventrical on 2016-06-08
> **coinfuture said:**
> 

For startup behavior to change, after 1 year of consistent behavior, is not normal computer behavior. Computers do not "spontanteously change". They change after being told to change. I'm trying to determine what is the root of the cause of this new behavior.

There are several cases where quick fixes are provided and they work very durably.  Then there are case/sessions where quick-fixes  will not work at all.

1. First: Keep posting until  you top up to your quota. Then you will have the needed access granted to present a properly formed response to inquires made by the other forum members that are trying to assist you.

2. Second: Learn how to use the online editor. It will only benefit  you in the long run.

3. Read some of the links provided and get used to the terminal. Learning about the terminal commands helps us keep sharp and up to date and able to not only fix our own problems but the problems of others.

4. You have assumed that it is some form of malware that has attacked your install but you cannot prove it and you cannot provide any log file data that we can look at to help validate your claim. That  brings us back to the beginning of the loop and why it is so important to learn how to use the terminal if you are adamant about the path you are taking to be a problem solver. Learning linux or Ubuntu does not happen over night. There is a learning curve that has to be learned. We will make mistakes and we will learn from trial and error. Mostly all the helps I pass along to others  are solutions developed by other members of the forums at large.

  So try to learn the first 3 steps and I assure you that you will succeed in one way or another.

Regards..

---

### Post by coinfuture on 2016-06-08
Thanks to everyone who has replied to this post. The info is just what i needed to point me in the right direction. If any of my posts came off as disrespectful, I am sorry. #4 by vertical, I have assumed that some form of malware is in my install and it has me extremely on edge.

---

### Post by ventrical on 2016-06-08
> **coinfuture said:**
> Thanks to everyone who has replied to this post. The info is just what i needed to point me in the right direction. If any of my posts came off as disrespectful, I am sorry. #4 by vertical, I have assumed that some form of malware is in my install and it has me extremely on edge.

You have not been disrespectful at all. I spent the greater part of 20 years fighting with and cleaning malware from customers PCs that were largely Microsoft based operating systems. There are anti-malware programs for linux/ubuntu ie; ClamAV, Avast, AVG and Comodo (CAVL) which have real time scanning and guards. However, I would suggest first to stay the course and learn a few survival terminal commands. They can carry you a long way. You find some good threads in Security here : [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338) , many of which I have participated in.

 Malware and virus for linux are very rare. With the policy tool kit, apport and the firewalls available (plus software center) it is mostly non-existent. The structure of the ubuntu kernel itself is a malware destroyer by the merit that it is mostly impervious to crudely written crapware that has existed  for the last 30 years and that which is emerging in the wild.

 But if you look at the security forums link which I have provided you will see that I have not rested on my laurels and I am not just talking out of my hat here. So , lets say, that you have a malware and so perhaps here your journey of discovery can begin, to attempt to prove or disprove this. It is no waste of time. There are no wasted words here.  All question answers , right or wrong , they are all part of a larger  knowledge base and you are now part of that great venture.

 In the meantime it is imperative that we have fun also so if you get stuck on an install that seems hopeless and frustrating then we do fresh installs. It's not a wrong thing. In fact , that is where the ubuntu experience begins.

Regards..

---

### Post by X-RED_Tech on 2016-06-08
I agree with the previous post, test everything an all just to be sure... But I also have two words for you: Occam's Razor.
Malware as an hypotheses should be at the absolute bottom of the list of possibilities here.

Whatever was "cleaned" as mentioned in the OP is by far the most likely culprit. Can you give more details about what you did prior to experiencing the issue?

---

### Post by coinfuture on 2016-06-09
I used Bleachbit to clear up space and in an attempt to get my computer to run faster and more efficiently. 

I've read that this could maybe be the cause of all of this? Any way on my end that I could investigate further? On a side note, my computer is running much more efficiently after installing Bleachbit. The only issue I'm having is upon start up. I try to read the commands that it is outputting but they move way to fast. 

Even if this is something I can safely ignore, I would still like to find the root cause of what changed this start up behavior? 

& Thanks again so much to everyone who gave input. I'll be sure to pay it forward when I'm able to

---

### Post by X-RED_Tech on 2016-06-09
Indeed. Bleachbit could have deleted something it shouldn't and probably that's why many users stay away from it but at the same time other users swear by it.
The only way to investigate further that I can think of is checking the logs. The problem is I don't know which ones...

@ventrical
@grahammechanical

Do any of you know which logs to check?

---

### Post by ventrical on 2016-06-09
Heres a thread..

[http://ubuntuforums.org/showthread.php?t=1962213](http://ubuntuforums.org/showthread.php?t=1962213)

---

