---
title: "Bottlenecks...Any Suggestion's?"
date: 2022-04-11
forum: General Help
---

### Post by wyattwhiteeagle on 2022-04-11
Now that I'm beginning to "sober up" some of my Lubuntu 20.04 "drunkenness" to where it isn't "stumbling into so many walls".


I'm sure there are other issue's that I've missed.


But for now, I'm feeling the need to address performance bottlenecks of packages, applications and internet (Wifi).


I found this guide, it seem's pretty reasonable and thorough...
> 
Troubleshoot performance and isolate bottlenecks in Linux
[https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/troubleshoot-performance-bottlenecks-linux](https://docs.microsoft.com/en-us/troubleshoot/azure/virtual-machines/troubleshoot-performance-bottlenecks-linux)

What would ya'll suggest?

---

### Post by Autodave on 2022-04-11
Please give us some specs on your equipment.  Also, please give specifics of what you are running and what is happening.

---

### Post by guiverc on 2022-04-11
Ensure you have *swap* enabled...  See

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)
- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

I recall vividly still that I needed to take half (4GB of 8GB) of a boxes RAM to use it to test another box; and given how I used that box I didn't expect to see any performance difference - boy was I wrong !  The Lubuntu install on the box didn't have any *swap* enabled & it showed.  I quickly added a *swapfile* and the performance hit from the halving of RAM was gone..  Also note use an appropriate size of *swap* for your use cases; the `calamares` installer used by Lubuntu only allocates 512MB which is too small for the old (*low-resource*) boxes I use, and my use-cases.

Next is use *apps* that share resources when co-existing in RAM.  Lubuntu uses the LXQt desktop, thus it's using Qt5 libs. If your box is RAM limited (*in my own experience that's anything less than 5GB with how I use my machines*) this really matters, esp. if RAM is <4GB.  Libraries/Toolkits I'm thinking of here are more technical (*if it's microsoft windows or apple mac software (they use Qt5 too) they only mention you need more RAM & avoid the reasons why*).

Key first step would be check *swap* you're using, are you using any? and is it an appropriate size for your hardware & actual usage?

---

### Post by wyattwhiteeagle on 2022-04-11
> **guiverc said:**
> Ensure you have swap enabled... See


- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)
- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)


I recall vividly still that I needed to take half (4GB of 8GB) of a boxes RAM to use it to test another box; and given how I used that box I didn't expect to see any performance difference - boy was I wrong ! The Lubuntu install on the box didn't have any swap enabled & it showed. I quickly added a swapfile and the performance hit from the halving of RAM was gone.. Also note use an appropriate size of swap for your use cases; the `calamares` installer used by Lubuntu only allocates 512MB which is too small for the old (low-resource) boxes I use, and my use-cases.


Next is use apps that share resources when co-existing in RAM. Lubuntu uses the LXQt desktop, thus it's using Qt5 libs. If your box is RAM limited (in my own experience that's anything less than 5GB with how I use my machines) this really matters, esp. if RAM is <4GB. Libraries/Toolkits I'm thinking of here are more technical (if it's microsoft windows or apple mac software (they use Qt5 too) they only mention you need more RAM & avoid the reasons why).


Key first step would be check swap you're using, are you using any? and is it an appropriate size for your hardware & actual usage?


Following your How-to about creating an 8gb swapfile while using an 8gb partition...
I am using a 16gb swap total... see
```

$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       498Mi       2.7Gi        87Mi       640Mi       3.0Gi
Swap:          16Gi          0B        16Gi

```

---

### Post by wyattwhiteeagle on 2022-04-11
> **Autodave said:**
> Please give us some specs on your equipment.  Also, please give specifics of what you are running and what is happening.
I will update this post when I have those brief details
Please check back often

---

### Post by wyattwhiteeagle on 2022-04-12
> **Autodave said:**
> Please give us some specs on your equipment. Also, please give specifics of what you are running and what is happening.

Equipment Specs
```

    SYS     Dell Latitude E5400
    HDD
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2J
             serial: 16FYTXN9T
             size: 931GiB (1TB)
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                logical name: /dev/sda2
                logical name: /
                size: 923GiB
                capacity: 923GiB
    CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
          size: 1557MHz
          capacity: 2001MHz
          width: 64 bits
          clock: 200MHz
    RAM
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M4 70T5663QZ3-CF7
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
    Network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                version: 00
                serial: 00:22:fb:9f:2e:6a
                width: 64 bits
                clock: 33MHz
    Connection speeds
        6000 kb/s
    OS    Lubuntu 20.04 Focal Fossa
```
It moved pretty quickly at first.
I didn't start noticing the bottleneck until I installed extra stuff.

Things I install before the bottleneck...
```
# Bleachbit
# Baobab (Disk Usage Analyzer)
# Brave Browser
# rdiff-backup
# Stacer
# Timeshift
# Ubuntu-Restricted-Extras
# Wine-staging
# IMVU (in Wine)
# IMVU Cache-Cleaner (in Wine)
```
Things I installed just before noticing the bottleneck
```
# Artha (Dictionary & Thesaurus)
# Gnome-Chess
# Gnome-Paint
# gnome-sudoku
# KolourPaint
# Mines (Minesweeper)
# Aisleriot (Solitaire)
# Totem (Videos)
# Xboard (Chess)
```
Steps taken up to now.
These steps seem to have improved the bottlenecks a little.

1. Limited AutoStart Items

2. Reconfigured logs /etc/logrotate.d to...
```

    Daily
    rotate 0
    maxsize 10M
```

3. Disabled Boot Services (copied from script)
```

    apparmor.service
    apport.service
    avahi-daemon.service
    cgmanager.service
    ModemManager.service
    speech-dispatcher.service
    whoopsie.service
    pppd-dns.service
    udisks2.service
    networkd-dispatcher.service
    NetworkManager-wait-online.service
```

The following seem to be needed by GUI I chose to install...
```

    avahi-daemon.service
    udisks2.service
```

With only 4gb RAM, I created...
    8gb partition
    8gb swapfile
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       929Mi       1.3Gi       247Mi       1.6Gi       2.4Gi
Swap:          16Gi          0B        16Gi
```
There are some issue's with the DNS in the Wifi and web browser.
I get DNS_PROBE_POSSIBLE and other DNS messages.
Those issue's happen only at specific times of day from 3pm to 6pm.
Sometimes it goes all the way to 10pm.
A full 7 hours before my machine stops probing.
Because of this happening only at specific times of day, it causes me to believe it's more of a "general combined internet usage overload" caused by "after-school access".

Are there other things I might need to check?

---

### Post by dragonfly41 on 2022-04-13
Because you identify time patterns I would check if some external player is trying to gain access. [COLOR=#000000]"after-school access".[/COLOR]

Open a Home user (free) account with OpenDNS.

[https://www.opendns.com/home-internet-security/](https://www.opendns.com/home-internet-security/)

Inspect dashboard after setup (as documented).

---

### Post by wyattwhiteeagle on 2022-04-13
> **dragonfly41 said:**
> Because you identify time patterns I would check if some external player is trying to gain access. [COLOR=#000000]"after-school access".[/COLOR]

Open a Home user (free) account with OpenDNS.

[https://www.opendns.com/home-internet-security/](https://www.opendns.com/home-internet-security/)

Inspect dashboard after setup (as documented).

After looking at that link

This happens not only with my laptop, but also with my fiance's laptop, our echo dot (alexa), our 2 Roku devices, and sometime's my fiance's phone.
My phone isn't affected.
My ISP download usage is more than double what my upload usage is. (affects my monthly bill).

Should I go for the free family OpenDNS and which items?
I didn't look at the free sign up.
or should I check the ISP download usage loads then pursue OpenDNS?

---

### Post by dragonfly41 on 2022-04-13
I would start with the Free Home account to get a feel of how to use.
Then move to Free Family.
I remember that you are short of cash so draw a line there.
It is a useful service. 

Also separately check [GRCShieldsUp site]("https://www.grc.com/x/ne.dll?bh0bkyd2") to probe your site for security gaps (open ports etc.)

---

### Post by TheFu on 2022-04-13
> **wyattwhiteeagle said:**
> Following your How-to about creating an 8gb swapfile while using an 8gb partition...
I am using a 16gb swap total... see
```

