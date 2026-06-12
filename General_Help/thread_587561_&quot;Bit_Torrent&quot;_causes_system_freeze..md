---
title: "&quot;Bit Torrent&quot; causes system freeze."
date: 2007-10-22
forum: General Help
---

### Post by pedwards on 2007-10-22
Howdy all,

I just got a fresh copy of gusty running, and I'm having an issue with the gnome default bittorrent client, 
whenever I open a torrent file, select a location to save the data, and hit save;
my system freezes. (mouse, screen, even currently playing sound.)
any ideas on how to remedy this?


-pat

---

### Post by pedwards on 2007-10-23
Bump.

---

### Post by ihcnet on 2007-10-23
Do you have the same problem if you use a different BT client, like azureus or deluge?

---

### Post by ramnath on 2007-10-23
I have the same issue too in Gutsy. Using bittorrents causes a hard freeze.
I have tried both azureus and deluge. Both of them cause a freeze.
Also I experience freezes sometimes when using gmail's chat in Firefox. Looks like there's a freeze whenever the network activity is high.
Dapper did not freeze at all whatever I did. And these freezes occur only in Gutsy.

---

### Post by rykel on 2007-10-25
I am also experiencing repeatable, hardcore freezes in Gutsy whenever I run Azureus... but I am not sure if it is a bittorrent problem, or there is something seriously wrong with the Gutsy internal core... I never had freezes with Dapper before. (the version I was using before switching 2 days ago to Gutsy.)

---

### Post by zaphod777 on 2007-10-25
I noteced some issues with azurus too maybe a Java issue? I have been using KTorrent without any issues in Gutsy since tribe 5.

---

### Post by rykel on 2007-10-25
Can anyone try running some downloads in Azureus too and see if this hangs their system? The Java I have is the latest version from Java.com... Update 6 or something.

---

### Post by zaphod777 on 2007-10-25
even in XP I have seen it be a little flaky I think KTorrent works just as good if not better. I am not a big fan of Java apps they tend to not run unless you have a perticulare version of Java installed. At work we require 3 different versions of Java to be installed on all of the machines in order for certian apps to work and if somone updates their Java it can break it. It is a real headach. Java was supposed to be a godsend but I have found that it is really just a pain. 

I would definatly say it is a Java issue the more I thnk about it.

---

### Post by rykel on 2007-10-25
While I am not a fan of Java (I hope OpenOffice.org does not depend on Java either), I am also not fond of Ktorrent or the other clients... In this case, what can we users do about it? That is, the conflict between Java and our beloved OS...   :confused:

---

### Post by zaphod777 on 2007-10-25
Open Office seams to work fine. Any reason why you don't like KTorrent? There are plenty of other good clients out there you just have to hunt around I think Azurus was bloated anyway.

---

### Post by rykel on 2007-10-25
Other than k3b and AmaroK, most of the K software do not quite appeal to me... it is a GNOME vs. KDE thingy... as for other clients, they are not as fully featured as Azureus.

I just tried to grab Deluge a minute ago, but the download link is erroneous.

Only other torrent client I kind of like for its efficiency is uTorrent, which I can easily run in WINE.

So do you know if it might make a difference if I direct Azureus to use the open source Java, rather than Sun Java?

---

### Post by zaphod777 on 2007-10-25
no Idea if it makes a difference or not.

---

### Post by rykel on 2007-10-25
btw I just had a complete freeze runniing ktorrent... so no, it seems like it is a BITTORRENT problem, rather than a Java one. these Gutsy freezes are getting into my nerves, coz I feel the pain for my hardware everytime I unplug it the cold turkey way!!   : P

---

### Post by zaphod777 on 2007-10-26
hmm what hardware are you using? I have had no problems that I havn't caused myself from messing with things.

---

### Post by rykel on 2007-10-26
I have a Toshiba M40 laptop with NVIDIA GeForce Go 6600... I have never had problems with Azureus and Java under Dapper.

As for messing around, so far I had only deleted /etc/xorg.conf and all its backups, but that is a resolution problem instead of a bittorrent one, so I do not think it is the cause.

---

### Post by Maestro23 on 2007-10-26
> **rykel said:**
> Other than k3b and AmaroK, most of the K software do not quite appeal to me... it is a GNOME vs. KDE thingy... as for other clients, they are not as fully featured as Azureus.

**I just tried to grab Deluge a minute ago, but the download link is erroneous.**

Only other torrent client I kind of like for its efficiency is uTorrent, which I can easily run in WINE.

So do you know if it might make a difference if I direct Azureus to use the open source Java, rather than Sun Java?

