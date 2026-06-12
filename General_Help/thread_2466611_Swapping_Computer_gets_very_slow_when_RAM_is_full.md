---
title: "Swapping? Computer gets very slow when RAM is full"
date: 2021-09-01
forum: General Help
---

### Post by MarcoPau on 2021-09-01
Hiall, I have recently changed my computer and for some reason I am experiencing long periods of hard drive noisy spinning when RAM is full.

My ubuntu is on an SSD, 8 gig swap is set on the HDD.

              total        used        free      shared  buff/cache   available
Mem:        7876632     4871984      404340     1051716     2600308     1667688
Swap:       8191996     3113572     5078424

This is the situation at the minute, and I still can hear the HDD spinning even if I am not actually writing any data on my HDD partitions, thus I assume it's the swapping.

Is there anything I could do other than buying extra RAM? :-)

Thanks!

---

### Post by TheFu on 2021-09-01
Sure, don't run so many programs 
or
choose lighter programs
or
tune the kernel parameters NOT to swap when there is still RAM available.

BTW, when posting command output, please show 
a) the exact command used
b) the output wrapped in forum code-tags - so columns line up here.

That looks like the the 'free' command.  I'd use **free -hm** which on my 20.04 system shows:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       767Mi       208Mi       8.0Mi       2.9Gi       2.8Gi
Swap:         4.1Gi          0B       4.1Gi
```
See how much easier that is to read and understand?

My example above doesn't have any kernel tuning. That is the default.  I think there is very little reason to have more than 4.1G as swap on any desktop today, provided you don't hibernate.
On another system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            31G         16G        3.4G        224M         11G         14G
Swap:          4.3G        1.6G        2.7G
```
The 4.3G swap was a round off issue when I resized it.  As you can see, it isn't hard to keep swap small if you choose light programs.

When RAM gets fully used, swap kicks in and the entire purpose of swap is one of these:
[LIST]
[*]Show clients you don't like them very much by slowing down servers (VPS providers do this on purpose for the very low-end, cheap, entrance level offers)
[*]Provide feedback to the users that they need to reduce the "ask" from the system, by getting slower.
[/LIST]

There is a thing called too much swap.

---

### Post by MarcoPau on 2021-09-03
Great, thank you!

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          7,5Gi       4,1Gi       323Mi       608Mi       3,1Gi       2,5Gi
Swap:         7,8Gi       1,8Gi       6,0Gi
```


Any specific hint for kernel tuning? I found something called swappiness on google, IIRC it's something I did use already many years ago but not sure.

Anyway, are we are talking about 323 MB of free memory in my above output? I am basically running Thunderbird and the two browsers Chromium and Firefox. Yes, they have a whole bunch of tabs but I use the suspend extensions for both of them...

Cheers.

---

### Post by TheFu on 2021-09-03
Those are 3 of the heavier program on Linux.  The only worse ones that I know are video editors, Evolution, and snap versions of any of those (including FF, TB, and Chromium).  

I think you have too much swap. Did you search, find and read the long thread about the purpose of swap from June 2020 in these forums? Well worth a read.

Besides that, there's nothing wrong with you system using RAM.  If you look at the output, 3.1G is being used for disk and network caching. As more programs are run, the amount used for caching will reduce.

I tune a few things in the kernel, but those parameters are for my specific workloads, not a typical desktop. On my desktop/laptop, I don't touch anything no that zswap is standard.

---

### Post by HermanAB on 2021-09-03
BTW, any amount of tuning to change swappiness will likely make no discernable difference to your situation.  

You should run 'top' or 'htop' to see which program is hogging resources and kill it.  Then, either restart it periodically if you *have* to use it - or find a better program to use that doesn't hog resources.

---

### Post by MarcoPau on 2021-09-10
Thank you guys. This means, if I assume correctly, that one needs 16 gigs of RAM in this period of time, even for just some major browsing on his desktop?

I thought I could safely keep on working with my 8 gigs and that's why I couldn't understand all this hard drive spinning noise (swapping) and consequent slowing down of the whole system, even when my RAM is not full.

I have read quite a few threads about swap. A "long" one was started in may 2020, is that the one you refer to? "Swap - The Age Old Question"

Do you think I could start with decreasing the swap size to 4 or 2 gigs, and moving it to the SSD instead of keeping it on my HD?

Thanks!

---

### Post by TheFu on 2021-09-10
My laptops have 2, 4, 6, and 8G of RAM.
My daily use "desktop" has 4G of RAM.  I limit the amount of RAM that firefox can see by running it inside a sandbox (firejail) and only let it see 8G of RAM - otherwise FF will say it has all the RAM in the system and all the available swap .... though it is probably using less than 1G. I'd expect thunderbird to have a similar behavior, since the same toolkit is used by Mozilla on both projects.
```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND 
 196948 tf        20   0 3974524 782776 259716 S  17.6  19.4  12:19.27 thunder+