$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       498Mi       2.7Gi        87Mi       640Mi       3.0Gi
Swap:          16Gi          0B        16Gi

```

I think this is a mistake.  Too much swap is just as bad as not enough.  On a modern Desktop - like any official flavor of Ubuntu, with certain assumptions, there is 1 answer for the size of swap.  4.1G.  Any less isn't enough with the bloated browsers. Any more and it is just wasted storage.
On a 4G RAM system, 4.1G is swap is ideal.

This recommendation is my own after lots of testing for systems with 2G, 4G, 8G, 16G and 32G of RAM.  There's 1 caveat. No hibernation, which shouldn't be used anyway. Hibernation has been deprecated. Use Standby mode instead, which freezes RAM and uses a tiny amount of battery/power to keep the RAM valid.

About 2 or 3 yrs ago, there was a very long thread in these forums about swap, the purpose, and optimal settings. Around that time, the kernel devs modified swap to be used internally for some very good reasons to actually improve performance.  Prior to then, on well understood workloads, it was best not to have ANY swap at all, if the system had all the RAM needed to service the workloads.  That changed about 3 yrs ago and having _some_ swap is needed to enable those kernel features now.  Not much, but some. On servers where I'd avoided having any swap at all, I now have 1G of swap.

**But on desktops, the answer is still 4.1G.**

The very old rules of thumb from the early 1990s haven't applied since our computers all got over 1G of RAM. Ignore any recommendations that are 2x or 3x the amount of RAM. That is much too simplistic and simply doesn't apply.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) I don't agree with all the recommendations. I think on the low end, crashes will happen. I've seen that on systems with less than 4G of swap.  On the high end, larger swap just isn't necessary. That isn't the point of swap.

And whenever anyone suggests using **gksu gedit** ... in your mind, you should see **sudoedit** as the command instead. There are many, many, reasons.  It isn't hard to use **gedit** as the default for **sudoedit**. This isn't about anyone's editor program preference. It is about security.

Swap is seldom really the first issue for performance.  The first step is to gather performance data. Capture a baseline for CPU, disk, network I/O. Gather FACTS before touching anything, not feelings.  Otherwise, you'll never actually know if a change improved the situation.  Many changes that are popular actually slow a system down. Get the baseline so you'll 100% KNOW that it is improving.

There are many different tools.  Typically, network I/O and disk I/O are the easiest to experience, but there are many different types of I/O for those subsystems.  Disks are used for tiny reads/writes and for huge reads/writes.  The tuning around those have conflicting settings.  Settings for dealing with video media files is very different from tuning for a DBMS or backup drive.  The storage, controller, cables, and tuning parameters for the storage all matter.  USB2, USB3, USB3.1, SATA, eSATA, SAS, Infiniband ... all have different strengths and weaknesses based on the type of data access nominal on that channel/partition.  Storage media - slow "Green" drives or very fast (expensive) NVMe x4 SSD storage makes a huge difference.  The goal is usually to balance the storage media type with the bus/controller so that the performance of the storage isn't limited by the bus at all.  For example, don't connect an NVMe SSD to a USB2 port.  That would be foolish.  Actually, connecting any NVMe SSD to any USB is pretty foolish, since NVMe can be 4x faster than USB 3.2.  OTOH, putting a SATA SSD into an m.2 slot that supports both SATA and NVMe isn't too smart either.  A SATA SSD can achieve 550 MB/s, so a SATA-3 port (6Gbps) would be sufficient and a SATA-2 port  (3Gbps) wouldn't be the end of the world, though it would limit performance.  But for any spinning HDD, SATA-1  (1.5Gbps) is fine. I think the fastest spinning disks might provide 250MB/s in ideal situations which I've never seen. 120MB/s (950 Mbps) is much more common and slower drives happen more often. 

Pay attention where it makes sense.

With networking, the same ideas arise, but there's a simple answer. **Avoid wifi.**  Wifi is prone to outside interference which nobody here or in your home can really control.  After disabling power-saving modes on the computer, most people aren't willing to actually do what's needed to improve wifi performance.  BTW, you can ignore whatever the box for the wifi (anything) said on the outside. You'll never get that speed. Never.  In fact, the speed that is listed on your computer as the "connection speed" is mostly a lie too.  If you care about network performance, don't use wifi.
Wired ethernet almost always provides excellent performance.  A 1Gbps router connected to a 1 Gbps computer over a proper CAT5e (or better) ethernet cable will achieve 920+ Mbps without any extra effort.  Some high end server NICs can get 940Mbps. Nobody will get 1 Gbps - there is protocol overhead which prevents that.  So ... wired ethernet gets 92% of the theoretical max with almost zero effort and wifi takes all kinds of effort to get 50% of whatever the box claims if the stars, planets, asteroids, and 25 closest stars all align.  
  In the real world, wifi has walls, concrete, poor drivers, poorly placed wifi router antennas ... all of that is just too much to overcome.  I've seen line-of-site wifi between 2 and 20 ft away achieve less than 50% the rated performance when tuned for a single device.  If your household has 3 devices, then the router settings will need to be a compromise so all those very different devices will even work, much less provide excellent performance.
Forgetaboutit.

---

### Post by wyattwhiteeagle on 2022-04-14
@TheFu
The following is what your post seems to suggest
> **TheFu said:**
> Completely ditch Wifi, use Ethernet
I'm not sure if you remember, I don't have a desktop computer and neither does my better half.
We use laptops.
When is the last time you seen a laptop that has an ethernet port?
I'm almost certain that it was around the time that Windows 10 came out.
Manufacturers began discontuing ethernet port's when Window's 98 came out.
By the time Windows 10 came, the "non-ethernet port laptops" was completed
My windows 7 Home Prem (SP1) laptop that I bought almost 10yrs ago in October 2012 didn't have any ethernet ports whatsoever.
It was an Acer Aspire 5733z


So I'm stuck with using Wifi.


> **TheFu said:**
> On a 4G RAM system, 4.1G swap is ideal.
Which is best, swapfile or swap partition?
I would think that whatever improves performance is best.
I know Ubuntu and it's flavour's are Linux-based.
Linux isn't Windows
However, I believe that RAM/Swap calculations remain the same. Correct me if I'm wrong.
RAM in MB multiplied by 1.5 equals Swap
```
I have 2-2gb RAM...thats 4gb RAM
Convert size of RAM to MB...4x1024=4096
Multiply by 1.5 is recommended...4096x1.5=6144
6144 MB virtual memory  (swap) is recommended for a 4gb RAM system by gaming technicians.
```
To convert that into GB...6144 divided by 1024 equals 6...so...
6144mb converts to 6gb


TheFu, a much more experienced Ubuntu user than I, suggest a 4.1gb swap.
Quiverc, a much more experienced Lubuntu user than I, suggests a 8gb swapfile...with or without an 8gb swap partition.
I'm currently using modern Lubuntu on a old laptop (Windows Vista era)


Some of my issue's are due to the old hardware.
For me to upgrade my system hardware means for me to ditch this laptop and buy a new one with Windows 11 so that it would be on the new end of today's technology standards.


My current monthly expenses won't allow me to just go buy a new one.
And I ain't gonna ask anyone to buy one for me.
Sure, I can "rent-to-own" one but that would cost me in the long run at least 3x the amount to just buy one.


Hardware upgrades are currently not an options until expenses open up.


> **TheFu said:**
> Disable Hibernation, use Standby mode
I'm using neither currently.
I'm sure that's a load on resources.
I will look into using standby mode.


> **TheFu said:**
> Use sudoedit for reconfiguring files


> **TheFu said:**
> Gather FACTS
Gather performance data. 
Capture a baseline for CPU, disk, network I/O.


You mention tools for gathering facts, performance data, and baseline's.
Somewhere you mentioned some CLI tools.
For the most accuracy, may I please get info about the CLI tools?


> **TheFu said:**
> HDD is ok
SSD is better
USB ports


Again, hardware upgrade isn't an option.

---

### Post by guiverc on 2022-04-14
> **wyattwhiteeagle said:**
> ...
We use laptops.
When is the last time you seen a laptop that has an ethernet port?
I'm almost certain that it was around the time that Windows 10 came out.
Manufacturers began discontuing ethernet port's when Window's 98 came out.
..

Which is best, swapfile or swap partition?

TheFu, a much more experienced Ubuntu user than I, suggest a 4.1gb swap.
Quiverc, a much more experienced Lubuntu user than I, suggests a 8gb swapfile...with or without an 8gb swap partition.


I'm only aware of one laptop I have that doesn't have an ethernet port; though I'm including have one with a multi-use port that requires a dongle to then use ethernet as with-ethernet.  Most of my devices are from windows 7/8 era where ethernet ports were still *common* on *enterprise* grade laptops.

Swap file is easier, which is why I usually recommend it to people. What is best will depend on how you'll use it; no simple *best* applies to everyone.

I don't recall every giving a recommendation in size for swap; usually I only give examples.  When I calculate swap size to create (*which I hate doing*) I consider the size of ram, what applications will be used, especially what applications will co-exist in RAM at the same time (*and what data they'll be handling during operation*), disk/ssd speed etc... ie. it's not a simple calculation so I don't usually give it.  My use of 8GB was possibly intended as example only.  If you understood TheFu's logic I'd follow that as I'm *rarely succinct*.

---

### Post by wyattwhiteeagle on 2022-04-14
> **guiverc said:**
> I'm only aware of one laptop I have that doesn't have an ethernet port; though I'm including have one with a multi-use port that requires a dongle to then use ethernet as with-ethernet.  Most of my devices are from windows 7/8 era where ethernet ports were still *common* on *enterprise* grade laptops.

Swap file is easier, which is why I usually recommend it to people. What is best will depend on how you'll use it; no simple *best* applies to everyone.

I don't recall every giving a recommendation in size for swap; usually I only give examples.  When I calculate swap size to create (*which I hate doing*) I consider the size of ram, what applications will be used, especially what applications will co-exist in RAM at the same time (*and what data they'll be handling during operation*), disk/ssd speed etc... ie. it's not a simple calculation so I don't usually give it.  My use of 8GB was possibly intended as example only.  If you understood TheFu's logic I'd follow that as I'm *rarely succinct*.

Maybe my use of the word suggest was improper.
You posted a link to a guide you wrote about creating a 8gb swapfile.
In that guide, you mentioned that you are using 8gb only as an example.

I took that guide and created a bash script and left the 8gb specification.

In general, I would rather have wasted disk space than to not have enough RAM/Swap.
Disk space isn't really a concern for me because I have a 1000gb HDD.
The HDD that I would be concerned about would be it's other specs such as rpm, heads, etc.
It is quite small and slow according to a power-user.
But I'm not a power-user

I can see why TheFu mentions no more than 4.1gb swap for a 4gb RAM system.
But he isn't using any GUI at all.
I believe he would need more than 4.1gb swap if he did use any GUI.

I am gonna take his advice about gathering facts; hopefully he at least mentions the names or even links of the CLI tools that I requested.

Would top, htop, iostat, vnstat, iptraf-ng, and free be some of these tool's?

So I may be changing the swap total to 4.1gb while I'm gathering and addressing those facts.

I'm also gonna take the advice about the OpenDNS.

As TheFu says...I need baseline facts first.

---

### Post by TheFu on 2022-04-14
> So I'm stuck with using Wifi.
No, you aren't. There are USB-2-Ethernet adapters for $20.  I have 2. They work reasonably well and skip all the hassles of wifi. The one I've been using most recently has a USBc connector with 3 USB3-A ports and a GigE ethernet port.  Performance is around 922 Mbps, though latency is a tiny bit higher than non-USB ethernet, it is still very acceptable. Only a network nerd would notice.

> I can see why TheFu mentions no more than 4.1gb swap for a 4gb RAM system.
But he isn't using any GUI at all.
I believe he would need more than 4.1gb swap if he did use any GUI.
I use a GUI on desktops and my advice is for a desktop.  4.1G for swap is the answer. Thought I was pretty clear, yet you decided to read extra stuff into my post.

> However, I believe that RAM/Swap calculations remain the same. Correct me if I'm wrong.
RAM in MB multiplied by 1.5 equals Swap
You are wrong.

If you don't use or need Standby mode, then don't use it.  It was mentioned only because hibernation **requires** the swap to be at least as large as the amount of RAM. You don't hibernate. That advice isn't for you. Ignore it.

I don't think anyone suggested replacing the laptop.  The 3 ways to get a faster system, in general, for everyone, are:
[LIST=1]
[*]replace a HDD with an SSD - even SATA-only computers are drastically helped by a SATA-SSD. They come in 2.5 inch laptop sizes. 1-for-1 swap almost always.  A 2.5in SATA SSD can be used in almost any computer except those ultra-thin laptops which are very common these days.  Of course, newer systems can have m.2 format SATA or NVMe SSD slots. THAT DOESN'T APPLY TO YOU!
[*]add more RAM to meet the amount needed by the workload. On a bloated desktop, that is usually 8G min. I wouldn't spend more than $20 for this throw-away upgrade.
[*]don't use wifi, use wired ethernet. A usb-2-gige adapter will work on any laptop, so this isn't throw-away.
[/LIST]

Be certain to understand openDNS's business model and that you can live with it. They were bought 5+ yrs ago by Cicso. I never understood why Cicso would want to buy a free DNS provider, unless they have a way to make money with it.  Cisco is clearly a business driven by profits, like Oracle. Nothing wrong with that, but where do they make money providing a free DNS?  Hummmm.  I don't know.  
Disclosure: I use a DNS tool from a company that Oracle bought. I'm not happy about it, but I've been with the prior company since the 1990s and have a grandfathered contract. I don't see any service impact since Oracle bought them. I don't know how Oracle makes money in this line of business, but I'm afraid to change anything which will force a contract change and much higher cost for the same service.  I think my agreement is hidden in the cracks, for now.  A few scary letters have arrived over the years suggesting  "your service may be interrupted."  The Oracle marketing people were just trying to get some reaction - a contact - I suppose. Not very nice and a waste of time.  My ISP offers a "free review" 2x a month too, which I ignore after foolishly calling back years ago to have 20 minutes wasted.  None of their "new" offers were competitive at all.  At this point, I'm looking to cut my ISP costs 50% and get at least 10x more bandwidth in the deal. My ISP is completely out of touch with reality.

---

### Post by wyattwhiteeagle on 2022-04-17
ok
I did a clean fresh install of Lubuntu 20.04 LTS.
I'm trying to get baseline's before installing or purging too many things.

I didn't create the swap partition but I only created a swapfile.

How would I use the following info's to get the needed baselines?
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       306Mi       2.6Gi        40Mi       955Mi       3.2Gi
Swap:         4.1Gi          0B       4.1Gi
```
```
$ iostat
Linux 5.13.0-39-generic (wyatt-latitudee5400)   04/17/2022      _x86_64_        (2 CPU)


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.60    0.05    2.01    1.65    0.00   92.69


Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
loop0             0.00         0.00         0.00         0.00         18          0          0
sda               4.01       118.54        30.58         0.00     872585     225093          0
scd0              0.00         0.00         0.00         0.00          2          0          0
```
```
$ sudo iostat -dxctm
[sudo] password for wyatt:           
Linux 5.13.0-39-generic (wyatt-latitudee5400)   04/17/2022      _x86_64_        (2 CPU)


04/17/2022 01:02:59 PM
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.57    0.05    2.01    1.64    0.00   92.73


Device            r/s     rMB/s   rrqm/s  %rrqm r_await rareq-sz     w/s     wMB/s   wrqm/s  %wrqm w_await wareq-sz     d/s     dMB/s   drqm/s  %drqm d_await dareq-sz  aqu-sz  %util
loop0            0.00      0.00     0.00   0.00    0.08     1.50    0.00      0.00     0.00   0.00    0.00     0.00    0.00      0.00     0.00   0.00    0.00     0.00    0.00   0.00
sda              2.26      0.11     1.23  35.22   35.22    51.79    1.71      0.03     1.49  46.57   14.69    17.72    0.00      0.00     0.00   0.00    0.00     0.00    0.11   2.59
scd0             0.00      0.00     0.00   0.00    1.00     0.23    0.00      0.00     0.00   0.00    0.00     0.00    0.00      0.00     0.00   0.00    0.00     0.00    0.00   0.00
```
```
$ ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
64 bytes from 1.1.1.1: icmp_seq=1 ttl=56 time=36.4 ms
64 bytes from 1.1.1.1: icmp_seq=2 ttl=56 time=565 ms
64 bytes from 1.1.1.1: icmp_seq=3 ttl=56 time=364 ms
64 bytes from 1.1.1.1: icmp_seq=4 ttl=56 time=30.9 ms
64 bytes from 1.1.1.1: icmp_seq=5 ttl=56 time=31.3 ms
64 bytes from 1.1.1.1: icmp_seq=6 ttl=56 time=51.6 ms
64 bytes from 1.1.1.1: icmp_seq=7 ttl=56 time=30.7 ms
64 bytes from 1.1.1.1: icmp_seq=8 ttl=56 time=30.4 ms
64 bytes from 1.1.1.1: icmp_seq=9 ttl=56 time=28.5 ms
64 bytes from 1.1.1.1: icmp_seq=10 ttl=56 time=106 ms
^C
--- 1.1.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 28.510/127.527/565.051/175.824 ms
```
```
top - 13:13:48 up  2:15,  1 user,  load average: 0.11, 0.16, 0.18
Tasks:    157 total,    1 running,    156 sleeping,    0 stopped,    0 zombie
%Cpu(s):    3.0 us,    6.1 sy,    0.0 ni,    90.9 id,    0.0 wa,    0.0 hi,    0.0 si,    0.0 st
MiB Mem:    3881.6 total,    2616.8 free,    307.6 used,    957.1 buff/cache
MiB Swap:    4199.0 total,    4199.0 free,    0.0 used,    3311.3 avail Mem
```