Just downloaded the .deb from here: [http://deluge-torrent.org/News:Portal](http://deluge-torrent.org/News:Portal)

---

### Post by lyka on 2007-10-26
same problem here with EVERY bittorrent client...deluge, azureus...bittornado...just freeze randomly with gutsy.

mobo with nvidia chipset

wifi atheros madwifi

---

### Post by ramnath on 2007-10-29
I use Deluge (which I think is python based) and I still get freezes.
Running Firefox with lots of tabs open and loading image intensive sites seems to cause a freeze. I switched to galeon and I still keep getting hard freezes if I open many tabs.
I have a Intel mobo with Nvidia 7300 LE Geforce

---

### Post by rykel on 2007-10-29
On my side, it is NOT a bittorrent problem anymore, even though for a while I thought I had narrowed the recurring freezing problem to BT... I had tried Azureus, Deluge, KTorrent, web-based BitLet.org, downloading updates in Synaptic AND still the lockup occurs.

Sigh.... where are you, oh mighty Ubuntu devs??   :confused:

---

### Post by zaphod777 on 2007-10-29
Just out of curiosity what NIC drivers are you guys using? Before I was using an updated tribe 5 Gutsy but I wanted my drive encrypted so I download ed thelatest CD and did a freash install. I was backup and running with everything the same and have had none of those errors. The only thought might be restricted drivers?

---

### Post by rykel on 2007-10-29
Hi zaphod,

In fact I would be lucky if I could use restricted drivers (NVIDIA) properly... since Gutsy, I have been unable to get the driver to stay in business (see other threads)... it would perhaps work for the current session, but once I reboot, I would be back with low-res.

btw, in the other lockup thread, someone already has his laptop screen possibly fried by Gutsy.

I am so freaked out by the number of freezes (that is, every session in which I am downloading something at more than 50kB/s for more than 5 min, ala Bittorrent or Synaptic Package Manager) that I am now typing this in Windows XP... can't afford to have my hard disk bonked by the OS.

My card is a NVIDIA Gefore Go 6600 and the NIC I am using is a Huawei E270 HSDPA modem.

---

### Post by Crafty Kisses on 2007-10-29
> **pedwards said:**
> Howdy all,

I just got a fresh copy of gusty running, and I'm having an issue with the gnome default bittorrent client, 
whenever I open a torrent file, select a location to save the data, and hit save;
my system freezes. (mouse, screen, even currently playing sound.)
any ideas on how to remedy this?


-pat

You might want to check your resources:
```
top
```

---

### Post by zaphod777 on 2007-10-30
> **rykel said:**
> Hi zaphod,

In fact I would be lucky if I could use restricted drivers (NVIDIA) properly... since Gutsy, I have been unable to get the driver to stay in business (see other threads)... it would perhaps work for the current session, but once I reboot, I would be back with low-res.

btw, in the other lockup thread, someone already has his laptop screen possibly fried by Gutsy.

I am so freaked out by the number of freezes (that is, every session in which I am downloading something at more than 50kB/s for more than 5 min, ala Bittorrent or Synaptic Package Manager) that I am now typing this in Windows XP... can't afford to have my hard disk bonked by the OS.

My card is a NVIDIA Gefore Go 6600 and the NIC I am using is a Huawei E270 HSDPA modem.

I would really like to see how it could fry somones screen. NOw the wear and tear on the HDD I can understand the jury is still out for me on that one but I could see the reasoning behind it. You may want to check for bad memory and hdd and such you could just have faulty hardware that will cause lockups in every operating system. You can check if you are affected by the HDD error here:

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

[http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions](http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions)

I myself have no wories about ubuntu destroying my laptop.

---

### Post by zaphod777 on 2007-10-30
it looks like there are issues with nvidea drivers.

[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

---

### Post by emil.s on 2007-10-30
> **zaphod777 said:**
> it looks like there are issues with nvidea drivers.

[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

I'm running my server without X, and it freezes after some time whith rTorrent running...

I have reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+bug/158037](https://bugs.launchpad.net/ubuntu/+bug/158037)

Can everybody who have this problem post a comment to confirm this?

---

### Post by Lord_Dicranius on 2007-11-10
I've been having the same issues w/ the regular BT client, deluge, and ktorrent.  I've replied with a comment to the bug (thx again for submitting emil.s).

---

### Post by rykel on 2007-11-11
Hi all,

I got so sick and tired of the freezes that I did a clean format and reinstall of Ubuntu Gutsy... so far, so good, no lockups, despite downloading huge chunks of data at speeds of more than 200kB/s.

---

### Post by Lord_Dicranius on 2007-11-12
**UPDATE**
I'm able to download one torrent at a time! haha  I'm using ktorrent still.  I've set the max upspeed at 35KB/s and haven't run into any problems...as long as I only download one at a time.

---

### Post by pedwards on 2007-11-20
op here

ive just confirmed that my system freezes with any torrenting program. 

here's my top. 
      
top - 11:10:44 up  2:49,  2 users,  load average: 0.08, 0.20, 0.17
Tasks: 107 total,   3 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.6%us,  0.3%sy,  0.0%ni, 94.4%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   1035636k total,   586084k used,   449552k free,    67788k buffers
Swap:  2000084k total,        0k used,  2000084k free,   266808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5178 root      15   0 98.9m  48m 7564 S  2.0  4.8   0:23.86 Xorg               
 5719 patrick   15   0 62224  21m 6676 S  1.3  2.1   0:11.37 compiz.real        
 5916 patrick   15   0  211m  75m  24m R  1.3  7.4   0:52.60 firefox-bin        
 5662 patrick   15   0 16460 2788 1828 S  0.3  0.3   0:01.15 gnome-screensav    
    1 root      15   0  2952 1852  532 S  0.0  0.2   0:01.11 init               
    2 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.89 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   26 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   27 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   28 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  121 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  144 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
patrick@patrick-desktop:~$ 



this is definatly a bug in gusty, anybody have any resources on how to approach this?

---

### Post by jimbojones on 2007-11-21
My laptop freezes consistantly anytime I am using alot of bandwidth, torrents or not.  If I am streaming music and downloading a few files I get the hard lock up everytime.

---

### Post by enchance on 2007-11-21
Use Deluge. It's in the repositories. Deluge is somewhat the Linux counterpart of everyones favorite uTorrent.

---

### Post by sgt. slaughter on 2007-11-21
This is totally affecting me and driving me insane. It occurs with both KTorrent and Azureus on a system with a brand new hard drive and brand new install.  If anyone hears back from the bug post, please put it up

---

### Post by radox1912 on 2008-03-27
just confirming. using kTorrent, after 2 minutes it freezes the PC. if anyone has  a solution, post it here plz

---

### Post by killstheweak on 2008-04-02
While searching the web for this same problem i have, there's tons of hits. Yet no developers saying whats going on, or what the problem is, all the "solutions" i've read so far don't work.

Here's everything i tried

Lower max connections, i lowered it all the way down, still freezes.
Network card driver is supposedly biffed, out of all the posts i read, everyone has a different card, i had found one post with the same card as me, an atheros based card, which i use the propitiatory one, and also tried the windows one with ndiswrapper, system freezes
Upgrade kernel, i was using gutsy, so i installed the kernel from hardy, freezes, i did a clean install of Hardy, upgrades the kernel a couple times, every time, it still freezes.
Tried acpi=off noapic, noeverything, still freezes
I've tried Deluge, Azurues, Ktorrent, Miro, and rtorrent, still freezes. I tried different versions of all the above, including the debs from Deluge's site, sense there newer, and Azurues 3.

Nothing else locks up my system, i run aMule, which handles a lot of connection just like bittorent, yet aMule don't lock up.

I believe libtorrent is the culprit. 

But even if it is, i don't get how a bittorent client can bring the King of Kernels to it's knees. I mean, we laugh at Windows for this same thing, yet here we are.

Guess it could be worse, having gedit halting the system :P

---

### Post by defmomo on 2008-04-02
I am having the same problem, i seemed likely to me that it was a bug in my wireless card's driver, since it wasn't supported in gutsy. Hope this gets fixed soon, or i will be stuck with running bittorrent from a vmware install of gutsy or windows...:confused:
By the way, has anyone tried the firefox torrent plugin?
I use: D-Link DWL-G510 with the Transmission bittorent client

---

### Post by killstheweak on 2008-04-03
There's a new kernel for Hardy today, running it right now with ktorrent, been downloading for a half an hour so far, and no freeze, maybe it finally got fixed (watch, itll probably freeze right after i post this :P)

---

### Post by defmomo on 2008-04-03
> **killstheweak said:**
> There's a new kernel for Hardy today, running it right now with ktorrent, been downloading for a half an hour so far, and no freeze, maybe it finally got fixed (watch, itll probably freeze right after i post this :P)

:lolflag:

Fingers crossed!

---

### Post by killstheweak on 2008-04-03
Bah, i added a second torrent to download and it froze a minute later, this is ridiculous.

---

### Post by killstheweak on 2008-04-04
Found a solution

Step 1) Install Windows XP
Step 2) Cry
Step 3) Install uTorrent


No more system halts 

:P

---

### Post by defmomo on 2008-04-04
I am pretty sure the Crying part occurs before, during, as well as after Step 1...

---

### Post by killstheweak on 2008-04-05
Ha, ya, but what else ya gonna do, the bug seems to being blamed on everything, and no fixes, nor anything specific to even look for to be able to fix :P

---

### Post by defmomo on 2008-04-05
I posted a bug report  in Launchpad : [https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/211026]("https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/211026"). Please post there all the different occurences of the bug, and your different environments. Hopefully we'll get it solved soon. By the way, the origin of the bug would appear to be the network, and not the torrent library

---

### Post by wieman01 on 2008-04-06
Same problem here with Kubuntu Gutsy. The whole system would freeze on me after a while and a reset is necessary.

---

### Post by stuart.camenzind on 2008-04-09
Hi all,
I had been having this problem for a long time, but I finally stumbled upon a solution.  See, in my case the problem was being caused by ndiswrapper.  I just went to ndiswrapper.sourceforge.net and downloaded older versions until I found one that worked for me.  I am using an Airlink AWLH6080 and ndiswrapper version 1.44 and am no longer having any freezing.  Do the following to install a new (old) version of ndiswrapper after downloading ndiswrapper tarball to home folder:

```
tar zxvf ndiswrapper-version.tar.gz
cd ndiswrapper-version
sudo su
make uninstall
make
make install

```
Then to reload the module:
```
modprobe -r ndiswrapper
modprobe ndiswrapper
```

I didn't get the right version the first time, so you'll just have to experiment and see what ndiswrapper version works for you.  Good luck!

---

### Post by wieman01 on 2008-04-10
stuart.camenzind, 

You are making a very good point. I have been suspecting the same thing, because the system started freezing with other apps (e.g. Superkaramba) running as well, in particular while network traffic was high.

I might try your solution.

---

### Post by killstheweak on 2008-04-11
Well ya the ndiswrapper in gutsy freezes too, but whatever one is in hardy works good, the atheros driver is biffed in gutsy and hardy.

---

### Post by defmomo on 2008-04-12
It seems too much of a coincidence that all these different cards fail at the same thing. Looks like it's a problem with the way the network card driver is handled

---

### Post by wieman01 on 2008-04-13
> **killstheweak said:**
> Well ya the ndiswrapper in gutsy freezes too, but whatever one is in hardy works good, the atheros driver is biffed in gutsy and hardy.
I can confirm it, no freezes up to know. Hardy Beta.

---

### Post by killstheweak on 2008-04-14
K it was either fixed recently in Hardy, or it was the realtime kernel causing it (anyone else with problems using the realtime kernel?).

 I can't tell cause the newest realtime kernel won't let me online at all, just keeps trying to connect.

In the newest regular kernel tho, i qued up 3 torrents with atleast 6000 seeds, and it didnt even show a sign of wanting to freeze.

---

### Post by defmomo on 2008-04-18
I'm just gonna hijack this thread for a sec:How can I remove the realtime kernel? I just upgraded from 7.10, here is some info:
```

tux@tux-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

```

