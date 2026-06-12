---
title: "Ram upgrade issue"
date: 2021-01-21
forum: General Help
---

### Post by jbcooper on 2021-01-21
Hello, I read [this thread]("https://ubuntuforums.org/showthread.php?t=2453831") with great interest because I have just upgraded the RAM on a 64 bit machine with Lubuntu 20.04 already installed from 2 to 8 GB. The only apparent effect is that when I reboot, the wireless internet is very unstable and keeps dropping out, at least according to the web-browsers I use, they keep saying connection lost. The only way to cure it is to reboot again. So every time I want to use the computer, I have to boot it twice, which is a bit frustrating! Any clues very much appreciated. I didn't change anything else, as far as I remember  except installing conky :-0

Apart from that the system is better i.e. doesn't crash when the RAM fills up, well, with 8 Gb it never does fill up now, in my hands. It's just the double-booting problem that I want to solve.

---

### Post by QIII on 2021-01-21
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2453831").

Hello!


Please do not hijack the threads of other users with an issue of your own.  Please allow all users, including yourself, to get one-on-one support for their individual requests.  While issues may often seem to be the same, similar symptoms may arise from entirely different causes.  Confounding a thread that way causes confusion for the OP, those who attempt to help, and you.

---

### Post by CelticWarrior on 2021-01-21
The wifi issue is unrelated to any memory upgrade or dual-booting.

---

### Post by Autodave on 2021-01-21
Try removing the battery and leaving it out for 10 minutes while ALL other cables are disconnected.  Reinstall and see if that helps.

---

### Post by jbcooper on 2021-01-21
Thank you. I will try that and see how it behaves over a couple of days. That is extremely helpful. Re: hijacking other people's threads, I was trying to give the impression that I had already looked for a solution before asking a question, which I admit I did not do as thoroughly as I could have done, so that was bad of me on two counts. However it was an unexpected consequence of doing a memory upgrade to 20.04, post-install, which might not be irrelevant to others trying the same thing in the hope of getting a more reliable OS.

---

### Post by CelticWarrior on 2021-01-21
Not a consequence, unexpected or otherwise. That it happened after or that you start noticing after doesn't imply correlation. That said, you may inadvertently touched or partially disconnected one of the antennas while you were adding the new RAM or somehow disturbed something. If not applicable then absolutely NOT related. Even if the new RAM is defective the symptoms would be not that.

You say Lubuntu and 2GB RAM so probably (very) old hardware? Failures happen and it doesn't take much.

Recently there was a kernel update that has/has some issues. It happening due to this update (to 5.8 series) is far more plausible. Or everything can be just a coincidence.

Better see actual data: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
Please post results from the script so we can take a look at it.

---

### Post by grahammechanical on 2021-01-21
Are you connected to the Internet Service Provider by a telephone landline? I have experienced instances where the web browser says the connection was lost. I look at the indicators on the router and the router has dropped the connection to the ISP and is re-initializing the connection. This takes a certain time. Rebooting the OS as you do will allow the router sufficient time to re-establish the connection. I just wait until the router has finished and then re-open the web browser.

In my case I am experiencing interference on the telephone line. It causes the download speed to drop significantly and if the interference is very bad the router drops the connection to the ISP.

Regards

---

### Post by jbcooper on 2021-01-22
Hello, thank you. It is just a home phone line, allegedly fibre broadband. I have always had the occasional dropping out that you mentioned. This is a bit more regular though i.e. it happens within seconds of opening a webpage after booting and the wifi still seems to be connected. The web browser just says the page has crashed rather than there being no connection. Anyway it was almost certainly my incompetence in fitting the RAM, earthing my fingers, etc. I'll check it again tonite as I have removed the battery and held the power switch down to blank-out any residual charge, etc. Dare I hijack my own thread with another query? I was interested in the other thread about the default swap space being zero and was thinking that maybe that's why it used to crash when the RAM filled up. With 8Gb I guess it'll be OK set to zero. Anyhow, that's just an academic point now as I need to find out if the chips are not fried first ;-0

---

