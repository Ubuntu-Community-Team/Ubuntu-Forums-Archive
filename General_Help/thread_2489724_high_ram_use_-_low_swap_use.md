---
title: "high ram use - low swap use"
date: 2023-08-08
forum: General Help
---

### Post by coley9225 on 2023-08-08
I've been getting oom errors and shut downs lately. Normally, overnight, firefox gets shutdown. I looked at journalctr and notice oom issues, and firefox is killed. I've uped the swapiness(using a 9.5 GB swap partition) to 70. I still see high ram use, and very little swap use. What else can I try?

Results of free -m

```
charles:$:free -m               total        used        free      shared  buff/cache   available
Mem:            7761        5412         133         952        2215        1096
Swap:           9765         351        9414



```

Return of lsblk, minus the loops(snaps).
```
 sda       8:0    0 931.5G  0 disk &#9500;&#9472;sda1    8:1    0   200M  0 part /boot/efi
&#9500;&#9472;sda2    8:2    0  48.8G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                 /
&#9500;&#9472;sda3    8:3    0     1M  0 part 
&#9500;&#9472;sda4    8:4    0   240G  0 part /home
&#9500;&#9472;sda6    8:6    0   250G  0 part /home/charles/.Shared_files
&#9492;&#9472;sda11   8:11   0   9.5G  0 part [SWAP]
sdb       8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1    8:17   0   293G  0 part /media/charles/copies
&#9500;&#9472;sdb2    8:18   0   250G  0 part /run/timeshift/backup
&#9474;                                 /media/charles/506a121f-dee0-445f-9e55-45ab6dea02da
&#9500;&#9472;sdb3    8:19   0   250G  0 part /media/charles/backintime
&#9492;&#9472;sdb4    8:20   0 138.5G  0 part /media/charles/media
sr0      11:0    1  1024M  0 rom  

Not sure what else I can try[I].

[/I]I installed gnome system monitor and notice my system was still using the swap *file* rather than the partition, which I fixed. I am still, on occasion, getting high ram use, and minimal swap use. I've considered changing swappiness to 80, 90, whatever, but I feel the system(kernal) should move inactive stuff to the swap. The results from the free command were while using nothing but YouTube, on google chrome. I normally have multiple items running, 2 separate instances of Firefox, 1 google chrome, Thunderbird, etc. As I'm typing this, I am watching the system monitor, and running "free -m", I currently am at:
[CODE]charles:$:free -m
               total        used        free      shared  buff/cache   available
Mem:            7761        5603         301         757        1856        1100
Swap:           9765         516        9249



```
Memory near full, and swap barely touched.

At a loss for ideas at this point. I'm just tired of the computer lagging and getting to point of the dreaded oom-reaper and shutdown apps, rather than swap them to swap partition.

As always, any insight, ideas, tips, would be greatly appreciated.
And as always, thank you in advance.

---

### Post by guiverc on 2023-08-08
I'll suggest looking at what *extensions* you have installed on your browser, given you mention `firefox` being shutdown.

`systemd-oomd` was introduced during the *jammy* or 22.04 cycle; and you'll see it mentioned by me [here]("https://ubuntu-mate.community/t/what-all-is-inbound-with-22-04/25130/3")  (*its a Ubuntu-MATE community page where I typed that, but my system is multi-desktop & I'm mostly using Lubuntu/LXQt, but also have installed Xubuntu/Xfce, Ubuntu/GNOME...* but the DEsktop makes no difference with this).

Up until my last PC died late last year, I was using a 2009 dell as my primary PC; alas its PSU died & it was replaced with this newer (2017) PC I now use, where I no longer care about this issue (*faster/newer cpu with fancier opcodes that bypass the issue, **more RAM, M2 SSD* etc).. anyway as I state in the provided link

> I have had an issue with browser extensions for a couple of years in  both chromium & firefox; the issue doesn't occur if I don't use  these extensions, but does when I do & I prefer using them thus I  do.


 I've learnt to manage the issue via htop being left  running in a terminal window; and when I detect signs of  growing-RAM-usage by either browser I confirm with my running htop & then close the browser down.. let the kernel clear up the RAM & when I see evidence of that (again on htop window) I restart the browser(s).



ie. I'd check your browser extensions.  

 If I wanted perfect performance I could have used both `chromium` & `firefox` without the *memory-leaking* extensions I liked using.. Alas I decided I preferred the extensions & just managed the OOM issues from ~2017 (*or whenever the ram leak started*) through to the introduction of `systemd-oomd`, that did nothing except change how I dealt with those *leaky* browser extensions.

---

### Post by coley9225 on 2023-08-08
Thank you guiverc.. I thought I had all extensions disabled, but I was mistaken...never wrong...just mistaken...lol.
 I don't know if something in the background stopped, or if this made an instant difference, but ram dropped from ~90% to ~ 40. I'll run this and see what happens. That help with the issue that pointed me to memory/swap issue..(things shutting down)..but still doesn't help with why my swap is'n't taking more of the load for the idle pages.

I'm a little confused as to why increasing my swap(from the swap file of 512MB) to the swap partition of 9+ GB still show high ram and low swap use.

Disabling the extensions may help with the unexpected shutdowns of Firefox,  or lagging during streaming shows(possibly unrelated,but at 100Mbts/s you'd think it would run fine).

Been watching the system monitor since dropping extensions since killing extensions, and still low ram hit(down to ~40%)., with no other changes.

I'll run like this for a while. I don't use real high ram app often, but if I do, It would be nice to NOT have a surprise shutdown of an app.

---

### Post by Quarkrad on 2023-08-09
Swappiness controls when the kernel will use the swap partition/area rather than RAM - or a better way of saying it when the RAM starts to get full the kernel will start using the swap area.  Swappiness can be between 0 and 100 - the lower the value the more the kernel will try to utilise the fast RAM memory rather than slowing things down transferring to the swap area.  The kernel is best at deciding how it utilities memory.  Ideally you want to use your fast RAM as much as possible and never use the swap area.  There is a very good explanation in the answers here [https://askubuntu.com/questions/157793/why-is-swap-being-used-even-though-i-have-plenty-of-free-ram](https://askubuntu.com/questions/157793/why-is-swap-being-used-even-though-i-have-plenty-of-free-ram). (Now you have disabled your extensions change your swappiness to 10 and see what happens to your overall performance.  I always change my swappiness to 10).

---

### Post by coley9225 on 2023-08-09
Thanks for the link quarkrad. A rather long read, but worth the time. Since disabling extensions in Firefox, I was amazed at the difference in ram use, My ram use has stayed below 60%, and swap use in ~350MB. I've decided to reduce swappiness to 40, and let the kernel do it's job, and see how things go. I appreciate the help. I'll mark as solved for now, and revisit the issue, if need be, at a later time.

---

