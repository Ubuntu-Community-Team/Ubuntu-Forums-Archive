---
title: "CPU running at 100%"
date: 2016-12-01
forum: General Help
---

### Post by djen9999-h on 2016-12-01
After a recent update, I noticed that both cores of my CPU were running at 100%. It appears to be gnome software that is the culprit, but I also found this when I went to "Top.
```
dave@dave-Precision-WorkStation-T3400:~$ top


top - 16:01:15 up 8 min,  2 users,  load average: 7.80, 6.72, 3.47
Tasks: 287 total,   5 running, 282 sleeping,   0 stopped,   0 zombie
%Cpu(s): 87.9 us, 11.8 sy,  0.2 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem :  8107064 total,   689976 free,  6148856 used,  1268232 buff/cache
KiB Swap:  8318972 total,  8318972 free,        0 used.  1612992 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2141 icecast2  20   0  142600   6888   5796 R  93.7  0.1   4:48.20 icecast2    
 3682 dave      20   0 4334416 3.617g   6540 R  28.8 46.8   0:41.46 deja-dup-m+ 
 1774 dave      20   0 1485200  61656  31240 R  18.9  0.8   1:17.68 gnome-sett+ 
 1884 dave      20   0 1981852 581088  81052 R  16.9  7.2   1:32.58 gnome-shell 
 1721 dave      20   0   50380   9852   2868 S  15.9  0.1   0:20.18 dbus-daemon 
  310 root      20   0   35508   6180   5612 S   9.9  0.1   0:47.28 systemd-jo+ 
 1014 syslog    20   0  256400   4960   2828 S   6.0  0.1   0:21.36 rsyslogd    
 1894 dave      20   0  179728   5736   4268 D   3.0  0.1   0:14.06 dconf-serv+ 
 1356 dave      20   0  318848  86564  32412 S   2.0  1.1   0:11.44 Xvfb        
 1896 root      25   5  228484  36212  16060 S   0.7  0.4   0:03.86 aptd        
 1931 root      20   0  250468  74672  49008 S   0.7  0.9   0:07.07 Xorg        
 3068 dave      20   0 1688492 274052 101604 S   0.7  3.4   0:20.79 chrome      
    3 root      20   0       0      0      0 S   0.3  0.0   0:01.13 ksoftirqd/0 
    7 root      20   0       0      0      0 S   0.3  0.0   0:00.54 rcu_sched   
  891 message+  20   0   45452   5808   3492 S   0.3  0.1   0:05.10 dbus-daemon 
 2538 dave      20   0 1310524  53340  43448 S   0.3  0.7   0:01.86 nautilus    
 2629 dave      20   0  938276  88380  57440 S   0.3  1.1   0:06.11 mutter      

```

Any help would be appreciated.

---

### Post by ajgreeny on 2016-12-01
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**.  You will note how the code tags arrange the text in columns as it was in terminal; without the tags it is just unformatted text and almost unreadable.

What makes you say it is gnome-software that is using all your CPU?
Your **top** output suggests it is icecast2 that is the problem

---