---

### Post by TheFu on 2022-04-17
You need a workload that can be reproduced. Also, capturing system information specifically related the the workload is necessary.  I don't think any of those tools are specific enough. They are good for general overviews, but not for comparing how a specific workload impacts a system.  There are monitoring tools that capture 30-100 things every 30-90 seconds and build graphs.  If you setup one of those tools (there are a bunch like munin, sysusage, cacti, monit, .... ), then you'll be able to compare any of those 30+ things for each different modification to the system as you attempt to improve performance.  If a specific workload options 1000 files, perhaps that could be an issue?  If the sole purpose of the system is to run 1 thing at a time, then perhaps limiting anything doesn't make as much sense as for a system where you like to run 20 programs concurrently.  Some other ideas and images of what the tools look like: [https://www.tecmint.com/linux-performance-monitoring-tools/](https://www.tecmint.com/linux-performance-monitoring-tools/)  The way I see it, if there isn't a DB as part of the monitoring, then it isn't capturing enough data consistently to allow comparisons for the last 1, 7, 14, 90 days.  With 7 days of data captured, a quick look at the graphs will let us see when the system it most highly used and delve into the details at that time to see where the bottlenecks are.  Only then can we actually address the real issues.  There are always issues, but getting to the point that a hardware upgrade of some sort is needed for improvements is the goal, IMHO.  Then it becomes a financial decision to upgrade or not.