```

For a desktop system, running modern browsers, I think there is only 1 answer for swap - 4.1G.  Higher isn't good.  Lower isn't good.
Did you read that long thread or just skim it? In it we outlined the purpose for swap and what different people do. My stance hasn't changed from then. 4.1G using a swap partition/LV.  I don't use swapfiles.

The point of swap is to provide feedback to the user when the system "feels" slower, that their system is having too many demands. The correct answer is to close a hog program, not make more swap.  Especially on a system with 8GB of RAM.

I'm assuming you aren't running CAD or 4K video editing or JAVA on this system.  Browsers, email, some lite coding should all be fine on an 8G system.

---

### Post by Impavidus on 2021-09-10
I wouldn't say you need 16GB these days. On my system:```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7886        1337        5401         264        1147        6044
Swap:          8667           0        8667
```(Yes, I know swap is a bit large. That's what the installer did 10 years ago and I never cared enough to change it.)
This is about an hour after booting, so buff/cache is still fairly low, but that typically increases with uptime. In your post you show over half the memory is used and only a third is still available. Hardly anything is still free. The system could have decided to drop some cache, but it decided to move some stuff to swap instead. I don't know the details of memory management by the Linux kernel, but it's reasonable that there's something in cache that's likely to be used again soon and there may be memory used by applications that won't be used any time soon. In that case, swapping may be better than dropping cache. But of course, memory management may guess wrong.

If you have plenty of cache available and your uptime is long enough, it will get used.

---

### Post by Yellow Pasque on 2021-09-10
If you're one of those people that loves to have 100 tabs open in Firefox/Thunderbird, 16GB RAM is a good idea.
Putting swap on an SSD is a bad idea if the swap gets frequent use, because it can wear out the SSD with a lot of writes.

---

### Post by monkeybrain20122 on 2021-09-10
> **Yellow Pasque said:**
> If you're one of those people that loves to have 100 tabs open in Firefox/Thunderbird. 16GB RAM is good idea

I have 120 tabs open on FF, I have only 6G of ram and it is pretty smooth (of course with addons to block ads and the like and did some optimization) FF manages tabs very efficiently, they are lazy load by default. In contrast for Chromium based browsers you need an extension or they will load all the saved tabs at startup and choke your system, but even with the extension they don't work as well as FF if you have many tabs. This is an old Toshiba netbook (one of those with a stupid secure screw that no one has the screw driver to open to add ram) and running Ubuntu 20.04 with unity-desktop.

---

### Post by MarcoPau on 2021-09-12
One thing I noticed: as soon as I turn on my computer and load Thunderbird (it's usually the first program I run), my RAM gets buffered/cached immediately, even if the system is using 1 gig of RAM.

I am basically starting with 5+ gigs of buff/cache RAM since the very beginning of my computer usage.

Is this supposed to be normal?

Cheers

---

### Post by Impavidus on 2021-09-12
Maybe Thunderbird reads a lot of files?

Do you keep all your old emails and attachments or do you regularly houseclean and store the attachments in a permanent location, whilst destroying the old emails?

---

### Post by MarcoPau on 2021-09-12
I keep all my email, thunderbird is connected to a few Gmail accounts via IMAP, everything is downloaded locally.

Is this causing the massive memory caching? In case it is not supposed to cache like that...

---

### Post by rsteinmetz70112 on 2021-09-12
I also keep a lot of historic email. Moving as much as possible to Local Folders will help somewhat.

On this desktop running 20.04 with only a terminal window,  Chromium and Thunderbird running.
```
$ free
              total        used        free      shared  buff/cache   available
Mem:        8006584     1647732     4071336       29284     2287516     6026296
Swap:      16770068      595044    16175024
```

I have 76 GB of mail in my Thunderbird profile.

If I start Firefox and open a few tabs this is what I get:
```
$ free
              total        used        free      shared  buff/cache   available
Mem:        8006584     2421116     2582012       76264     3003456     5205888
Swap:      16770068      590180    16179888
```


I don't have much of a problem with Thunderbird. I have not done any tuning, this is the default setup.

---