### Post by Yellow Pasque on 2021-01-22
I would run memtest to verify new and old RAM is good. What kind of system/motherboard are we dealing with here? Was 20.04 upgraded from an older version or fresh installed? 20.04 should have created a swapfile by default, unless Lubuntu does not that. The /etc/fstab entry would be:
```
/swapfile                                 none            swap    sw              0       0
```

>  Even if the new RAM is defective the symptoms would be not that.

It's unlikely, but we don't know for sure. PCI-e addressing/configuration can be affected by changes in RAM.

---

### Post by jbcooper on 2021-01-22
Hello, many thanks all. It is an Asus X453M from about 2015 which I did not start using until about 4 months ago - its basically a new machine! Lubuntu 20.04 was a fresh install over Windows 8. The wifi seemed fine today but here is the output from the wifi test: 

[https://pastebin.com/RnNwpvBk](https://pastebin.com/RnNwpvBk)
[FONT=courier new]
[FONT=arial]A few other commands show there is no swap space. I must have made a big bloomer when I did the installation which would explain why it kept hanging with only 2Gb RAM, duh.

[/FONT]cat /etc/fstab[/FONT]
[FONT=courier new]# /etc/fstab: static file system information.[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# Use 'blkid' to print the universally unique identifier for a device; this may[/FONT]
[FONT=courier new]# be used with UUID= as a more robust way to name devices that works even if[/FONT]
[FONT=courier new]# disks are added and removed. See fstab(5).[/FONT]
[FONT=courier new]#[/FONT]
[FONT=courier new]# <file system>             <mount point>  <type>  <options>  <dump>  <pass>[/FONT]
[FONT=courier new]UUID=b4e30e5d-1eea-4abc-bf75-095bfe91d10d /              ext4    defaults   0 1
[/FONT]
[FONT=courier new]cat /proc/swaps
Filename                                Type            Size    Used    Priority[/FONT]

free -h
              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       6.9Gi       176Mi       219Mi       646Mi       362Mi
[FONT=&amp]Swap:            0B          0B          0B

The web suggests about 8Gb swap space for 8Gb RAM so I just followed this excellent [article]("https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-20-04") and set the swapfile to 8Gb without any apparent issues! 

The output from Memtester looks ok, I think:
[FONT=courier new]
[/FONT][/FONT][FONT=courier new]sudo memtester 7G 1[/FONT][FONT=courier new]memtester version 4.3.0 (64-bit)[/FONT]
[FONT=courier new]Copyright (C) 2001-2012 Charles Cazabon.[/FONT]
[FONT=courier new]Licensed under the GNU General Public License version 2 (only).[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]pagesize is 4096[/FONT]
[FONT=courier new]pagesizemask is 0xfffffffffffff000[/FONT]
[FONT=courier new]want 7168MB (7516192768 bytes)[/FONT]
[FONT=courier new]got  7168MB (7516192768 bytes), trying mlock ...locked.[/FONT]
[FONT=courier new]Loop 1/1:[/FONT]
[FONT=courier new]  Stuck Address       : ok         [/FONT]
[FONT=courier new]  Random Value        : ok[/FONT]
[FONT=courier new]  Compare XOR         : ok[/FONT]
[FONT=courier new]  Compare SUB         : ok[/FONT]
[FONT=courier new]  Compare MUL         : ok[/FONT]
[FONT=courier new]  Compare DIV         : ok[/FONT]
[FONT=courier new]  Compare OR          : ok[/FONT]
[FONT=courier new]  Compare AND         : ok[/FONT]
[FONT=courier new]  Sequential Increment: ok[/FONT]
[FONT=courier new]  Solid Bits          : ok         [/FONT]
[FONT=courier new]  Block Sequential    : ok         [/FONT]
[FONT=courier new]  Checkerboard        : ok         [/FONT]
[FONT=courier new]  Bit Spread          : ok         [/FONT]
[FONT=courier new]  Bit Flip            : ok         [/FONT]
[FONT=courier new]  Walking Ones        : ok         [/FONT]
[FONT=courier new]  Walking Zeroes      : ok         [/FONT]
[FONT=courier new]  8-bit Writes        : ok[/FONT]
[FONT=courier new]  16-bit Writes       : ok[/FONT]
[FONT=courier new]Done.

Actually, the [thread]("https://ubuntuforums.org/showthread.php?t=2453831") I originally posted in had other relevant information from [/FONT][FONT=courier new]guiverc which confirms Yellow Pasques comment that Lubuntu 20.04 might not create swap space by default any more: "[/FONT]*[COLOR=#000000]However PLEASE NOTE: You currently may not have any swap allocated/utilized (which can slow performance significantly if your machine has limited RAM). It's not default on a Lubuntu 20.04 LTS install.[/COLOR]*[FONT=courier new]" Hence the crashing, I suspect.

Still got a bit of a crashy browser issue now, but never mind. I have tried clearing the cache and will see. [/FONT]

---

### Post by jbcooper on 2021-01-29
[s][SOLVED][/s]

Changed the wireless card [s]and the problem has gone away[/s]. Thanks to all who tried to help!

---

### Post by jbcooper on 2021-01-31
Well, partly solved. I had some browser crashing again  last night! I'm thinking it may be related to Falkon (my fave because it's very fast) since I get better reliability with Seamonkey instead, but with slower page-loads. Maybe Fallon is just too fast for it's own good!! Another thing I am getting with seamonkey is that pages start loading, then they disappear and then they appear again, apparently fine. I think Falkon was dying trying to do the same thing. Anyone got a clue what's going on? I can't complain though because I've never had the web as fast as this...