```

tux@tux-desktop:~$ uname -a
Linux tux-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

---

### Post by Virtual_Ron on 2008-04-20
Anyone get anywhere with this?

I'm having the similar problems.  cannot run any torrent clients.  My fav was Deluge, but I've tried ktorrent, and transmission.    They all work, but hang randomly.    They may run for 20 hours then hang, or 2 minutes then hang.   All the clients hang my entire machine requiring a hard boot, except transmission... instead of hanging my machine, it just unexpectedly closes, with the following in syslog.

[PHP]Apr 20 14:51:28 vulcan kernel: [ 8742.215403] transmission[30956] general protection rip:7f0d512d5a92 rsp:42403e30 error:0
Apr 20 14:52:27 vulcan kernel: [ 8761.872357] transmission[31006] general protection rip:7fe7f370f253 rsp:7ffffd0a5268 error:0
Apr 20 14:54:48 vulcan kernel: [ 8808.867910] general protection fault: 0000 [1]  SMP[/PHP]

I've been having this problem for a few weeks now.   I upgraded my ATI drivers, tried various kernels, tried KDE4, finally upgraded to Hardy.  All to no avail.
I've NO screensavers running, no desktop effects, no powersave features enabled.

I have even deleted all current torrents, and started a "new" one to see if it was a problem with any of my current downloads.  nope.

I have no problem downloading other than torrent.   I downloaded the hardy dvd without issues.

Any suggestions/rants/raves/ would be welcome.    "torrent" is 99% of the reason I built this machine ;)

I'm currently running ** Kubuntu 8.04rc AMD64**
Hardy Heron
kernel: **2.6.24-16-generic**
4 Gigs Ram
AMD64 X2 Dual 6000+
ATI Radeon X1200
ATI 8.476 video drivers
KDE 3.5.9

---

### Post by jmlaniel on 2008-04-21
Same problem here on my Dell Inspiron 530... I tried Azureus and the Transmission that comes with Hardy (Beta) and the system freezes for no reason. It might be instantaneous or after 5 hours. From what I see with the bug report, nothing is really converging toward a solution...

I tried looking for the problem in the logs, but I was unable to find anything... :confused:

One thing I noticed when doing a normal shutdown that I did not get when I was running Gutsy: in the verbose, I see a line that seems to be telling me that there is a problem with doing the shutdown of the network manager. However, since the verbose is going really fast, I can't see it. I was also unable to find this verbose in the logs... How can I access this verbose?

I am now convince (as a lot of people on the board) that the problem is probably with the network driver.

If anyone has a solution, please post-it!!!

---

### Post by Padishad on 2008-04-22
Hi everyone, 

I certainly do not have a solution but I can tell that this "freezing" bug started for me a week ago, after two main steps:

- I resolved the "ubuntu kills my HDD" problem (I can't even explain correctly what I did in French, so people who don't see what I'm talking about, search on Google; to sum up, I changed the HDD spin configuration, preserving it from unloading every 5 seconds - you know, a strange "clack" in your HDD; here is a link in French that explains everything and tells what to do: [http://idoric.free.fr/dotclear/index.php/post/2007/10/27/Comment-jai-echappee-a-la-mort-prematuree-du-disque-dur-de-mon-Dell-Inspiron-6400n](http://idoric.free.fr/dotclear/index.php/post/2007/10/27/Comment-jai-echappee-a-la-mort-prematuree-du-disque-dur-de-mon-Dell-Inspiron-6400n)

and that's what I did: typing this "/dev/sda {apm = 254}" then editing the "/etc/laptop-mode/laptop-mode.conf", caching etc...) (can't say more in English, sorry)

- I changed my wifi control pannel, deleting network-manager and installing wicd (definitely a better one); i remember installing the newest ndiswrapper during the process (following advices from a guy using the same Inspiron 6400 than me, who told me it will improve my wifi connection)


I did that last week; since, each time I use Ktorrent, no matter what I download / the speed / the other programms running, it freezes after 5 or 10 minutes. Amule seems to work well. I never had this problem before using wicd (and downloading the newest ndiswrapper) and resolving the "ubuntu kills my HDD" stuff. 
So I think the problem comes from one of these two steps..

Hope my comment to be helpful

---

### Post by defmomo on 2008-04-23
The problem remains, but it now manifests itself when more than 1 program is using the network: After two days of tests, i either use bittorent or surf the internet or use ssh, but never at the same time. As soon as i launch a second program, the pc freezes within minutes.

---

### Post by calc on 2008-04-23
One of the reports mentioned that after the machine had hung for the user he unplugged the network cable (non-wifi) and that the system was no longer frozen and started working again. If this is the case for other users with the hang problem it may be that the torrent apps are opening too many network connections (or not closing them after use) or something of that nature. If this is the cause it may take a few minutes for the system to unhang after removing the network cable, for the connections to timeout. If the systems stay frozen though it does sound like some sort of driver problem.

---

### Post by calc on 2008-04-23
You can use 'netstat -ntu' to see how many connections your system is currently keeping track of and their current state.

---

### Post by Virtual_Ron on 2008-04-29
After pulling out all but 3 of my hairs... I discovered my torrent crashing was due to bad RAM.   Wierd  how the only time I had any freezes/crashes was when running torrent, but... o'well.

I ran memtest86+ and during the first 2 tests, I got a flood of errors. I narrowed it down to what memory Unit it was, removed it, and PRESTO.  All is well.

Morel of this story:   even if you don't suspect it, run a memtest anyway. :)

---

### Post by defmomo on 2008-04-29
Memory issues can not explain this happening to this many people (although i ran a memtest as soon as i saw your post). Glad removing the faulty ram fixed it for you.

---

### Post by wieman01 on 2008-04-29
> **defmomo said:**
> Memory issues can not explain this happening to this many people (although i ran a memtest as soon as i saw your post). Glad removing the faulty ram fixed it for you.
Unless there are **many** people with RAM problems.

---

### Post by defmomo on 2008-04-29
It's possible, but highly unlikely

---

### Post by wieman01 on 2008-04-30
> **defmomo said:**
> It's possible, but highly unlikely
:-)

---

### Post by trunip190 on 2008-05-12
I am currently using 8.04(Hardy Heron), and after i have accessed the itnernet for a certain period of time, i get a freeze, and have to manually shut down. i have tried this with both firefox and the software updater.

---

### Post by rykel on 2008-05-13
> **trunip190 said:**
> I am currently using 8.04(Hardy Heron), and after i have accessed the itnernet for a certain period of time, i get a freeze, and have to manually shut down. i have tried this with both firefox and the software updater.

Was your Ubuntu a new installation or upgrade? Also, was it installed using Wubi (ie. in a folder within Windows) or on a separate partition?

IF you upgraded, or is running from Wubi installation, try (re)installing (on a separate partition) as old files might have caused conflicts with the new ones. Hope that helps.

---

### Post by trunip190 on 2008-05-14
i had Gutsy installed, but formatted the partition to install.
it is on a seperate partition.

---

### Post by defmomo on 2008-05-14
The problem seemed to go away, but it came back after the update to the 2.6.24-17 kernel...

---

### Post by trunip190 on 2008-05-15
i'm wondering whether it's the wireless network adapter sending a request that is being counted as a freeze request.
i have an advent 7302 laptop, do other people have laptops or is this problem also on desktops?

---

### Post by messelink on 2008-05-22
I'm having the same problem. The system will completely freeze when downloading torrents.

The system (Hardy) is used as a MASQ router for an internal network as well. The on board network (Abit AN7 mainboard) is used for the external connection and the extra network card is connected to the local network (all cable).

I have tried a lot of different bit torrent clients: BitTornado, Deluge, Transmission, Transmission-cli for TorrentFlux-B4rt and they all have the same problem.

The problem occured after upgrading Gutsy to Hardy.

The system completely freezes and you can't restart X or do a soft reboot. Also, as mentioned above, there is no network activity anymore.

---

### Post by minibeardeath on 2008-06-02
i have had the same problems with the torrent clients. up until i upgraded to hardy, i was able to get DL speeds of up to 1Mb/s w/ my wifi card, now i can get those same speeds, but only for a random length of time until my computer freezes up. after reading through this thread, the only thing that i have to add, is that i get the following error in my kern.log right at the time that my computer freezes.

```
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.553476] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.554715] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.554716] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.555867] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.555868] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559093] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559094] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559283] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559284] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559435] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559436] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559624] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.559625] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560074] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560075] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560415] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560416] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560771] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.560772] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.561085] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.561086] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.561232] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.561233] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.883517] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:37 patrick-desktop kernel: [ 2468.883519] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.738361] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.738362] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.738899] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.738901] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.839333] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.839334] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.839508] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2469.839509] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192109] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192111] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192350] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192351] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192619] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:38 patrick-desktop kernel: [ 2470.192620] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.242619] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.242620] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.245359] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.245360] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.246761] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.246762] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.247053] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.247054] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.247307] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.247308] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.248008] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.248009] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.292881] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.292883] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.293603] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.293604] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.294678] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.294680] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.294983] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.294984] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.295327] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.295328] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.393913] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.393914] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395061] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395062] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395231] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395232] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395545] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.395546] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.494822] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.494823] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495010] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495011] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495440] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495441] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495792] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.495793] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.496206] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.496207] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.496479] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.496480] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.545287] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.545288] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553393] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553395] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553665] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553666] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553877] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.553878] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554210] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554211] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554422] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554423] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554876] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.554877] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555023] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555024] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555341] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555342] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555551] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.555552] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.595860] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.595861] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.598228] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.598229] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.599991] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.599992] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.601896] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.601897] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.603891] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.603892] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.607453] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.607454] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.614272] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.614273] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.615212] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.615214] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.616689] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.616690] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.617194] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.617196] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.617551] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.617553] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.618139] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.618140] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.619030] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.619031] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.620414] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.620415] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.646259] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.646261] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.646819] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.646820] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.647388] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.647389] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.647978] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.647980] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.648290] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.648291] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.797430] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.797431] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798022] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798023] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798245] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798246] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798672] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2470.798673] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:39 patrick-desktop kernel: [ 2471.052970] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:39 patrick-desktop kernel: [ 2471.052971] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.305772] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.305773] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.306432] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.306434] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307089] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307091] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307761] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307762] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307989] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.307990] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.308198] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.308200] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.308651] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.308653] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.506682] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.506683] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.516172] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.516173] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.516912] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.516914] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.517073] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.517074] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.517382] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2471.517383] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:40 patrick-desktop kernel: [ 2472.110957] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:40 patrick-desktop kernel: [ 2472.110958] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.514443] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.514444] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.515346] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.515347] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.766728] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.766730] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.767274] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.767275] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.768125] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.768126] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.816126] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.816127] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.816479] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.816480] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.916922] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:41 patrick-desktop kernel: [ 2472.916923] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471110] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471112] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471312] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471313] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471484] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.471485] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.622255] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.622257] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623379] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623380] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623644] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623645] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623981] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.623982] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.624353] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2473.624354] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.024969] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.024971] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025282] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025283] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025551] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025552] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025783] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:42 patrick-desktop kernel: [ 2474.025784] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.528395] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.528397] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931421] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931422] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931455] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931456] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931926] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.931928] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.932074] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:43 patrick-desktop kernel: [ 2474.932075] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.636736] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.636738] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.636931] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.636932] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.989049] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.989050] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.989219] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2475.989220] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.190362] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.190364] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.190612] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.190613] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.191640] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.191641] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.191909] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:44 patrick-desktop kernel: [ 2476.191910] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.391776] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.391778] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.408953] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.408954] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409296] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409297] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409561] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409562] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409746] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.409747] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.410171] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.410172] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.410701] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.410702] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411069] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411070] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411257] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411258] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411590] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411591] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411904] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.411905] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412057] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412058] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412506] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412507] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412855] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.412856] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.693839] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.693840] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.693968] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.693969] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.999092] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.999093] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.999405] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2476.999406] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.000147] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.000148] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.002190] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.002191] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.004704] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.004705] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.005471] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.005472] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.005839] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.005840] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.006066] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.006067] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.007915] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.007916] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.008066] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.008067] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.008403] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.008404] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.009107] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.009108] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010015] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010017] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010320] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010321] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010624] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.010625] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.011053] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.011054] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.011658] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.011659] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012207] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012208] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012577] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012578] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012740] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.012741] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.013046] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.013047] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.013290] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:45 patrick-desktop kernel: [ 2477.013291] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.549056] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.549057] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.549342] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.549343] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.649977] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.649979] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.801174] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.801175] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.801461] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2477.801462] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:46 patrick-desktop kernel: [ 2478.002955] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:46 patrick-desktop kernel: [ 2478.002956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758189] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758191] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758337] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758338] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758472] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2478.758473] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010332] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010333] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010517] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010518] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010667] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.010668] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011002] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011003] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011256] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011257] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011426] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011427] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011600] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:47 patrick-desktop kernel: [ 2479.011601] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.363333] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.363335] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.413837] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.413838] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.413977] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.413978] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.464338] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.464339] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466136] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466137] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466671] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466672] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466880] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.466881] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468230] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468231] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468570] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468572] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468843] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2479.468845] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.031412] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.031414] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035040] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035042] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035385] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035386] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035794] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:48 patrick-desktop kernel: [ 2480.035795] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.371148] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.371149] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379273] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379274] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379664] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379665] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379811] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.379812] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.380165] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.380166] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.380498] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:49 patrick-desktop kernel: [ 2480.380499] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.467719] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.467721] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.467991] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.467992] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.921120] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.921122] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.921903] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.921904] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.922108] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2481.922109] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.025362] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.025364] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.025951] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.025952] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.072578] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.072579] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.073514] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.073515] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.074191] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.074193] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.074502] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.074503] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.170030] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.170031] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.170702] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.170704] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171071] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171072] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171299] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171300] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171468] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171469] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171697] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.171698] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172006] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172007] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172395] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172396] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172783] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.172784] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173012] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173013] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173180] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173181] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173390] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173391] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173800] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.173801] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174229] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174230] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174498] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174499] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174787] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.174788] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175215] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175216] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175504] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175505] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175673] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175674] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175881] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.175882] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176311] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176312] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176760] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176761] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176948] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.176949] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177298] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177299] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177647] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177648] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177876] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.177877] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178164] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178165] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178373] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178374] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178601] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.178602] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179052] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179053] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179281] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179689] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179690] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179998] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.179999] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180247] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180248] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180696] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180697] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180985] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.180986] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181154] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181155] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181563] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181564] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181721] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181723] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181980] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.181981] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182233] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182234] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182459] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182460] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182706] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182707] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182956] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.182957] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.183188] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.183189] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.183374] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:50 patrick-desktop kernel: [ 2482.183375] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.375123] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.375124] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.375266] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.375267] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.425713] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.425715] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.425971] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:51 patrick-desktop kernel: [ 2482.425972] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476025] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476027] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476257] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476258] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476694] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476695] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476924] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.476925] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.497951] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.497952] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.499240] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.499241] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.499862] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.499863] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.500300] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.500301] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.500441] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.500442] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980218] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980220] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980414] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980415] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980560] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980561] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980896] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:52 patrick-desktop kernel: [ 2483.980897] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.481867] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.481869] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.484224] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.484225] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.485284] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.485285] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.485748] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.485749] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486192] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486193] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486496] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486498] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486801] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.486802] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487084] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487085] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487249] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487250] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487474] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487474] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487818] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487819] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487990] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.487991] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.488376] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2484.488377] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067067] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067068] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067098] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067099] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067281] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067282] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067561] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067562] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067639] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.067640] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.168626] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.168628] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.169303] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.169304] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.169610] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.169611] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.170318] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.170320] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.171223] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.171224] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.171812] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.171814] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172260] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172261] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172649] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172651] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172837] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.172838] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173127] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173128] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173379] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173380] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173545] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173546] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173915] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.173916] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.174303] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:53 patrick-desktop kernel: [ 2485.174304] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:54 patrick-desktop kernel: [ 2485.672089] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:54 patrick-desktop kernel: [ 2485.672091] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.299059] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.299060] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300083] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300085] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300395] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300396] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300748] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300749] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300960] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.300961] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.349391] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.349393] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.350158] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.350160] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.350551] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.350552] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.399918] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.399919] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.400140] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.400142] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.400587] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.400588] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.401274] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.401275] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.401481] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.401482] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.752652] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2486.752653] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:55 patrick-desktop kernel: [ 2487.023252] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:55 patrick-desktop kernel: [ 2487.023253] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.658831] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.658833] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659172] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659174] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659344] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659345] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659537] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.659538] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.709289] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.709290] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.810083] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.810084] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.810466] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:56 patrick-desktop kernel: [ 2487.810468] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817114] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817115] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817222] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817223] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817409] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817410] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817854] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:57 patrick-desktop kernel: [ 2488.817855] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:57 patrick-desktop kernel: [ 2489.220328] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:57 patrick-desktop kernel: [ 2489.220330] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:58 patrick-desktop kernel: [ 2490.026184] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:58 patrick-desktop kernel: [ 2490.026186] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:58 patrick-desktop kernel: [ 2490.026244] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:58 patrick-desktop kernel: [ 2490.026246] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.166881] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.166883] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.166933] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.166934] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167137] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167138] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167546] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167547] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167895] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.167896] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168124] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168125] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168373] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168374] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168682] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:51:59 patrick-desktop kernel: [ 2491.168683] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2491.288779] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2491.288780] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2491.292658] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2491.292659] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.145688] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.145690] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.145938] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.145939] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.146369] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.146370] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.146682] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:00 patrick-desktop kernel: [ 2492.146683] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.467156] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.467158] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470350] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470351] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470673] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470674] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470959] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.470960] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471425] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471426] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471690] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471692] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471955] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.471956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.472205] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.472206] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.599392] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2492.599394] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2493.103499] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2493.103500] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:01 patrick-desktop kernel: [ 2493.103658] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:01 patrick-desktop kernel: [ 2493.103659] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.305140] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.305141] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.305337] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.305338] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.405915] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.405917] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.406371] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.406373] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.406663] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.406664] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506539] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506567] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506569] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506896] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.506897] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.507205] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.507206] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.507362] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:02 patrick-desktop kernel: [ 2493.507363] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.292810] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.292812] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.297585] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.297587] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.297870] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.297871] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298022] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298023] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298465] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298466] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298669] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298670] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298954] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.298955] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.299299] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.299301] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.299724] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.299725] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.665852] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.665854] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.666061] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.666062] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.666467] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:03 patrick-desktop kernel: [ 2494.666469] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.522510] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.522511] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.523580] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.523581] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.524913] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.524914] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.525697] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.525698] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.525926] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.525927] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526343] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526344] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526491] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526492] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526664] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.526665] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.527017] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.527018] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.527206] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2495.527207] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.126982] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.126983] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.127107] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.127108] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.227776] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.227777] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.228153] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.228155] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.228345] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:04 patrick-desktop kernel: [ 2496.228346] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.241362] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.241363] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.310637] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.310639] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.311453] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.311455] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.312209] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.312210] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.312392] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.312393] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.504302] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.504303] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.505281] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.505282] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.591293] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.591294] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.592537] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.592538] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593646] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593647] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593776] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593777] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593920] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.593921] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.594246] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.594247] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.594820] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.594822] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.595050] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:07 patrick-desktop kernel: [ 2498.595051] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.248449] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.248451] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.751363] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.751364] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.751418] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.751419] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.852289] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.852290] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.902782] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.902783] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.903369] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.903371] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.903799] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.903800] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904009] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904010] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904420] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904421] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904611] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904612] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904900] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.904901] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.953280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.953282] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.953727] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2499.953729] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.154853] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.154854] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.155236] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.155238] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.155483] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:08 patrick-desktop kernel: [ 2500.155484] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.356342] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.356343] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.356652] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.356653] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507258] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507259] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507287] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507288] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507647] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.507648] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.508099] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.508100] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557679] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557681] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557705] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557706] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557856] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.557857] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.558190] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.558191] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.558364] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:09 patrick-desktop kernel: [ 2500.558365] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398054] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398056] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398394] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398396] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398627] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.398627] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399170] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399172] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399338] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399339] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399490] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399491] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399845] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.399846] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.498976] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.498978] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.700440] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.700442] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.700643] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.700644] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.901873] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2501.901875] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.203921] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.203923] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.204625] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.204626] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.205143] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.205144] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.206618] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.206619] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.206927] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.206929] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207175] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207177] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207447] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207448] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207615] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207616] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207946] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.207947] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208235] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208237] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208508] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208509] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208941] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.208942] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209373] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209374] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209663] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209664] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209935] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.209936] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.210204] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.210205] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.210613] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.210614] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.211173] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:10 patrick-desktop kernel: [ 2502.211175] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.405795] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.405796] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.406073] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.406074] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.506510] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.506512] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508086] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508087] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508473] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508475] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508866] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.508867] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.510084] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.510085] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.510438] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.510439] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708030] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708031] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708385] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708386] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708730] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.708731] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.709183] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.709184] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.709355] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2502.709355] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.010237] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.010238] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.013528] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.013530] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.015525] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.015527] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.017460] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.017461] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.017846] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.017847] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.018141] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.018142] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.018576] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.018577] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.019062] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.019063] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163346] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163348] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163422] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163423] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163710] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.163710] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164140] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164142] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164329] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164330] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164738] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164739] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164968] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:11 patrick-desktop kernel: [ 2503.164969] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.717264] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.717266] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.720506] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.720507] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.720700] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.720701] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.866828] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.866830] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.899361] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.899362] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.968760] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:12 patrick-desktop kernel: [ 2503.968762] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2504.624282] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2504.624284] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.027021] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.027023] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.046787] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.046789] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048399] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048400] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048610] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048611] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048961] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.048962] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049254] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049255] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049642] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049643] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049970] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:13 patrick-desktop kernel: [ 2505.049971] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:14 patrick-desktop kernel: [ 2505.882778] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:14 patrick-desktop kernel: [ 2505.882780] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:14 patrick-desktop kernel: [ 2505.883003] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:14 patrick-desktop kernel: [ 2505.883004] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:15 patrick-desktop kernel: [ 2506.889593] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:15 patrick-desktop kernel: [ 2506.889594] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:15 patrick-desktop kernel: [ 2506.889623] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:15 patrick-desktop kernel: [ 2506.889624] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.392891] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.392892] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393037] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393038] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393486] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393488] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393814] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.393816] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.394027] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.394033] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.594451] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2507.594452] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.047760] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.047762] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199011] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199012] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199213] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199215] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199944] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:16 patrick-desktop kernel: [ 2508.199945] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.299921] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.299923] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.299997] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.299998] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.300426] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.300427] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.300835] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.300836] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.334869] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.334870] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.336714] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.336715] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.337159] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.337161] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350479] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350480] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350524] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350525] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350711] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.350712] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.605503] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.605505] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.606078] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.606079] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.981681] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.981683] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.981868] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:17 patrick-desktop kernel: [ 2508.981869] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2509.233788] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2509.233790] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090265] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090267] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090388] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090389] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090581] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090582] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090755] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.090756] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091107] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091109] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091396] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091397] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091845] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.091847] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.190981] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.190983] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.191546] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.191547] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.192020] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:18 patrick-desktop kernel: [ 2510.192021] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443003] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443005] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443541] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443543] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443870] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.443871] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.444214] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.444215] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.444462] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:19 patrick-desktop kernel: [ 2510.444463] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.903947] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.903948] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.905828] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.905829] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906092] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906093] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906436] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906437] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906681] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906682] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906949] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.906950] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907270] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907271] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907616] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907617] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907881] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.907881] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908284] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908285] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908571] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908572] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908904] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.908905] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.909115] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.909116] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.909384] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.909385] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.955454] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.955455] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.955997] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2511.955998] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2512.156186] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2512.156187] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:20 patrick-desktop kernel: [ 2512.156959] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:20 patrick-desktop kernel: [ 2512.156960] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408253] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408254] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408292] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408293] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408734] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.408735] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.409168] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.409169] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.409476] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2512.409477] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:21 patrick-desktop kernel: [ 2513.113262] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:21 patrick-desktop kernel: [ 2513.113263] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.567172] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.567174] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818464] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818466] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818516] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818517] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818910] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2513.818911] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.120604] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.120605] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.120894] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.120896] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121057] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121058] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121387] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121388] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121842] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:22 patrick-desktop kernel: [ 2514.121843] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.484112] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.484114] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.506551] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.506553] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.506984] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.506985] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507207] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507208] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507533] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507534] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507941] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.507942] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.508587] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.508588] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.508759] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.508760] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509165] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509166] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509412] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509413] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509930] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2514.509931] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:23 patrick-desktop kernel: [ 2515.026507] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:23 patrick-desktop kernel: [ 2515.026508] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.229165] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.229167] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231000] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231001] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231148] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231149] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231612] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.231614] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.430758] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.430760] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.430835] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:24 patrick-desktop kernel: [ 2515.430835] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.286780] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.286782] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.286902] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.286903] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.287427] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.287429] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.438087] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.438088] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.438127] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.438128] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.454565] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.454566] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.790616] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.790618] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.790637] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.790638] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791079] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791080] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791250] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791252] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791423] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:25 patrick-desktop kernel: [ 2516.791424] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.402156] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.402158] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406059] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406060] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406247] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406248] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406951] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.406952] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.407304] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.407305] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408014] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408015] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408268] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408269] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408600] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408601] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408913] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.408914] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.409327] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.409328] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.817996] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.817998] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.818165] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:26 patrick-desktop kernel: [ 2517.818167] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:27 patrick-desktop kernel: [ 2519.006999] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:27 patrick-desktop kernel: [ 2519.007001] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:27 patrick-desktop kernel: [ 2519.007119] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:27 patrick-desktop kernel: [ 2519.007120] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:29 patrick-desktop kernel: [ 2520.734215] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:29 patrick-desktop kernel: [ 2520.734217] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:29 patrick-desktop kernel: [ 2520.918080] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:29 patrick-desktop kernel: [ 2520.918082] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:29 patrick-desktop kernel: [ 2521.114369] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:29 patrick-desktop kernel: [ 2521.114371] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:29 patrick-desktop kernel: [ 2521.116436] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:29 patrick-desktop kernel: [ 2521.116437] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.314249] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.314250] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.314371] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.314372] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.315791] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.315792] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.316526] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.316527] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.316859] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.316860] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.317148] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.317149] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.716912] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.716913] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.718213] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.718214] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.718580] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.718581] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.719484] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.719485] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.719872] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.719873] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720137] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720138] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720390] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720391] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720614] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720615] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720768] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2521.720769] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.068735] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.068737] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.070693] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.070695] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.071386] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.071387] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.072879] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.072880] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.073326] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.073327] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.073895] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.073896] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.074243] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.074244] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075190] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075191] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075336] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075337] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075781] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.075783] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.076247] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.076248] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.076620] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.076621] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077051] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077052] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077247] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077248] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077488] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077489] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077685] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.077686] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.219817] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:30 patrick-desktop kernel: [ 2522.219818] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.320380] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.320381] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.320591] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.320592] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.521838] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.521840] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.521992] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.521993] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522165] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522166] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522540] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522791] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.522792] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.523105] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.523106] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.723575] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.723577] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.723626] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.723627] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724094] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724095] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724330] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724331] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724900] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:31 patrick-desktop kernel: [ 2522.724901] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.328445] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.328446] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.832276] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.832277] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.992527] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2523.992529] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.012099] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.012100] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.012638] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.012639] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.013299] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.013300] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.013897] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:32 patrick-desktop kernel: [ 2524.013898] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.688932] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.688934] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.689086] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.689087] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.689519] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.689520] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.940979] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:33 patrick-desktop kernel: [ 2524.940981] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.495005] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.495007] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.797000] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.797001] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.797216] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.797217] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.897872] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.897874] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.948233] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:34 patrick-desktop kernel: [ 2525.948234] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2526.804515] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2526.804516] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2526.804807] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2526.804808] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.056113] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.056115] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.058877] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.058879] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.060746] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.060747] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061316] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061317] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061666] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061667] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061857] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:35 patrick-desktop kernel: [ 2527.061858] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2527.560750] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2527.560752] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2527.560962] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2527.560963] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.114740] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.114741] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165087] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165088] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165356] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165357] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165787] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165788] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165955] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.165956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166147] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166148] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166478] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166479] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166931] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:36 patrick-desktop kernel: [ 2528.166932] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.417100] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.417102] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.543518] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.543520] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.546123] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.546125] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.549528] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.549529] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.550324] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.550325] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551013] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551014] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551589] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551590] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551855] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.551856] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.552219] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.552220] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.552552] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.552553] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.570587] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.570589] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571390] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571391] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571848] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571849] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571996] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:37 patrick-desktop kernel: [ 2528.571997] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.823861] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.823863] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.824085] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.824086] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.824394] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.824395] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874337] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874339] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874433] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874434] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874722] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.874723] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.875054] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2529.875055] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025352] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025354] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025556] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025557] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025740] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.025741] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.026024] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.026025] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.027973] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.027975] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.028267] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.028268] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.028958] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.028959] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029106] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029107] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029378] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029379] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029713] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029714] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029882] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.029883] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030230] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030231] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030463] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030464] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030788] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.030789] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.137584] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:38 patrick-desktop kernel: [ 2530.137586] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.630141] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.630142] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.766017] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.766019] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.766929] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.766930] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.767805] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.767806] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.768152] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.768153] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.831831] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.831832] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.831949] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.831950] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832178] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832179] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832587] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832588] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832776] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:39 patrick-desktop kernel: [ 2530.832777] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2531.412022] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2531.412024] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2531.412251] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2531.412252] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199003] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199004] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199306] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199307] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199747] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199748] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199898] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.199899] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200150] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200151] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200380] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200381] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200773] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.200774] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201159] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201160] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201403] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201404] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201626] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201627] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201919] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.201921] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202248] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202249] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202514] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202515] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202943] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.202944] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.203252] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.203253] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.203521] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.203522] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.204672] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.204673] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.209478] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.209479] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.210901] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.210902] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.213617] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.213618] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.214890] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.214891] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.218258] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.218259] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.219554] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.219555] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.220562] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.220563] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221054] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221055] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221487] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221489] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221916] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.221917] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.222063] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.222064] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.222416] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:40 patrick-desktop kernel: [ 2532.222417] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.222763] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.222764] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223067] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223068] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223460] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223461] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223853] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.223854] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224147] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224149] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224543] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224544] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224896] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.224897] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225141] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225142] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225297] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225298] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225611] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225612] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225984] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.225985] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226132] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226133] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226285] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226286] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226738] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.226739] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.227172] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.227173] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.227581] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.227582] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228145] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228146] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228631] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228632] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228777] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.228778] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229228] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229229] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229722] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229723] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229914] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.229915] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230207] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230208] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230415] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230417] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230849] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.230851] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231198] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231199] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231354] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231355] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231744] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231745] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231955] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.231956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.232325] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.232326] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.232754] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.232756] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233084] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233085] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233456] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233457] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233636] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.233637] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.234014] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.234015] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.235936] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.235937] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237142] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237143] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237292] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237293] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237726] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.237727] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238059] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238061] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238452] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238453] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238744] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.238746] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239134] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239135] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239487] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239488] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239719] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.239720] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240167] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240169] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240355] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240356] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240630] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240631] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240898] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.240899] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.241171] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.241172] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.241623] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.241624] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.242072] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.242073] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243163] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243164] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243412] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243413] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243825] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.243826] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244218] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244219] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244444] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244445] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244819] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.244820] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245272] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245273] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245624] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245625] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245837] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245838] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245988] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.245989] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.246441] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.246442] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.246749] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.246751] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247159] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247160] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247468] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247469] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247741] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.247742] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248194] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248195] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248627] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248628] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248896] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.248897] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249180] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249181] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249330] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249331] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249562] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249563] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249971] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.249972] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250220] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250221] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250413] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250414] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250767] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.250768] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251099] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251100] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251531] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251532] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251699] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251700] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251954] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.251954] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.252447] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.252448] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.252919] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.252921] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.253353] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.253354] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.253746] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.253747] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254023] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254024] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254204] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254205] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254576] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254577] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254797] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254798] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254966] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.254967] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255335] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255337] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255490] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255491] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255752] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.255753] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256101] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256102] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256451] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256452] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256860] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.256861] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257033] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257034] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257281] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257709] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257710] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257958] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.257959] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258112] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258113] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258486] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258487] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258635] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.258636] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259008] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259010] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259540] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259779] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.259780] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.260206] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.260207] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.260555] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.260556] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261008] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261009] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261361] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261362] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261731] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.261732] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262231] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262232] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262564] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262565] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262771] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.262772] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263202] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263203] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263474] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263475] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263666] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263667] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263936] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.263937] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264211] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264212] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264426] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264426] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264698] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.264699] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265132] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265134] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265571] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265572] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265875] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.265876] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.266047] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.266048] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268004] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268005] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268432] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268433] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268684] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.268686] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269061] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269063] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269285] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269286] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269660] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.269661] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270108] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270109] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270281] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270639] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270640] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.270999] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.271000] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.271556] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.271557] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.271704] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.271705] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272093] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272094] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272505] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272506] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272758] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.272759] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273195] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273196] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273539] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273768] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273768] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273940] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.273941] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.274130] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.274131] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.274558] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.274559] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275015] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275016] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275344] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275345] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275769] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.275770] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276005] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276006] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276355] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276356] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276791] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276792] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276936] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.276937] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277347] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277348] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277712] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277713] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277919] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.277920] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278084] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278084] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278337] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278338] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278630] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278632] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278956] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.278957] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279160] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279161] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279348] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279349] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279614] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279616] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279784] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279785] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279968] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.279969] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280173] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280174] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280389] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280390] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280654] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280655] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280901] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.280902] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.281289] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.281290] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.281458] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.281459] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.283184] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.283185] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.283754] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.283755] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284038] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284039] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284205] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284206] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284542] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284543] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284909] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.284910] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285158] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285159] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285426] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285427] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285800] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.285801] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286168] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286169] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286360] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286361] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286610] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286611] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286931] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.286932] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287195] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287196] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287628] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287629] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287830] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.287831] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.288023] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.288024] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.288472] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.288473] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.289154] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.289155] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.289539] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.289540] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.301593] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.301594] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.301784] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.301785] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.302150] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.302151] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.302357] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.302358] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.303343] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.303344] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.303856] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.303857] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304200] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304202] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304493] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304494] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304801] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.304802] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305040] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305041] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305439] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305440] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305583] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305584] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305914] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.305915] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306250] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306251] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306643] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306644] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306871] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.306872] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.307084] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.307085] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.582043] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:41 patrick-desktop kernel: [ 2532.582045] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2533.324117] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2533.324118] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2533.324319] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2533.324320] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.129500] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.129502] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.131303] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.131304] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.132311] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.132312] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.132503] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.132503] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.134251] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.134252] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.134562] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.134563] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.135016] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.135017] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.135970] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.135971] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.136554] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.136555] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.136827] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.136828] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.137017] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.137018] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.137369] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:42 patrick-desktop kernel: [ 2534.137370] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.280538] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.280540] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.438793] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.438794] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.454920] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.454922] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455224] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455225] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455636] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455637] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455928] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.455930] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.456541] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.456542] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.456935] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.456936] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457228] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457229] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457541] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457542] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457865] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.457867] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458019] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458020] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458303] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458304] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458549] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.458550] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.459002] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.459003] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.459265] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.459266] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.582839] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.582841] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.582971] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.582972] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.583321] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.583322] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.583774] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.583776] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.584106] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.584108] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.744686] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.744688] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.756300] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.756301] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757094] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757095] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757446] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757447] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757815] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.757816] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758205] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758206] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758404] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758405] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758540] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758805] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.758806] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759190] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759192] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759523] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759524] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759727] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.759728] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760113] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760114] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760419] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760420] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760621] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2534.760622] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.036793] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.036795] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.037747] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.037749] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.038093] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.038094] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.056634] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.056635] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062004] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062005] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062592] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062593] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062737] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.062738] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063306] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063308] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063510] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063511] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063828] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:43 patrick-desktop kernel: [ 2535.063829] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:44 patrick-desktop kernel: [ 2535.641107] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:44 patrick-desktop kernel: [ 2535.641108] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:44 patrick-desktop kernel: [ 2535.641260] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:44 patrick-desktop kernel: [ 2535.641261] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.102667] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.102668] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.103438] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.103439] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.103727] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.103728] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.104091] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.104092] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.104521] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:45 patrick-desktop kernel: [ 2537.104522] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.210975] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.210976] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.211185] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.211187] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.211977] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:46 patrick-desktop kernel: [ 2538.211978] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:47 patrick-desktop kernel: [ 2539.167293] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:47 patrick-desktop kernel: [ 2539.167295] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:47 patrick-desktop kernel: [ 2539.167514] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:47 patrick-desktop kernel: [ 2539.167516] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:48 patrick-desktop kernel: [ 2539.673049] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:48 patrick-desktop kernel: [ 2539.673050] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277154] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277155] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277215] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277216] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277443] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.277444] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.428796] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.428798] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429090] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429091] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429477] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429478] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429770] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.429771] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.430001] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.430002] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.629970] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.629972] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.630250] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.630251] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.630591] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.630592] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.631023] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.631024] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.631435] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.631437] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.885549] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:49 patrick-desktop kernel: [ 2540.885551] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.289836] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.289838] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.290137] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.290138] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.290509] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.290510] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.893906] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.893908] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.894063] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.894065] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.894772] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.894773] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895025] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895026] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895217] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895218] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895429] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:50 patrick-desktop kernel: [ 2541.895430] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:51 patrick-desktop kernel: [ 2542.397374] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:51 patrick-desktop kernel: [ 2542.397376] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.004457] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.004458] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.105033] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.105034] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.105118] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:51 patrick-desktop kernel: [ 2543.105119] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:52 patrick-desktop kernel: [ 2543.306449] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:52 patrick-desktop kernel: [ 2543.306451] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.372252] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.372254] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.822898] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.822900] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.822931] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.822932] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.823468] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.823470] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.823617] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.823618] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824066] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824067] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824497] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824498] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824791] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.824792] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.825204] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:53 patrick-desktop kernel: [ 2544.825205] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:54 patrick-desktop kernel: [ 2545.578270] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:54 patrick-desktop kernel: [ 2545.578272] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:54 patrick-desktop kernel: [ 2545.578301] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:54 patrick-desktop kernel: [ 2545.578302] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:54 patrick-desktop kernel: [ 2546.031506] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:54 patrick-desktop kernel: [ 2546.031507] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2546.365554] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2546.365556] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2546.365921] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2546.365922] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.087550] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.087551] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188220] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188222] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188645] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188646] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188788] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:55 patrick-desktop kernel: [ 2547.188789] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.238676] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.238678] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.238793] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.238794] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.239242] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.239243] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.340971] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.340973] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.341513] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.341514] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.343611] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.343612] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.343865] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.343866] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.345893] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.345894] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346061] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346062] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346214] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346215] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346852] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.346853] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.347104] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.347105] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.347438] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:56 patrick-desktop kernel: [ 2547.347439] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.346312] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.346314] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.396877] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.396879] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.447272] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:57 patrick-desktop kernel: [ 2548.447273] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:58 patrick-desktop kernel: [ 2549.404106] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:58 patrick-desktop kernel: [ 2549.404108] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.726801] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.726802] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733110] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733111] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733554] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733555] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733939] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.733940] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734323] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734324] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734708] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734709] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734912] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.734913] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735137] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735138] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735543] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735544] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735748] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2550.735749] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199673] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199675] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199710] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199711] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199980] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.199981] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.200488] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.200489] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.200840] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:52:59 patrick-desktop kernel: [ 2551.200842] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.300404] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.300406] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.701831] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.701832] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.701968] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.701969] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.702217] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.702218] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.702650] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.702651] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.753097] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.753098] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.758335] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.758336] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759033] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759035] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759280] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759281] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759529] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759530] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759898] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.759899] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760210] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760211] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760663] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760664] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760957] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.760958] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.802705] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.802706] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.802925] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.802926] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.953594] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.953595] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.953624] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:00 patrick-desktop kernel: [ 2551.953625] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.557583] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.557584] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.557846] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.557847] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.558009] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.558010] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.558353] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2552.558354] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.175703] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.175705] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.176230] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.176232] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.200540] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.200541] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.203292] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.203294] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.204478] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.204479] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.209847] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.209848] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.210316] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.210317] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.210894] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.210895] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211299] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211300] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211644] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211645] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211808] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.211809] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.213609] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.213610] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.213873] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.213874] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214039] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214040] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214243] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214244] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214608] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.214610] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.215053] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:01 patrick-desktop kernel: [ 2553.215054] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215418] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215419] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215621] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215622] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215948] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.215949] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.216352] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.216353] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.216617] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.216618] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217006] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217008] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217230] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217231] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217656] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217657] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217859] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.217860] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218034] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218035] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218359] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218360] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218503] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218504] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218758] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.218759] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219034] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219035] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219339] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219340] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219585] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.219586] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.613988] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.613989] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614088] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614089] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614418] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614419] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614830] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:02 patrick-desktop kernel: [ 2553.614831] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:03 patrick-desktop kernel: [ 2554.593138] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:03 patrick-desktop kernel: [ 2554.593140] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:03 patrick-desktop kernel: [ 2554.620396] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:03 patrick-desktop kernel: [ 2554.620397] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.648178] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.648180] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828086] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828088] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828195] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828196] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828423] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828424] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828815] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.828816] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.829272] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.829273] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.928921] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.928922] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.936508] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.936509] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.936933] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.936934] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937266] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937268] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937419] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937420] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937608] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937608] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937899] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.937900] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.938597] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.938598] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940089] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940090] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940398] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940399] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940670] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940671] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940883] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.940884] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.979347] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.979348] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.979909] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2555.979910] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.180704] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.180706] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.181150] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.181151] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.181513] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.181514] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.182625] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.182627] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.183417] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.183418] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.183675] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.183676] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.184009] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:04 patrick-desktop kernel: [ 2556.184010] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.237292] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.237294] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.238876] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.238878] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.239324] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.239325] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.634267] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.634269] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.634441] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.634442] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.986568] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:05 patrick-desktop kernel: [ 2556.986569] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339059] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339061] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339100] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339101] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339251] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.339252] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.894713] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.894715] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.895311] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.895312] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.895564] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.895565] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.896012] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:06 patrick-desktop kernel: [ 2557.896013] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.700778] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.700780] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.702298] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.702299] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.702729] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2558.702730] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.002981] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.002983] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003044] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003045] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003447] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003449] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003657] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.003658] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004153] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004154] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004497] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004498] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004701] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.004702] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.006704] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:07 patrick-desktop kernel: [ 2559.006705] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2559.314226] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2559.314228] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010240] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010242] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010407] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010408] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010732] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.010733] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011077] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011078] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011385] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011386] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011683] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011684] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011948] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.011949] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.012241] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.012242] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.012534] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:08 patrick-desktop kernel: [ 2560.012535] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.815905] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.815906] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816161] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816162] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816528] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816529] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816941] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2560.816942] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2561.155081] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2561.155082] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:09 patrick-desktop kernel: [ 2561.155264] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:09 patrick-desktop kernel: [ 2561.155265] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:10 patrick-desktop kernel: [ 2562.061123] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:10 patrick-desktop kernel: [ 2562.061124] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:10 patrick-desktop kernel: [ 2562.063503] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:10 patrick-desktop kernel: [ 2562.063504] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.413954] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.413956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414113] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414114] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414522] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414524] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414673] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414674] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414968] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.414969] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.716821] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.716822] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867425] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867427] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867732] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867734] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867900] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.867901] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.868106] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.868107] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.868421] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:11 patrick-desktop kernel: [ 2562.868422] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.270643] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.270645] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.270965] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.270966] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.271299] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.271300] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.272020] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.272021] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.522729] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.522731] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775095] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775097] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775425] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775427] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775958] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:12 patrick-desktop kernel: [ 2563.775959] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.227768] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.227769] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228217] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228218] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228406] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228407] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228615] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228616] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228864] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.228865] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.229197] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.229199] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.229409] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.229410] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.278325] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.278326] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.580700] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.580702] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.580846] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.580847] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.581200] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.581201] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883133] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883135] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883625] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883626] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883815] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:13 patrick-desktop kernel: [ 2564.883816] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839181] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839182] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839319] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839321] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839503] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839504] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839755] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2565.839756] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.191933] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.191934] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.199598] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.199599] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200041] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200042] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200286] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200287] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200430] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200431] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200655] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.200655] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201191] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201192] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201396] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201397] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201565] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201566] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201835] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:14 patrick-desktop kernel: [ 2566.201836] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.494292] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.494293] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.494590] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.494591] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495019] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495020] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495207] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495208] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495946] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.495947] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.646217] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.646218] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.650389] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:15 patrick-desktop kernel: [ 2566.650390] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:16 patrick-desktop kernel: [ 2568.209455] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:16 patrick-desktop kernel: [ 2568.209457] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.219687] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.219688] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.219956] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.219957] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.220328] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.220329] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.360613] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.360615] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.360656] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:17 patrick-desktop kernel: [ 2568.360657] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.367876] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.367878] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.367929] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.367930] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369316] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369317] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369557] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369558] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369786] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.369787] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370119] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370120] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370267] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370268] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370480] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370480] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370771] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.370772] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.771065] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2569.771067] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174230] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174231] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174312] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174313] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174760] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.174761] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.176132] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.176133] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177177] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177178] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177462] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177463] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177807] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:18 patrick-desktop kernel: [ 2570.177808] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.292608] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.292610] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.292690] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.292691] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.292999] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.293000] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.293199] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.293200] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.293605] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.293606] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343046] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343047] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343309] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343311] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343638] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:21 patrick-desktop kernel: [ 2572.343639] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.551453] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.551454] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.556080] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.556082] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.556423] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.556424] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.760554] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.760555] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.810932] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.810933] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.811504] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.811505] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.811852] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.811853] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.812484] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:22 patrick-desktop kernel: [ 2573.812485] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:23 patrick-desktop kernel: [ 2574.213678] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:23 patrick-desktop kernel: [ 2574.213680] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:23 patrick-desktop kernel: [ 2574.213921] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:23 patrick-desktop kernel: [ 2574.213922] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.119070] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.119072] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.120683] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.120685] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.121031] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:23 patrick-desktop kernel: [ 2575.121032] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.680706] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.680707] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.681081] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.681083] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.681687] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.681688] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.936991] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.936993] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.937402] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.937404] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942079] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942080] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942431] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942432] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942818] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.942819] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943248] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943249] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943697] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943698] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943905] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:24 patrick-desktop kernel: [ 2575.943906] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.009603] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.009605] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.010743] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.010744] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.010949] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.010950] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.011181] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.011182] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.011330] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.011331] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110407] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110409] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110526] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110527] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110671] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:27 patrick-desktop kernel: [ 2579.110672] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:28 patrick-desktop kernel: [ 2579.771024] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:28 patrick-desktop kernel: [ 2579.771026] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:28 patrick-desktop kernel: [ 2579.774632] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:28 patrick-desktop kernel: [ 2579.774633] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:29 patrick-desktop kernel: [ 2581.099999] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:29 patrick-desktop kernel: [ 2581.100001] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.509775] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.509776] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.511035] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.511037] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.761708] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.761709] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.765257] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.765258] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.765819] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.765820] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766056] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766057] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766379] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766381] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766729] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2582.766730] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2583.013603] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2583.013604] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:31 patrick-desktop kernel: [ 2583.164910] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:31 patrick-desktop kernel: [ 2583.164911] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.265732] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.265734] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.265963] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.265964] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.769538] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.769539] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.769853] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:32 patrick-desktop kernel: [ 2583.769854] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.532955] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.532956] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533043] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533044] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533410] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533411] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533742] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.533743] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.534096] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.534097] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.534838] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2585.534839] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:34 patrick-desktop kernel: [ 2586.187892] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:34 patrick-desktop kernel: [ 2586.187893] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.340063] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.340065] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.340538] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.340539] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.490133] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.490134] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.490467] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.490469] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.657207] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.657209] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.950646] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.950648] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.959137] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.959138] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.960705] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.960706] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961144] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961145] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961336] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961337] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961987] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.961988] Please file bug report to http://rt2x00.serialmonkey.com.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.962399] phy0 -> rt2x00pci_write_tx_data: Error - Arrived at non-free entry in the non-full queue 2.
Jun  1 14:53:35 patrick-desktop kernel: [ 2586.962400] Please file bug report to http://rt2x00.serialmonkey.com.
```
hope this can help someone. 

i am running 
Hardy Heron
kernel 2.6.24-17
nvidia 8800 GTS w/ resricted drivers (these have only caused an issue on one day, when the xorg.config would reset to default everytime my comp froze because of bittorrent)
ndiswrapper - rt61pci driver

---

### Post by minibeardeath on 2008-06-07
still haveing the problem w/ kernel -19, but it was fine w/ kernel -18.

---

### Post by defmomo on 2008-06-08
That's strange, the only kernel that worked well for me was -16, all the rest kept freezing on me.

---

### Post by trunip190 on 2008-06-09
i'm still having problems with my install, but i'm gonna try and clean install again.

---

### Post by minibeardeath on 2008-06-10
> **minibeardeath said:**
> still haveing the problem w/ kernel -19, but it was fine w/ kernel -18.
actually i mixed that up, it works (sort of) in 19 and not at all in 18.


i have discovered several things that "trigger" the freeze. 
1) setting the number of allowed connections too low will cause a freeze (mine is set to 6000 global, 500 incoming per torrent, 180 outgoing per torrent; and i can safely run 2 torrents so long as none of the conditions below occur), setting any value to zero will cause a freeze after a random length of time.
2) running *any* form of multimedia (music, video...) from either: A) the drive on which the torrents are being placed (the external in my case), or B) the primary drive.
3) watching or listening to any multimedia that is streaming on the internet. (also, just loading a web page that is very large can cause the freeze)

here are my theories as to the root of the problem.
1) the kernel and/or network card has trouble processing and infinite # of connections
2) the kernel/network card has trouble processing high bandwidth connections from multiple sources (eg. using torrent and youtube)
3) there is some inherint conflict between the torrent program and the multimedia applications.

if anyone has anything to add to help us solve the problem, any help is welcome.

now a bit of good news. last night, whilst downloading the xubuntu iso, i was able to achieve a whopping 1.5 mbps (sustained) on a wifi connection that claim to be a 1 mbps connections:). also, i achieved a peak speed of 2.01 mbps on that same connection!!! (then i tried to watcha youtube movie and the whole thing froze)

edit: i installed kernel -14 from a liveCD, and all later kernels were installed using the update manager. i am running Ubuntu with GNOME only

---

### Post by defmomo on 2008-06-11
You are still getting freezes with kernel -14?

---

### Post by minibeardeath on 2008-06-12
> **defmomo said:**
> You are still getting freezes with kernel -14?

sorry i meant later instead of previous.
currently, i am using deluge bittorrent client, and i have had no torrent related freezes (knock on wood) while running 3 torrents active @ a time.
i will edit my previous post

---

### Post by killstheweak on 2008-07-15
Decided to run update sense mine was working, and the problem came back, the kernel developers have to know whats wrong with it, as its broke than fixed, broke than fixed, than broke, etc....

EDIT: Forgot i booted into the realtime kernel, which i've yet to see fixed, generic one works fine for torrents.

---

### Post by dbarbour on 2008-07-20
Removed Transmission and went with Deluge. All seems fine now.

---