It is all about trade offs.

The free output says something like 300MB of RAM is being used.  That seems reasonable to me for a light DE ... doing nothing.

Swap performance is related to disk performance.  Tune the disk parameters for the workload.  Do you use lots of tiny files or mostly huge files?  The tuning will be different.  Disks connected through USB need different tuning (and expectations) than disks connected via SATA or SAS or NMVe.

There are hundreds of details that only you know, research and tune.  For disk performance, I use a mix of fio and dd.  There are articles for how to use these known to google.  Tuning parameters for storage are in the file system and in the cache chunks sizing.  That's specific to the hardware (mostly).  tune2fs and hdparm are commonly used.

Network tuning is probably not worth your time besides ensuring a fast enough DNS is used.  That's dependent on your location and how much you trust any specific DNS provider.  The fastest may or may not be the most trustworthy.  I don't want to use DNS by certain providers because they are known to capture the data and sell it.  A few DNS providers do not do that, if they can be believed is the trust aspect.  It is also important that the DNS provider not get hacked all the time.  Few things are worse for our security than a DNS that cannot be trusted.

RAM performance is mostly a BIOS setting thing. Try to run at the correct speed for the system and RAM.  On one of my systems, because I don't have "matched" pairs of DDR4, they cannot run at the speed supported by the MB and CPU and RAM. I had to reduce the speed slightly until I got the system stability just right.  All this because I bought 16G each time, a year apart for 32G or RAM.  Running about 10% slower isn't bad and the over system performance is still amazing.

---

### Post by wyattwhiteeagle on 2022-04-18
You mention DNS providers and performance monitoring tools...
Which ones do you personally use?

---

### Post by TheFu on 2022-04-18
> **wyattwhiteeagle said:**
> You mention DNS providers and performance monitoring tools...
Which ones do you personally use?

munin, monit, 1.1.1.1 and a few paid DNS for domains that I own.  I've used Cacti, Nagios, some commercial performance tools from BMC and SysUsage previously. The BMC stuff is good, but bloated and expensive. 

I run an internal set of DNS servers, but they point to 1.1.1.1 for the upstream 99.999% of the time. My internal DNS servers do the domain filtering I want.  I think currently about 330K domains are filtered, but I didn't count recently.  I also filter around 9K internet subnets (in and out).

Slow DNS and slow networking (wifi) can make everything feel slower on a Unix workstation.  That's because there are many commonly used tools that perform DNS lookups even when we expect the answer provided to be a localhost.  The remote DNS has to return a "not-found" before they continue.  For example, sudo does DNS lookups because the sudoers config file supports per-host rules.  That could mean that a sudo command could take up to 30 seconds (a guessed timeout lookup period) before it even tries to do anything.  Misconfigured DNS settings are a very common performance issue.

---

### Post by wyattwhiteeagle on 2022-04-18
> **TheFu said:**
> munin, monit, 1.1.1.1 and a few paid DNS for domains that I own.  I've used Cacti, Nagios, some commercial performance tools from BMC and SysUsage previously. The BMC stuff is good, but bloated and expensive. 

...

 Misconfigured DNS settings are a very common performance issue.
Thank you

Are there tools to correct the misconfigured DNS settings?

---

### Post by TheFu on 2022-04-19
> **wyattwhiteeagle said:**
>  Are there tools to correct the misconfigured DNS settings?

I use sudoedit.

---

### Post by wyattwhiteeagle on 2022-04-19
> **TheFu said:**
> ...The way I see it, if there isn't a DB as part of the monitoring, then it isn't capturing enough data consistently to allow comparisons for the last 1, 7, 14, 90 days....

When you say DB, are you talking about DataBase...as in like on the internet or in the cloud?

I remember seeing your response in another thread about OpenDNS.
It causes me to wonder if OpenDNS is one of those that you refer to as selling customer data of the customer's 
or maybe it's one that is easily hacked all the time.
I haven't seen it anywhere on any DNS host/provider list anywhere.
Not even on Wikipedia.

DNS 1.1.1.1 is CloudFlare.
I seen some site's claim that CloudFlare's free version is only a trial version.
Is that true?

---