---

### Post by Yellow Pasque on 2021-01-31
[QUOTE=ME]I would run memtest to verify new and old RAM is good.[/QUOTE]
^^^^^^^

---

### Post by jbcooper on 2021-01-31
Hello again, the problems indeed returned with vengeance tonight and I believe that Yellow Pasque's excellent suggestion to re-check the memory provided the critical clue. I was going to revert back to the original 2Gb RAM to see what happened and therefore took the laptop apart again. While re-fitting the old RAM card I noticed it clunked-in much better than the new one had done, suggesting that I had not pressed in the new RAM card properly (yes, its that stupid of me, sorry!!). So the 8 Gb one was fitted again and pushed into its slots better, everything reassembled and, hey presto, no problems. I've been trying to break the web browsers for an hour or so, but not succeeded so far. Looks pretty promising now, I must say. Cheers again.

---

### Post by 18jamesw on 2021-02-01
wifi issue and RAM upgradation are poles apart. There may be some other issue with wifi, such as wifi adapter, or driver update.

---

### Post by jbcooper on 2021-02-01
Thanks. Still had the problem today but it was fixed with a single reboot. Previously was having to reboot several times! Still not got to the bottom of this one! There is a lot on the web about wifi power management causing the wireless connection to drop. If I type "iwconfig wlp2s0" it says power management is off, but if I look in "etc/NetworkManager/conf.d/default-wifi-powersave-on.conf" it says "wifi.powersave = 3" which corresponds to power management being on. All very confusing. The command: "sudo iw dev wlp2s0 set power_save off" works but saying "sudo iw dev wlp2s0 set power_save on" instead gives: "command failed: Operation not supported (-95)" suggesting that the power management is indeed off, perhaps?? The idea behind this is that if the battery is dodgy and using power after a restart or something, then looking at heavy-to-load RAM and CPU intensive websites might make the power dip enough to drop the wifi?? Is that a dumb idea?? It is plugged in all the time though.

---

### Post by jbcooper on 2021-02-03
Might have had a bit of a breakthrough - the system went so wonky it told me to run fsck during a reboot which seems to have done some good. Will update.

---

### Post by jbcooper on 2021-02-04
Looks very promising. 

So the working hypothesis is that having only 2Gb RAM with no swap space made the system crash about once a day which corrupted the filesystem. When I upgraded the RAM, the wonky filesystem was crashing the internet and other programs, too. 

Will update!

---

### Post by jbcooper on 2021-02-11
Kept going wonky so I re-ran memtester and this showed memory faults, duh, so it was the RAM after all. Refitted the 2Gb one and its fine.

---

