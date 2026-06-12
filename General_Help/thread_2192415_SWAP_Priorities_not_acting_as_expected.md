---
title: "SWAP Priorities not acting as expected?"
date: 2013-12-07
forum: General Help
---

### Post by NTL2009 on 2013-12-07
I'm running Ubuntu 12.04, xfce desktop, and I installed ZRAM a few months back, and that is working great (my EM725 is limited to 3GB RAM).

But when the ZRAM fills and it goes to swap to the hard drive, of course things slow down terribly while the disk is being accessed. So I decided to try using a 4GB SDCARD as swap (I know some say this will wear out the sdcard, but they are like $4 now, I'l take my chances ;) ).

So I used gparted to set the sdcard to swap, set the priorities in the terminal with the swapon command so that the sdcard has a higher priority than my hard drive, and things seemed reasonable. So I edited etc/fstab to match and re-booted. Things look OK, but once ZRAM fills it seems to write alternately to the sdcard and the HDD. Here is what I got before, and just after ZRAM filled:

```
xxxxxxxxxxxxxxxxxxx:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    5119996    0    2
/dev/sdb1                               partition    3868156    0    4
/dev/zram0                              partition    756872    386436    5
/dev/zram1                              partition    756872    386896    5

and after more memory intensive tasks.......

xxxxxxxxxxxxxxxxxxx:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/sda3                               partition    5119996    28864    2
/dev/sdb1                               partition    3868156    28920    4
/dev/zram0                              partition    756872    756616    5
/dev/zram1                              partition    756872    756644    5



My etc/fstab entries:


UUID=c8e94d8b-26dd-4eca-b81a-3bd8eabc8242 none swap defaults,pri=2 0 0
UUID=ff3bca9f-3e22-498e-9e89-18935afa6c34 none swap defaults,pri=4 0 0
```

Shouldn't sdb1 (the sdcard) fill before anything goes to sda3 (my hard drive swap)? Is there something wrong in my setup?

TIA - NTL2009

---

### Post by heir4c on 2013-12-07
> (my EM725 is limited to 3GB RAM).

What using you that your 2 zram are full? I have 4GB RAM and 2 swap partitions (on 2 HD in the system) and no swap is used.
The output here of cat /proc/swaps is:
Filename				Type		Size	Used	Priority
/dev/sda6                               partition	5241852	0	-1
/dev/sdb5                               partition	2046972	0	-2

And with the commando top:
KiB Mem:   3642616 total,  2509696 used,  1132920 free,   142184 buffers
KiB Swap:  7288824 total,        0 used,  7288824 free,  1214156 cached

And: a sdcard is no faster than a HD, so it's no useful to change the HD for a SDcard.

---

### Post by NTL2009 on 2013-12-07
The memory usage is the result of opening and closing many, many browser tabs/windows over a few days. Closing and re-opening the browser will free most of the memory. I'm running a Chromium browser, but I don't think it is any worse than others for memory usage.

Other than this sort of browser usage, I do not think I would be swapping.

I'll check the read/write speeds of SD versus HD. I assumed the SD was faster, I may need a high speed card?

-NTL2009

---

### Post by heir4c on 2013-12-07
I thought a SD is not faster than a HD but I can wrong... 
Beside that, you let the computer on? I shut down every day, but I don't know if that is the reason of so much using of the zram and swap.
Maybe you can run it a while without a swap and so to turn off the swap with the command:
```
sudo swapoff -a
```
If you want it on again you use the command:
```
sudo swapon -a
```
The -a stands for 'all'.
See also the man-pages of swapon/swapoff with the command:  man swapon

Or you can get a lower swapiness. See the 1st answer: [http://askubuntu.com/questions/103242/is-it-safe-to-turn-swap-off-permanently](http://askubuntu.com/questions/103242/is-it-safe-to-turn-swap-off-permanently)
Or via this link: [https://sites.google.com/site/easylinuxtipsproject/speed#TOC-The-absolute-number-1:-decrease-swap-use](https://sites.google.com/site/easylinuxtipsproject/speed#TOC-The-absolute-number-1:-decrease-swap-use)

---

### Post by NTL2009 on 2013-12-07
Well, maybe SD is slower - I will research that, and test my own read/write speeds with swap off to see on my machine/card. If so, I'll forget about this!

I do keep my machine on for days/weeks w/o a re-boot. I just sleep it.

Regardless, that priority command should work the way I'm expecting, right? The priority 4 drive should fill before accessing the priority 2.

-NTL2009

---

### Post by NTL2009 on 2013-12-07
OK, so I've determined that SD speeds are much slower than HDD (I got ~ 10 Mb/s reads on my SD, and ~ 65Mb/s on my HDD). So this might not be such a great idea.

I still wonder about the priorities. Maybe it starts to write to the SD, then the SD gets busy so it writes to the HDD? So maybe priorities are not simply based on 'full', but also 'available/busy'? But that might still help - writing to two devices in parallel might be faster than just to the HDD - esp with the faster seek times of the SD (2mSec versus 22mSec for the HDD).

So If I decide to keep this old laptop as my main machine, I'll look into an SSD or hybrid drive. Most likely, I'll retire it to another use that is less memory intensive (a music player).

-NTL2009

---

### Post by heir4c on 2013-12-08
I thought (but I'm not sure) a higher priority has a number that is LOWER than the other. So 2 is higher than 4.

---

### Post by NTL2009 on 2013-12-08
No, from the manpage, [COLOR=#000000][FONT=arial]Higher numbers indicate higher priority[/FONT][/COLOR]:

> **-p, --priority** *priority*Specify the priority of the swap device. *priority* is a value between 0 and 32767. Higher numbers indicate higher priority. See **[swapon]("http://linux.die.net/man/2/swapon")**(2) for a full description of swap priorities. Add **pri=***value* to the option field of */etc/fstab* for use with **swapon -a**.



[COLOR=#000000][FONT=arial]You might be thinking of the defaults, which I think are negative numbers. In that case a -1 has higher priority than -2.[/FONT][/COLOR]

But I couldn't find anything to support my theory that it would start using the lower priority drive if the higher was busy, rather than full.

-NTL2009

---

### Post by heir4c on 2013-12-08
Ok, ThanX for the info.

---