### Post by TheFu on 2022-04-19
> **wyattwhiteeagle said:**
> When you say DB, are you talking about DataBase...as in like on the internet or in the cloud?
DB is a file or set of files where a database management system stores data. It isn't not specific to any location, but at some point it has to be stored somewhere.  Some DBs are in memory only, but if we are talking about backups, then I'd be talking specifically about DB files on the system that needs to be backed up.  DB files that are open while being backed up often cause corrupted backups.

> **wyattwhiteeagle said:**
> I remember seeing your response in another thread about OpenDNS.
It causes me to wonder if OpenDNS is one of those that you refer to as selling customer data of the customer's 
or maybe it's one that is easily hacked all the time.
If I didn't say, then it is only suspicion and research is needed.  I don't keep links as proof laying around for everything. Use whatever web search tool you like to look for problems.  People often only seek out whether a service is free or not. They don't often search for whether is it secure or has been hacked and by whom that happened in history.  Often, the types if prior issues say much about a service. Most companies don't really change everything after issues happen, unless there is external, mandated, oversight.  For example, Asus network/router equipment was caught having extremely poor security practices. The US FTC sued them and won the case ( or the company decided to settle, sometimes that is hard to tell). In the settlement for deceptive practices, Asus agreed to all sorts of oversight for that product area and they've been one of the best home router company for keeping their hardware patched for more than 3 yrs AND they act with reasonable speed to close reported issues. They are a model for the rest of the industry NOW. The settlement required 20 yrs of oversight. I think it was around 2013 or 2015, so they are well into doing it right.  I learned this by doing research, finding hacked routers, seeing govt documents.  It has been a few years, so my memory has simplified everything down to ... Asus routers are good for being patched with known security updates. I don't use Asus routers, but that's because I want routers with more control and continuous patching. Most people wouldn't want/need that.

> **wyattwhiteeagle said:**
> I haven't seen it anywhere on any DNS host/provider list anywhere.
Not even on Wikipedia.

DNS 1.1.1.1 is CloudFlare.
I seen some site's claim that CloudFlare's free version is only a trial version.
Is that true?

Did you try google/startpage/ddg?  Perhaps putting 1.1.1.1 into a simple web browser would provide some answers?  IDK.

I can only guess there is confusion between being an end-user of DNS and setting up DNS so that websites and domains you own can be found.  [https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site) explains what is needed to have your own website.  DNS is in that list.  After all, someone has to pay to make DNS possible and end-users aren't going to pay.  They get all the people running domains to pay instead.
There are also end-user DNS services that add value with selected filtering based on that user's choices.  There are family filters, porn filters, kid filters, religious filters with the ability to add custom filters.  Some of those value-add services charge money. Some do not.  Some ISPs have bought access to the service, like some ISPs have bought access to Windows AV software. Customers of those ISPs gain access for free ... and I suspect the ISP gains access to all the data too.

There are many rabbit holes here. Sorry.

---

### Post by wyattwhiteeagle on 2022-04-20
Are there any GUI performance monitoring tools that doesn't need an internet connection to work?

One of the major issue's is that sometimes my laptop has no internet connection.
If I run only web-based monitoring tools...how am I supposed to see what caused the problem if the problem is "no internet connection"?

*buntu can get corrupted when poor security or dumb things are being practiced.
The laptop I had some time ago caught a trojan virus...(MS Windows of course).
I was using Avast Free Antivirus.
I could boot only into safe mode.
I couldn't boot into safe mode with networking and I couldn't boot into normal windows.
so I tried scanning with Avast only to learn that Avast needs an internet connection for it's User-Interface to work.

Lesson learned about using web-based software.

I don't want to be a CLI-only user and I don't want to be a GUI-only user.
I use both interchangably.
Doing both has proven to myself that I get better results.
That may not be true for everybody, but it's true for me.

---