### Post by #&amp;thj^% on 2016-12-01
You have icecast2 running?  is it configured properly? and how many icecast streams are going?
I have never seen mine run that high on CPU usage. "**CPU 93.7  0.1   4:48.20 icecast2** "
Here is just a nice basic set-up guide: [http://icecast.org/docs/icecast-2.4.1/basic-setup.html](http://icecast.org/docs/icecast-2.4.1/basic-setup.html)

---

### Post by djen9999-h on 2016-12-01
I don't recall installing icecast, and I have nothing streaming that I know of. I believe icecast is part of some other app. I tried uninstalling it, but it's not on my list of installed apps. I tried Synaptic and terminal. I will try the configuration suggestion.

---

### Post by djen9999-h on 2016-12-01
My formatting is incorrect and I apologize. Because of the high CPU usage, I keep locking up. Any ideas how to get rid of icecast? I checked my PPAs and i don't see anything. I could be wrong.

---

### Post by #&amp;thj^% on 2016-12-01
Try this:
```
killall icecast2
```
If you did not install it you could also remove it with:
```
sudo apt remove icecast2
```
log out and then login again...any better.

---

### Post by djen9999-h on 2016-12-01
Nope!  Still running at 100%.  Again, sorry for the formatting, but I'm working under pressure before my computer locks.

Here's my new Top.

```
dave@dave-Precision-WorkStation-T3400:~$ top


top - 21:34:36 up 3 min,  2 users,  load average: 7.65, 4.28, 1.72
Tasks: 300 total,   4 running, 295 sleeping,   0 stopped,   1 zombie
%Cpu(s): 81.6 us, 17.9 sy,  0.5 ni,  0.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8107064 total,  4819916 free,  2104344 used,  1182804 buff/cache
KiB Swap:  8318972 total,  8318972 free,        0 used.  5671348 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 3250 dave      20   0 1929816 410068  81216 R  38.5  5.1   0:24.04 gnome-shell 
 2004 dave      20   0 1486000  62792  31004 R  35.5  0.8   0:34.72 gnome-sett+ 
 1974 dave      20   0  360664  18488   6628 R  30.2  0.2   0:25.83 gnome-keyr+ 
 2577 dave      20   0 1694904 246928 100400 S  24.9  3.0   0:08.03 chrome      
  310 root      20   0   35516   8540   7968 S  19.6  0.1   0:22.21 systemd-jo+ 
 3060 dave      20   0  965988 221404  49868 S  16.3  2.7   0:04.75 chrome      
  904 syslog    20   0  256400   4252   2684 S   8.6  0.1   0:10.05 rsyslogd    
 2333 dave      20   0  179728   5744   4272 D   7.6  0.1   0:04.49 dconf-serv+ 
 1349 dave      20   0  318328  86372  32220 S   5.6  1.1   0:06.39 Xvfb        
 1883 dave      20   0   44856   4944   2788 S   3.0  0.1   0:04.24 dbus-daemon 
  910 message+  20   0   45616   6128   3540 S   2.0  0.1   0:05.10 dbus-daemon 
 2345 root      25   5  228492  36356  16204 S   2.0  0.4   0:01.99 aptd        
 1315 root      20   0  251184  74752  48984 S   1.3  0.9   0:04.19 Xorg        
    3 root      20   0       0      0      0 S   1.0  0.0   0:00.56 ksoftirqd/0 
 3604 dave      20   0  629536  32552  24748 S   0.7  0.4   0:00.19 mate-termi+ 
   13 root      20   0       0      0      0 S   0.3  0.0   0:00.45 ksoftirqd/1 
  259 root      20   0       0      0      0 D   0.3  0.0   0:00.13 jbd2/sda1-8
```

---

### Post by djen9999-h on 2016-12-01
Maybe a little better?

```
dave@dave-Precision-WorkStation-T3400:~$ top


top - 21:42:59 up 3 min,  2 users,  load average: 8.28, 3.80, 1.46
Tasks: 296 total,   4 running, 291 sleeping,   0 stopped,   1 zombie
%Cpu(s): 78.4 us, 19.0 sy,  0.3 ni,  0.2 id,  1.8 wa,  0.0 hi,  0.3 si,  0.0 st
KiB Mem :  8107064 total,  4902528 free,  2061152 used,  1143384 buff/cache
KiB Swap:  8318972 total,  8318972 free,        0 used.  5717020 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1890 dave      20   0 2002044 504060  81356 R  60.6  6.2   0:46.53 gnome-shell 
 2474 dave      20   0  364336  24048   6484 R  53.6  0.3   0:14.20 gnome-keyr+ 
 1779 dave      20   0 1487072  65064  31152 R  31.5  0.8   0:39.19 gnome-sett+ 
  298 root      20   0   35516   8492   7940 S  17.9  0.1   0:23.50 systemd-jo+ 
  916 syslog    20   0  256400   4252   2684 S   7.3  0.1   0:10.36 rsyslogd    
 1899 dave      20   0  179524   5620   4156 S   7.0  0.1   0:03.79 dconf-serv+ 
 1396 dave      20   0  311664  79440  32464 S   4.6  1.0   0:06.73 Xvfb        
 1728 dave      20   0   44732   5216   2868 S   3.3  0.1   0:04.86 dbus-daemon 
 1929 root      20   0  249808  74340  48940 S   2.0  0.9   0:03.03 Xorg        
  923 message+  20   0   45500   5924   3524 S   1.3  0.1   0:04.00 dbus-daemon 
 1901 root      25   5  228364  36124  16156 S   1.3  0.4   0:02.20 aptd        
 2567 dave      20   0  938236  89220  57804 S   1.3  1.1   0:01.43 mutter      
 3030 dave      20   0 1574124 178164  97580 S   0.7  2.2   0:04.72 chrome      
    3 root      20   0       0      0      0 S   0.3  0.0   0:00.53 ksoftirqd/0 
    7 root      20   0       0      0      0 S   0.3  0.0   0:00.20 rcu_sched   
   13 root      20   0       0      0      0 S   0.3  0.0   0:00.56 ksoftirqd/1 
  260 root      20   0       0      0      0 S   0.3  0.0   0:00.10 jbd2/sda1-8
```

---

### Post by mc4man on 2016-12-01
Why are you running gnome-shell in ubuntu mate?

---

### Post by alexjpowell on 2016-12-02
If you're not using icecast then what streaming software are you using?

---

### Post by djen9999-h on 2016-12-02
Good question. I switched from unity. Can I safely delete it?

---

### Post by djen9999-h on 2016-12-02
I use Google cast.

---

### Post by #&amp;thj^% on 2016-12-02
> **djen9999-h said:**
> Good question. I switched from unity. Can I safely delete it?

Just depends on which DM is being used. And to find out use this in the terminal:
```
grep '/usr/bin' /etc/systemd/system/display-manager.service
```
^^^Return the output here^^^
And just one more:
```
echo $DESKTOP_SESSION
```
Also ^^^Return the output here^^^

---

### Post by djen9999-h on 2016-12-02
Will do. I'm at work right now but I'll do it as soon as I get home. Thanks.

---

### Post by djen9999-h on 2016-12-02
> **1fallen said:**
> Just depends on which DM is being used. And to find out use this in the terminal:
```
grep '/usr/bin' /etc/systemd/system/display-manager.service
```
Blank - Nothing showed up at all!

^^^Return the output here^^^


And just one more:
```
echo $DESKTOP_SESSION
```

Again, blank - nothing at all
Also ^^^Return the output here^^^



Curioser and curioser!

---

### Post by #&amp;thj^% on 2016-12-02
Wow!! Do you just leave this machine on 24/7?
I wonder how it boots with no DM...unless you have a script made for this.
I was expecting something similar to mine:
```
[me@Silversurfer ~]$ grep '/usr/bin' /etc/systemd/system/display-manager.service
ExecStart=/usr/bin/[COLOR=#ff0000]gdm[/COLOR]
[me@Silversurfer ~]$ echo $DESKTOP_SESSION
[COLOR=#ff0000]mate[/COLOR]

```
So I use GDM as a DM && Mate as my DE.
I really need to think here to advise you any further...might take me some time though.
Just one more command to run for me if you would.
```
lsb_release -a
```
Just paste back in you your reply and not mine here...less confusing for me.

---

### Post by djen9999-h on 2016-12-02
dave@dave-Precision-WorkStation-T3400:~$ lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial
dave@dave-Precision-WorkStation-T3400:~$

---

### Post by ajgreeny on 2016-12-02
Hey, 1fallen.
Just for info I tried that ```
grep '/usr/bin' /etc/systemd/system/display-manager.service
```command on my Xubuntu 16.04 and I also get no output exactly like djen9999-h.

I'm not sure where this leads, though I think the command should be ```
grep '/usr/sbin' /etc/systemd/system/display-manager.service
```note /usr/[COLOR="#FF0000"]sbin[/COLOR], not /usr/[COLOR="#FF0000"]bin[/COLOR], where my system then outputs 
```
:~$ grep '/usr/sbin' /etc/systemd/system/display-manager.service
11:ExecStart=/usr/sbin/lightdm
```so I assume the various DMs perhaps install their executables in those different folders.

I am, however, equally baffled by the lack of output from the **echo $DESKTOP_SESSION** command.

---

### Post by djen9999-h on 2016-12-02
Thanks ajgreeny. I thought I was going nuts. I'm out for the evening, I'll continue my saga tomorrow.

---

### Post by #&amp;thj^% on 2016-12-02
> **ajgreeny said:**
> Hey, 1fallen.
Just for info I tried that ```
grep '/usr/bin' /etc/systemd/system/display-manager.service
```command on my Xubuntu 16.04 and I also get no output exactly like djen9999-h.

I'm not sure where this leads, though I think the command should be ```
grep '/usr/sbin' /etc/systemd/system/display-manager.service
```note /usr/[COLOR=#FF0000]sbin[/COLOR], not /usr/[COLOR=#FF0000]bin[/COLOR], where my system then outputs 
```
:~$ grep '/usr/sbin' /etc/systemd/system/display-manager.service
11:ExecStart=/usr/sbin/lightdm
```so I assume the various DMs perhaps install their executables in those different folders.

I am, however, equally baffled by the lack of output from the **echo $DESKTOP_SESSION** command.

Good catch ajgreeny:D  and might be also the difference between the OS i am currently running (Arch) 
So if the OP will try the new code ajgreeny has offered might prove a different result
```
grep '/usr/sbin' /etc/systemd/system/display-manager.service
```
Thanks Again ajgreeny.

---

### Post by djen9999-h on 2016-12-03
Thanks guys. I'll be back on line shortly. I'll check these commands

---

### Post by djen9999-h on 2016-12-03
Here's what I have so far

dave@dave-Precision-WorkStation-T3400:~$ grep '/usr/sbin' /etc/systemd/system/display-manager.service
ExecStart=/usr/sbin/lightdm
dave@dave-Precision-WorkStation-T3400:~$

---

### Post by ajgreeny on 2016-12-03
I think you have come across one of the potential problems of running two different DEs on the same OS, ie, there may be some incompatibilities of the usual DM used.

Unfortunately you have been using two of the DEs that I do not know nor use, so I will have to drop out here, apart from saying that you should be able to change the DM used with terminal command with ```
sudo dpkg --configure lightdm
``` I think that will ask you which DM you wish to use if more than one is found, and will then reconfigure the OS to do so.

Of course, whether or not changing the DM will have any effect on the high CPU% usage that was your original problem I can not say, but I can't quite figure out why it should cause that.

---

### Post by oldrocker99 on 2016-12-03
I have a low-powered laptop, on which I installed Ubuntu MATE. I had very high CPU usage as well on it, and installed lubuntu-desktop, and the CPU usage is much lower.

Just sayin'.

---

### Post by #&amp;thj^% on 2016-12-03
> **ajgreeny said:**
> I think you have come across one of the potential problems of running two different DEs on the same OS, ie, there may be some incompatibilities of the usual DM used.

Unfortunately you have been using two of the DEs that I do not know nor use, so I will have to drop out here, apart from saying that you should be able to change the DM used with terminal command with ```
sudo dpkg --configure lightdm
``` I think that will ask you which DM you wish to use if more than one is found, and will then reconfigure the OS to do so.

Of course, whether or not changing the DM will have any effect on the high CPU% usage that was your original problem I can not say, but I can't quite figure out why it should cause that.
+1 And at this point....we could see a real can of worms here.
> **oldrocker99 said:**
> I have a low-powered laptop, on which I installed Ubuntu MATE. I had very high CPU usage as well on it, and installed lubuntu-desktop, and the CPU usage is much lower.

Just sayin'.
+2 
@OP My 2 cents worth here is back-up your important data...and do a nice clean new install with just One Desktop Environment IE LXDE, XFCE, or if your up to it just a text-based OS with no GUI's.
Mate has been a steady and enjoyable experience for myself...but I have a Machine that handles all DE's quite well.
Maybe download some Live isos and try them before installing them to get feel for how they run on your hardware...and get feel for how they work for you.

---

### Post by djen9999-h on 2016-12-03
I'll try this first, before I do a clean install.  Thanks.

---

### Post by djen9999-h on 2016-12-03
dpkg: error processing package lightdm (--configure):
package lightdm is already installed and configured
Errors were encountered while processing:
lightdm


Next question. I have a 1TB drive that my OS is on as well as a ton of files, and an 80 gb drive with practically nothing on it. Is there any reason why I shouldn't designate the 80 gb drive as my boot drive?  I can just wipe the 80 gb drive and start fresh there.

---

### Post by ajgreeny on 2016-12-04
> **djen9999-h said:**
> dpkg: error processing package lightdm (--configure):
package lightdm is already installed and configured
Errors were encountered while processing:
lightdm


Next question. I have a 1TB drive that my OS is on as well as a ton of files, and an 80 gb drive with practically nothing on it. Is there any reason why I shouldn't designate the 80 gb drive as my boot drive?  I can just wipe the 80 gb drive and start fresh there.
It looks as if lightdm is the only display manager on your system, so that is the reason for that first error, and it should not be something to worry about.

Your second 80GB drive should also be fine for the root partition of a new OS if that is the way to go that you prefer.  Just choose "Something Else" at the partitioning stage of installing and point to a partition on that disk, make it ext4, use / (root) as the mountpoint and make sure the format tickbox is selected.  Your current / partition can be left alone for the moment; just make sure the tickbox for format is **not selected**. We can clean up any unwanted hidden files and folders in that later if necessary, and could even make it a new home partition, but let's move one step at a time for now.

---

### Post by djen9999-h on 2016-12-04
Sounds good. Thanks.

---

### Post by djen9999-h on 2016-12-05
I did a clean install.  Everything is running fine.  CPU is running between 2% and 17% depending on the load.  If anyone can give me some input as to why this may have happened in the first place, I'd be happy to hear it.

---

### Post by djen9999-h on 2016-12-07
Now, that I'm booting from the 80GB drive, can I just delete all of my system files from the 1TB drive or do I need to do something else?

I also switched the two drives so that I'm booting from the "a" drive.

---

