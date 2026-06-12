---
title: "*extremely* slow after RAM cache is built"
date: 2007-12-07
forum: General Help
---

### Post by puargs on 2007-12-07
I have Ubuntu desktop "gutsy gibbon"... New to linux as of a month or so ago, I'm still lacking familiarity at this point, so I built this computer to be able to use linux well. AMD 3200+, 512MB of RAM, Nvidia Geforce 6100. 80 gig hard drive with ~1200 megs of swap space (auto-configured by the Ubuntu installer).

Anyway, the problem is this- when using linux, the RAM cache starts getting built up; once it hits the 512 meg mark and starts to use the swap file, everything goes to pot. (I know the RAM caching and swap usage is normal, I know that linux automatically stores everything it has accessed in RAM - caching is basically "always good", or so I've heard). The computer just GRINDS to a slow pace, unbelievably slow. The mouse cursor itself is even bouncing around the screen slowly.

CPU usage remains low, and actually memory usage remains low. It just seems that if I have ubuntu running for any period of time in which I am actively downloading/working with files, it eventually grinds to a halt. System is also unresponsive to SSH attempts from the network.


Any idea why this is happening? The hard drive seems to be working just fine, and loading quickly, the RAM seems to be working just fine... maybe I'm missing something?
(edit: sorry, let me specify- this problem occurs ALWAYS when it starts to use the swap partition. If it's just using the RAM, it's fine until about that ~500 meg mark. That is not *running process* memory, just cache memory. I am not doing anything nearly intensive enough to utilize all 512 megs of ram.)

---

### Post by puargs on 2007-12-07
I went through about a bazillion threads since posting and couldn't find something similar (I might be looking for the wrong things??) Anyone have any idea?

---

### Post by ~LoKe on 2007-12-07
What kind of apps are you running?  I rarely ever used up more than 512MB's of RAM.  Something doesn't seem quite right if it's already hitting your page file.  And yes, the swap usage will cause things to be slow, it's like "virtual" ram to keep your computer from locking up completely.

---

### Post by puargs on 2007-12-07
There isn't more than 200 megs worth of ACTIVE programs in RAM at any given time. If I view htop, it tells me only like 150-200 is in actual use, the rest is just cache.

Here's the situation as it happens:
1) Boot computer, runs great.
2) Fart around a bit, RAM usage goes slightly up.
3) Start installing updates/using synaptic manager for something in the background.
4) RAM hits 512 meg mark, system slows way the hell down.
5) Install *finishes*, all programs closed except, say, firefox.
6) Active programs now only use about 150 megs of RAM, but STILL USING SWAP MEMORY.
7) System is slow as crap. No way to get it to work properly again unless I reboot. I cry a little inside and go watch tv while I wait on system reboot so I start all over again.

---

### Post by Zeratul7 on 2007-12-09
I have the exact same problem with 1GB ram and I am searching for a solution.

---

### Post by Zeratul7 on 2007-12-11
I uninstalled all the "tracker" stuff and then it seems to run better.

---

### Post by skymera on 2007-12-11
wow thats strange, maxing out your RAM then swapping?

i never go over 250mb ram usage really, and dont have a swap.

but one time i did fill my RAM with something, games, browing etc.

as soon as it started to swap, total system lagg, very bad lagg.
cursor wouldnt move, then all my progs closed down and worked fine.

perhaps a bug?

---

### Post by quadomatic on 2007-12-11
I'm having this very same problem. I'm not sure exactly what's causing it, but my symptoms sound very similar to yours.

Usually, I can boot my system, and then everything works peachy. Then, once I start doing stuff thats memory intensive, like using Firefox and Thunderbird, or watching videos, after a little while, my system starts going slower, and my PC's hard drive is reading a lot (orange light going off). Eventually, it just slows down so much that I can't move my mouse much at all. It bounces around like it's running like a slideshow. I have to hit my reset button to get out of it.

My programs DON'T close.

Does anyone have an idea why this is happening? Maybe our swap files got screwed up or something. I think this is more of a recent development for me.

---

### Post by Ashrael on 2007-12-17
[http://ubuntuforums.org/showthread.php?p=3961619#post3961619](http://ubuntuforums.org/showthread.php?p=3961619#post3961619)

My dmesg output (post #381).....

I seem to have the same over here, my cache fills up slowly, hitting a whopping 80% of my 1 Gig ram!
Then it starts doing a lot of hd activity, i am assuming it's swapping, for about 5 minutes!!! during which it goes totally irresponsive, not reacting even to <ctrl-alt-backspace>...or <ctrl-alt-F1> etc..
Five minutes (give or take) after that it reacts normal again... I have it especially when using firefox so far.

Since de-installing evms it works a little better, or rather: it fills up slower...see: 
[http://www.devlib.org/forums/memory-leak-gutsy-t2506.html?](http://www.devlib.org/forums/memory-leak-gutsy-t2506.html?)

and:

[http://www.squarefree.com/2007/09/20/firefox-memory-usage-and-memory-leak-news/](http://www.squarefree.com/2007/09/20/firefox-memory-usage-and-memory-leak-news/)

HTH

---

### Post by cmost on 2007-12-17
I'm sorry if I seem daft, but isn't the point of having RAM to use it?  The cache socks away recently used files, libraries, etc. for rapid access later.  That's what it's supposed to do!   

The biggest place it's being used is in the disk cache.  This is reported by top as "cached". Cached memory is essentially free, in that it can be replaced quickly if a running (or newly starting) program needs the memory.

The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from the cache is around 1,000 times faster than getting it from the hard disk. If it's not found in the cache, the hard disk needs to be read anyway, but in that case nothing has been lost in time.

To see a better estimation of how much memory is really free for applications to use, run the command:
$free -m

The -/+ buffers/cache line shows how much memory is used and free from the perspective of the applications. Generally speaking, if little swap is being used, memory usage isn't impacting performance at all.

---

### Post by Dryw Paulic on 2007-12-17
Hi Puargs,

 Since you say that the ram seems to be mostly used for cache and not active applications, it would seem that you may need to change your swappiness settings.

Try adding the line:

```
vm.swappiness=0
```

To the bottom of /etc/sysctl.conf . This controls the degree to which the kernel swaps/frees memory. The range of values is between 0 and 100, 0 meaning that the kernel should try to avoid using the swap as much as possible and 100  meaning that it will use the swap considerably more. The default value in Ubuntu is 60. I currently use a value of 25 on my desktop system and I'm quite happy with it. I would try playing with a few values to see if there is a particular number that works for you.

You can take a look at free memory, swap files usage etc with the command "vmstat". It would be useful if you posted the output of vmstat before and after the problem occurs.

-Dryw

---

### Post by fjgaude on 2007-12-17
Thanks for the tip... few would know such insight and how such commands, eh?

---

### Post by muuramenian on 2007-12-17
Hi,
Thanks for the info, now for a beginner question:
This is my sysctl.conf, do i stick the bit of code in at the end there?
I did this once before to edit my keyboard layout, but this feels a little different, someone help me a little...

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

---

### Post by Dryw Paulic on 2007-12-17
Hi muuramenian,

Yeah, just drop the vm.swappiness=0 at the end of the file so it looks like:

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information. 
#

#kernel.domainname = [example.com]("http://example.com/")
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not 
# visible to other users.
kernel.maps_protect = 1

################################################## ############3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter) 
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1 

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

#Tell Kernel to avoid using swap if possible! Keep things in nice fast memory.
vm.swappiness=0 

```You may also want to experiment with different settings for the swapiness to see what works best on your system. Hopefully this solves your swap problem!

Cheers,
-Dryw

---