### Post by dragonfly41 on 2022-04-20
> [COLOR=#000000]I don't want to be a CLI-only user and I don't want to be a GUI-only user.[/COLOR]
[COLOR=#000000]I use both interchangably.[/COLOR]

Some time back .. in one of your discussions .. I pointed to Actiona which is a Qt4 era automation tool.
I believe that you installed it.  It is in the repo.
It has some uses. Such as creating a custom library of CLI scripts (gleaned from this forum) which you can run
through a simple GUI.  Some time back there was clicompanion2 but it seems to have dropped out.

---

### Post by TheFu on 2022-04-20
> **wyattwhiteeagle said:**
>  
If I run only web-based monitoring tools...how am I supposed to see what caused the problem if the problem is "no internet connection"?


"Web-based" doesn't mean internet.  It means running on a web server.  Your laptop can easily run a web server that displays the monitoring information from the DB, also on your laptop.  These things are NOT heavy processes. Typically, about 3-5% of the CPU would be used for monitoring and showing the data.  You can have the data graphics created on-demand only, so the processing of the DB information into pretty graphs only happens when you actually want to see it.  Many of these tools use a specialized DB format called RDD. This has been used in Unix since before I started with it nearly 30 yrs ago. It is a file-based DB, without a daemon. 1000x lighter than MariaDB/MySQL or those types of DBMS.

BTW, you can easily limit access to the web server to only localhost, so nobody else can see the data either. I think that might be the default for most of these tools.

But none of them are install-n-look.  They all need a little setup and at least a few hours of data capture to er ... capture some data to be displayed. OTOH, if data capture never starts, there won't ever be any data to visualize.  On of the easiest to setup is SysUsage, but I haven't used it recently, so my memory about it could be off.  [https://sysusage.darold.net/](https://sysusage.darold.net/)

It is fine if this is beyond the effort desired. Use the tools that others have suggested, but if you aren't watching those tools before, during, and after the issue happens, it will be hard to figure out.  Short-term pain, for long-term gain.

---

### Post by wyattwhiteeagle on 2022-04-20
> **dragonfly41 said:**
> Some time back .. in one of your discussions .. I pointed to Actiona which is a Qt4 era automation tool.
I believe that you installed it. It is in the repo.
It has some uses. Such as creating a custom library of CLI scripts (gleaned from this forum) which you can run
through a simple GUI. Some time back there was clicompanion2 but it seems to have dropped out.


Yes, I installed Actiona on Ubuntu (minimal install) and again under Wine.
We learned that only the one install was needed.
Actiona wasn't a problem...it was Ubuntu.
Ubuntu Minimal was too much for my limited resources (RAM).


I went through installs of Linux-Lite, Ubuntu, Lubuntu, and Xubuntu.
Xubuntu didn't seem to match my needs and it was more confusing than Lubuntu.


Finally, I said to myself,
> "Self, you need to make up your mind.
Pick one, get used to it, learn it, and make it yours.
Stop going back and forth between the distro's and flavour's.
You didn't learn Windows over-night.
Learning *buntu isn't gonna be an over-night thing either.
I didn't know then as much as I know now.


Actiona is still in the plans.
I'm working out the "querks and kinks" before I "re-embark" on the Actiona venture.


> **TheFu said:**
> "Web-based" doesn't mean internet. It means running on a web server. Your laptop can easily run a web server that displays the monitoring information from the DB, also on your laptop. These things are NOT heavy processes. Typically, about 3-5% of the CPU would be used for monitoring and showing the data. You can have the data graphics created on-demand only, so the processing of the DB information into pretty graphs only happens when you actually want to see it. Many of these tools use a specialized DB format called RDD. This has been used in Unix since before I started with it nearly 30 yrs ago. It is a file-based DB, without a daemon. 1000x lighter than MariaDB/MySQL or those types of DBMS.


BTW, you can easily limit access to the web server to only localhost, so nobody else can see the data either. I think that might be the default for most of these tools.


But none of them are install-n-look. They all need a little setup and at least a few hours of data capture to er ... capture some data to be displayed. OTOH, if data capture never starts, there won't ever be any data to visualize. On of the easiest to setup is SysUsage, but I haven't used it recently, so my memory about it could be off. [https://sysusage.darold.net/](https://sysusage.darold.net/)


It is fine if this is beyond the effort desired. Use the tools that others have suggested, but if you aren't watching those tools before, during, and after the issue happens, it will be hard to figure out. Short-term pain, for long-term gain.


Thank you, it puts my mind at ease.
When I was looking through the tools you mentioned, a few of them were installed by default.
I'll look at all of them more thoroughly and let you know which I choose.

---

### Post by TheFu on 2022-04-20
Ubuntu Minimal is the Gnome4 (depending on which release was selected), just without most of the automatic end-user programs.  It isn't lite. It just uses less storage. Lubuntu and Xubuntu are the light-er 'buntu family choices.  There are a few other desktop versions without ubuntu in the name too. I can't keep up.

If you want a usable, but lite distro, check out **MXLinux**.  It has some pains with it and their releases aren't as consistent, but for people with less current hardware, it's a valid choice.  A few friends love it after trying all the others first on their C2D-like hardware.

---

### Post by wyattwhiteeagle on 2022-04-20
> **TheFu said:**
> Ubuntu Minimal is the Gnome4 (depending on which release was selected), just without most of the automatic end-user programs.  It isn't lite. It just uses less storage. Lubuntu and Xubuntu are the light-er 'buntu family choices.  There are a few other desktop versions without ubuntu in the name too. I can't keep up.

If you want a usable, but lite distro, check out **MXLinux**.  It has some pains with it and their releases aren't as consistent, but for people with less current hardware, it's a valid choice.  A few friends love it after trying all the others first on their C2D-like hardware.

Nope
I've come this far with Lubuntu.
I'm not looking to change until, at the very least, I get a new laptop as my budget allows.

I'm choosing munin and monit.
After backup...
What all system changes should I look into making to prepare the system for those?
What settings & preferences should I choose after installing them?
```
wyatt@wyatt-latitudee5400:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             481964    539   481425    1% /dev
tmpfs            496843    827   496016    1% /run
/dev/sda2      61038592 277928 60760664    1% /
tmpfs            496843     41   496802    1% /dev/shm
tmpfs            496843      6   496837    1% /run/lock
tmpfs            496843     19   496824    1% /sys/fs/cgroup
tmpfs            496843     37   496806    1% /run/user/1000
```
```
wyatt@wyatt-latitudee5400:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     389M  6.3M  382M   2% /run
/dev/sda2      ext4      916G   25G  845G   3% /
tmpfs          tmpfs     1.9G   16M  1.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     389M  8.0K  389M   1% /run/user/1000
```
```
wyatt@wyatt-latitudee5400:~$ snap list


Command 'snap' not found, but can be installed with:


sudo apt install snapd
```
```
wyatt@wyatt-latitudee5400:~$ systemd-analyze time
Startup finished in 8.753s (kernel) + 28.421s (userspace) = 37.175s 
graphical.target reached after 28.404s in userspace
```
```
wyatt@wyatt-latitudee5400:~$ systemd-analyze blame | head
10.985s dev-sda2.device                                    
10.482s NetworkManager-wait-online.service                 
 9.044s networkd-dispatcher.service                        
 7.594s accounts-daemon.service                            
 5.670s NetworkManager.service                             
 5.405s udisks2.service                                    
 4.531s systemd-resolved.service                           
 4.383s avahi-daemon.service                               
 3.625s polkit.service                                     
 3.261s gpu-manager.service                                

```
```
wyatt@wyatt-latitudee5400:~$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.


graphical.target @28.404s
&#9492;&#9472;multi-user.target @28.404s
Red&#9492;&#9472;kerneloops.service @28.221s +181ms
    &#9492;&#9472;network-online.target @28.124s
   Red&#9492;&#9472;NetworkManager-wait-online.service @17.640s +10.482s
     Red&#9492;&#9472;NetworkManager.service @11.964s +5.670s
          &#9492;&#9472;dbus.service @11.959s
            &#9492;&#9472;basic.target @11.547s
              &#9492;&#9472;sockets.target @11.547s
                &#9492;&#9472;uuidd.socket @11.547s
                  &#9492;&#9472;sysinit.target @11.168s
                 Red&#9492;&#9472;systemd-backlight@backlight:acpi_video0.service @10.235s +917ms
                      &#9492;&#9472;system-systemd\x2dbacklight.slice @10.230s
                        &#9492;&#9472;system.slice @6.844s
                          &#9492;&#9472;-.slice @6.844s
```

---

### Post by TheFu on 2022-04-20
> **wyattwhiteeagle said:**
>  
I'm choosing munin and monit.
What all system changes should I look into making to prepare the system for those?
What settings & preferences should I choose after installing them?

I don't remember. You only need 1, not both.  Follow the install guides on the project pages.

---

### Post by wyattwhiteeagle on 2022-04-20
Monit's manpage say's...and I quote...


> Before Monit is started the first time, you can test the control file for syntax errors:
```

 $ monit -t
 $ Control file syntax OK

```
If there was an error, Monit will print an error message to the console, including the line number in the control file from where the error was found.

I typed "sudo monit -t" into the terminal...
```
$ sudo monit -t
[sudo] password for wyatt:           
Control file syntax OK
```

---

### Post by wyattwhiteeagle on 2022-04-21
The manpage for monit mentions a control file  named monitrc.
It has a lot of things.
The only things commented in are the things needed for monit to run in the background.
Everything else is commented out..

One out-comment is a line that mentions a bash script that I create and store in a specified location.

What is my next step?

Should I comment in everything that is relevant to what I'm looking for in the control file?
Should I create my own using the manpage for all the options and arguments that I need?

---

### Post by wyattwhiteeagle on 2022-04-26
Here's a start with monit...
```

[TABLE="width: 100%"]
[TR]
[TD="class: left, width: 100%, colspan: 2"][h=1]Monit Service Manager[/h][CENTER]Monit is [running]("http://localhost:2812/_runtime") on wyatt-latitudee5400 and monitoring:[/CENTER]
[/TD]
[/TR]
[/TABLE]
[TABLE="width: 1216"]
[TR]
[TH="class: left first, align: left"]System[/TH]
[TH="class: left, align: left"]Status[/TH]
[TH="class: right column, align: right"]Load[/TH]
[TH="class: right column, align: right"]CPU[/TH]
[TH="class: right column, align: right"]Memory[/TH]
[TH="class: right column, align: right"]Swap[/TH]
[/TR]
[TR="class: stripe"]
[TD="class: left"][wyatt-latitudee5400]("http://localhost:2812/wyatt-latitudee5400")[/TD]
[TD="class: left"][COLOR=#00FF00]OK[/COLOR][/TD]
[TD="class: right column, align: right"][0.39] [0.46] [0.45][/TD]
[TD="class: right column, align: right"]0.0%us 0.0%sy 0.0%ni 0.0%wa [/TD]
[TD="class: right column, align: right"]24.1% [936.8 MB][/TD]
[TD="class: right column, align: right"]0.0% [0 B][/TD]
[/TR]
[/TABLE]

```

---

### Post by TheFu on 2022-04-26
Well, that isn't really too useful.  If you click the system link, does it go into details?  Is there a way to gather detailed process, disk, network data?
If not, sorry, I mixed up monit with all the other tools.  [https://munin-monitoring.org/](https://munin-monitoring.org/) will gather and display detailed process, disk, network data. Perhaps that's why I don't remember much about monit?

---

### Post by wyattwhiteeagle on 2022-04-26
> **TheFu said:**
> Well, that isn't really too useful.  If you click the system link, does it go into details?  Is there a way to gather detailed process, disk, network data?
If not, sorry, I mixed up monit with all the other tools.  [https://munin-monitoring.org/](https://munin-monitoring.org/) will gather and display detailed process, disk, network data. Perhaps that's why I don't remember much about monit?

What all do we need to monitor?

I'm able to get the details we need.
I just haven't configured monitrc enough to get those details.
I just got monit going.

The monitrc uses an example for Apache and only references MySQL and others.

---

### Post by TheFu on 2022-04-26
> **wyattwhiteeagle said:**
> What all do we need to monitor?

I'm able to get the details we need.
I just haven't configured monitrc enough to get those details.
I just got monit going.

The monitrc uses an example for Apache and only references MySQL and others.

What to monitor is a judgement call.  You want to monitor the system, not any specific daemon, at least until you know when and what is causing the issue.  There are about 30-50 system things to watch. Only after you watch them all for a week, will the items having problems jump out in the graphs.
  Perhaps monit is for watching specific daemons being available instead of performance monitoring a complete system.  It isn't like you had apache or mariadb (never use mysql) on the system when issues started.

I think monit was a bad suggestion for your needs. Sorry.  I'm using munin and for each node, it generates 106 graphs.  See what I mean by there are lots of things to monitor?  That IOPS, network packets, disk use, disk inodes, processes, cpu, temperatures, system time drift, network latency, netstat, nfs, email, vmstat, fans, number of open files,  open files per process and a bunch of other things.  System stuff.  You don't know, until you see it all.  It will also monitor daemons like ssh, apache, DBMS, using a plugin too, but the defaults monitor the system.

---

### Post by wyattwhiteeagle on 2022-04-26
> **TheFu said:**
> Well, that isn't really too useful.  If you click the system link, does it go into details?  Is there a way to gather detailed process, disk, network data?
If not, sorry, I mixed up monit with all the other tools.  [https://munin-monitoring.org/](https://munin-monitoring.org/) will gather and display detailed process, disk, network data. Perhaps that's why I don't remember much about monit?

I believe we're needing to see graph's and number's instead of just number's.
I'll look into getting the detailed process, disk, and network data.
I may switch to Munin.
The only details I can get right this moment is the following...

*UPDATE*
I don't believe these details are specific enough.
```

[FONT=HelveticaNeue][TABLE="width: 100%"]
[TR]
[TD="width: 20%"][Home]("http://localhost:2812/") > [wyatt-latitudee5400]("http://localhost:2812/wyatt-latitudee5400")[/TD]
[TD="width: 60%, align: center"]Use [M/Monit]("https://mmonit.com/") to manage all your Monit instances[/TD]
[TD="width: 20%"][RIGHT][Monit 5.31.0]("http://localhost:2812/_about")[/RIGHT]
[/TD]
[/TR]
[/TABLE]
**System status**

[TABLE="width: 1201"]
[TR]
[TH]Parameter[/TH]
[TH="width: 70%, align: left"]Value[/TH]
[/TR]
[TR]
[TD]Name[/TD]
[TD]wyatt-latitudee5400[/TD]
[/TR]
[TR]
[TD]Status[/TD]
[TD][COLOR=#00FF00]OK[/COLOR][/TD]
[/TR]
[TR]
[TD]Monitoring status[/TD]
[TD]Monitored[/TD]
[/TR]
[TR]
[TD]Monitoring mode[/TD]
[TD]active[/TD]
[/TR]
[TR]
[TD]On reboot[/TD]
[TD]start[/TD]
[/TR]
[TR]
[TD]Load average[/TD]
[TD][0.51] [0.20] [0.11][/TD]
[/TR]
[TR]
[TD]Cpu[/TD]
[TD]6.8%usr 3.1%sys 0.0%nice 1.3%iowait 0.0%hardirq 0.1%softirq 0.0%steal 0.0%guest 0.0%guestnice[/TD]
[/TR]
[TR]
[TD]Memory usage[/TD]
[TD]1.0 GB [27.1%][/TD]
[/TR]
[TR]
[TD]Swap usage[/TD]
[TD]0 B [0.0%][/TD]
[/TR]
[TR]
[TD]Uptime[/TD]
[TD]9h 37m[/TD]
[/TR]
[TR]
[TD]Boot time[/TD]
[TD]Tue, 26 Apr 2022 13:57:41[/TD]
[/TR]
[TR]
[TD]Filedescriptors[/TD]
[TD]5920 [0.0% of 9223372036854775807 limit][/TD]
[/TR]
[TR]
[TD]Data collected[/TD]
[TD]Tue, 26 Apr 2022 23:34:57[/TD]
[/TR]
[TR="class: rule"]
[TD]CPU usage limit[/TD]
[TD]If greater than 200.0% for 4 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]CPU I/O wait limit[/TD]
[TD]If greater than 80.0% for 2 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]CPU system limit[/TD]
[TD]If greater than 20.0% for 2 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]CPU user limit[/TD]
[TD]If greater than 80.0% for 2 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]Swap usage limit[/TD]
[TD]If greater than 20.0% for 4 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]Memory usage limit[/TD]
[TD]If greater than 80.0% for 4 cycles then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]Load average (15m)[/TD]
[TD]If greater than 1.0 then alert[/TD]
[/TR]
[TR="class: rule"]
[TD]Load average (5m)[/TD]
[TD]If greater than 3.0 then alert[/TD]
[/TR]
[/TABLE]
[TABLE]
[TR]
[TD][/TD]
[/TR]
[/TABLE]

[/FONT]
[CENTER][COLOR=#777777][FONT=HelveticaNeue]Copyright ©


[/FONT][/COLOR][/CENTER]

```

---

### Post by TheFu on 2022-04-27
If I printed the graphs for 1 system created by **munin**, it would be at least 10 pages long, mainly because my systems have multiple NICs.  The underlying numbers are available that made the graphs, if needed.  Clicking on a graph will move to another page with daily, weekly, monthly and year graphs. It is possible to specify start-end dates for any graph, I've never bothered.

A demo website: [http://demo.munin-monitoring.org/](http://demo.munin-monitoring.org/) to see what I mean about system monitoring.

The setup guide: [https://munin-monitoring.org/download/](https://munin-monitoring.org/download/)
I'm using the version from the default repos.

Sorry for the wild goose chase. 100% my fault.  I really expected you'd pick something prettier like Cacti.  I use munin with a primary server and about 20 nodes.

---

### Post by wyattwhiteeagle on 2022-04-27
> **TheFu said:**
> If I printed the graphs for 1 system created by **munin**, it would be at least 10 pages long, mainly because my systems have multiple NICs.  The underlying numbers are available that made the graphs, if needed.  Clicking on a graph will move to another page with daily, weekly, monthly and year graphs. It is possible to specify start-end dates for any graph, I've never bothered.

A demo website: [http://demo.munin-monitoring.org/](http://demo.munin-monitoring.org/) to see what I mean about system monitoring.

The setup guide: [https://munin-monitoring.org/download/](https://munin-monitoring.org/download/)
I'm using the version from the default repos.

Sorry for the wild goose chase. 100% my fault.  I really expected you'd pick something prettier like Cacti.  I use munin with a primary server and about 20 nodes.

The prettier ones have more of a workload than the less pretty ones.
If we're looking for a baseline/workload...it seem's senseless to me to have part of the prettier workload in the numbers and graphs.

---

### Post by TheFu on 2022-04-27
> **wyattwhiteeagle said:**
> The prettier ones have more of a workload than the less pretty ones.
If we're looking for a baseline/workload...it seem's senseless to me to have part of the prettier workload in the numbers and graphs.

The graphs can be created either on-demand (cgi) or scheduled (via cron) for creation during non-peak periods.  Data collection is almost zero load.  Remember those physics labs? Just looking at a particle changes the behavior of the particle, a tiny bit. That's the same with all server monitoring.  But without any data, there's no hope of determining the root cause and if steps to improve actually work.

I'd recommend using cron to create graphs 2x a day. Then serve the created html using any light webserver you prefer. The install gui has example configs for all the popular web servers.

---

### Post by wyattwhiteeagle on 2022-05-03
ok...I got Munin going about an hour ago...
It show's a whole array of graph's with number's.
The graph's and number's shown are Munin's defaults.

It shows there are no criticals or warnings.
Most likely because Munin isn't customized yet to monitor those.

How do I get baseline numbers from these info's?

---

### Post by wyattwhiteeagle on 2022-05-03
I spoke too soon...
Looks like I still have some custom configurations to set.

I got some errors about things that prevent Munin from working.
Munin worked 3 times before but now it isn't working.

I will post the error's later sometime today.

*Update*
Errors posted
[https://ubuntuforums.org/showthread.php?t=2474590](https://ubuntuforums.org/showthread.php?t=2474590)

---

### Post by wyattwhiteeagle on 2022-05-10
I have munin going
Right now I have about a day and a half of graph's and number's.

I've had to do several Timeshift system restores, so I don't have as many days as I should.

Munin uses Apache2.
I'm working on learning why the Apache2 HTTP Server keeps getting broken when I use the System Clean in Stacer.

I'm hoping to get some baseline number's from Munin soon.

---

### Post by dragonfly41 on 2022-05-10
Some clues found ..

[https://github.com/oguzhaninan/Stacer/issues/425](https://github.com/oguzhaninan/Stacer/issues/425)

---

### Post by TheFu on 2022-05-10
> **wyattwhiteeagle said:**
>  
I'm working on learning why the Apache2 HTTP Server keeps getting broken when I use the System Clean in Stacer. 

Yet another reason that mixing desktop stuff with server stuff isn't a great idea.  Sure, lots of people do it, but to get Munin working, we  have to configure all sorts of server directories outside our $HOME. Some for Munin data collection, some for generating graphs, and some for the web server.  Those locations shouldn't be touched by 'desktop' clean up processes.  And, you may want to include the new directories in any backup directories, so that when something bad happens, the months to years of performance data isn't lost too.

---

### Post by wyattwhiteeagle on 2022-05-20
> **TheFu said:**
> Yet another reason that mixing desktop stuff with server stuff isn't a great idea.  Sure, lots of people do it, but to get Munin working, we  have to configure all sorts of server directories outside our $HOME. Some for Munin data collection, some for generating graphs, and some for the web server.  Those locations shouldn't be touched by 'desktop' clean up processes.  And, you may want to include the new directories in any backup directories, so that when something bad happens, the months to years of performance data isn't lost too.

Some good points here.
The laptop I have would be considered an "end-user desktop".

I agree..."If it ain't a server, don't use server stuff."
Now I may break that rule on some things, but not when it comes to something good on my system not working.

Are there any monitoring tools that gather the same specific info's that aren't for a server/client setup?

You mentioned before that you believed I would've chosen one of the "prettier" ones like Cacti.
The pretty is nice sometimes, but I will choose the less pretty before choosing the pretty.
I'm not completely against "pretty", it just isn't my "first-choice go-to"

I'm used to using Windows "Task Manager" and "Resource Monitor" but it was time-consuming.
For me, there was no option to "set something up and wait a week"

---

### Post by dragonfly41 on 2022-05-20
Another thread of an idea..

Gave you tried running lynis which should be installed by default? If not it is in the repo.
It is an audit tool run at command level. Runs through a whole lot of audit checks.
There is a commercial pro version. But the basic version is free.

[FONT=monospace][COLOR=#000000]sudo lynis --verbose[/COLOR]
[/FONT]

---

### Post by wyattwhiteeagle on 2022-05-20
> **dragonfly41 said:**
> Another thread of an idea..

Gave you tried running lynis which should be installed by default? If not it is in the repo.
It is an audit tool run at command level. Runs through a whole lot of audit checks.
There is a commercial pro version. But the basic version is free.

[FONT=monospace][COLOR=#000000]sudo lynis --verbose[/COLOR]
[/FONT]
Lynis isn't installed by default.
Neither is it available through Muon Package Manager.
An internet search for Lynis returned some results.

I noticed that everything I looked at mentioned lynis being on older releases of Ubuntu and offered on Linux.
Nothing for Lubuntu.

Is lynis a qt5/kde or is it for all linux-based?
Is it outdated/unsupported on flavours of today?

---

### Post by dragonfly41 on 2022-05-21
So be it ..

I found it by browsing Synaptic in my current Ubuntu **20.04**.
But that version of lynis (version 2) is old and you can download latest version 3 from here ..

It is designed to identify security holes rather than "bottlenecks", as I understand.

[https://cisofy.com/downloads/lynis/](https://cisofy.com/downloads/lynis/)


Quote:
Although most users will install Lynis via a package, installation is not required! Just extract the archive (tarball) and run [B]./lynis audit system


[Added note]
[/B]It is easy to find if you searched.
Go to this site     [https://cisofy.com/lynis/](https://cisofy.com/lynis/)
and view the "Demo in 30 seconds" clip.

Also read here ..

[https://cisofy.com/lynis/#operating-systems](https://cisofy.com/lynis/#operating-systems)
I would be surprised if Lubuntu is not supported.

---

### Post by wyattwhiteeagle on 2022-06-25
Is Conky specific enough for monitoring my "non-server" machine?

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Post your .conkyrc files w/ screenshots (closed thread)
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by wyattwhiteeagle on 2022-06-26
Conky didn't work correctly...
No quit button or anything.
only the info being monitored
had to shut down or reboot to exit the window.

Installed Cacti.

Any tips on how to configure Cacti?

---

### Post by dragonfly41 on 2022-06-27
Cacti prickly?

For your consideration ...

[https://stackshare.io/stackups/cacti-vs-prometheus#:~:text=Cacti%20provides%20a%20fast%20poller,systems%20and%20service%20monitoring%20system](https://stackshare.io/stackups/cacti-vs-prometheus#:~:text=Cacti%20provides%20a%20fast%20poller,systems%20and%20service%20monitoring%20system).

---

### Post by wyattwhiteeagle on 2022-06-27
> **dragonfly41 said:**
> Cacti prickly?

For your consideration ...

[https://stackshare.io/stackups/cacti-vs-prometheus#:~:text=Cacti%20provides%20a%20fast%20poller,systems%20and%20service%20monitoring%20system](https://stackshare.io/stackups/cacti-vs-prometheus#:~:text=Cacti%20provides%20a%20fast%20poller,systems%20and%20service%20monitoring%20system).
Seeing that comparison report leads me to ask...

1. Does Cacti have any triggers for alerting the user if there's a problem?
2. Does Prometheus cost any money?
3. Which tool can alert the user pin-pointing the exact file, the files location, and line number that is causing the problem?

There's a world of Cacti posts here on the forums.
It would seem as though Prometheus would have more inquiries than Cacti.
But like that report states, "FREE is the main reason Cacti is chosen."

---

### Post by dragonfly41 on 2022-06-27
Prometheus is in Ubuntu repo .. but I have not yet found the time to try it. Search "prometheus" in Synaptic Package Manager.
The interesting thought is to setup a pipeline from Prometheus to Grafana so that issues can be seen on a Grafana cloud dashboard (rather like Stacer).

---

### Post by wyattwhiteeagle on 2022-06-27
> **dragonfly41 said:**
> Prometheus is in Ubuntu repo .. but I have not yet found the time to try it. Search "prometheus" in Synaptic Package Manager.
The interesting thought is to setup a pipeline from Prometheus to Grafana so that issues can be seen on a Grafana cloud dashboard (rather like Stacer).

A cloud dashboard
Does that mean that my info will be sent to the cloud?

---

### Post by #&amp;thj^% on 2022-06-27
More here: [https://prometheus.io/docs/prometheus/latest/querying/basics/](https://prometheus.io/docs/prometheus/latest/querying/basics/)
> **wyattwhiteeagle said:**
> A cloud dashboard
Does that mean that my info will be sent to the cloud?
You can have it to rely only for local storage

---

### Post by wyattwhiteeagle on 2022-12-18
Ok...I know it's been a while...

After through much stresses at home with family, I've been able to finally get my system to somewhat sustain some stability...
I've found Monitorix.

Monitorix, compared to other monitoring tools that I've tried, is the first one able to be very specific while not breaking when I use Stacer, Bleachbit, and a custom cleanup script.

However, the only graphs enabled are the defaults.
This means I haven't made any changes to the config file.

To sum it up...it works for my system.

Does anyone have any tips or suggestions in how to configure and/or use Monitorix?
Or should I give it some time then see what the default graphs and numbers look like?

---

