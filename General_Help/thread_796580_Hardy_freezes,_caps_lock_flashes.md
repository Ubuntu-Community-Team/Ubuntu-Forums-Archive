---
title: "Hardy freezes, caps lock flashes"
date: 2008-05-16
forum: General Help
---

### Post by joe57005 on 2008-05-16
Hi, i've just installed ubuntu hardy from the liveCD (upgrade from gutsy screwed up my system, so i started new) My system will randomly freeze while on the internet. It happens (less often) while browsing with firefox, and (more often) while downloading usenet binaries. it has not frozen (yet) while downloading torrents. When it does freeze, the mouse and keyboard stop responding, the caps lock light flashes roughly twice a second, and i have to physically disconnect the computer from power to restart it. I have not been able to find any suspicious errors in the system log, so i don't know the cause. i *think* it may be a driver problem with my wireless card, though i had no such problems with gutsy or feisty. (though, feisty had no support for my wireless card at all)
i think my card has the ralink chipset (the brand name is airlink101), but i'm not sure as i'm not at home.
I'm a linux n00b, so any help would be much appreciated.

---

### Post by joe57005 on 2008-05-16
My wireless card shows up thusly on lspci:
02:0A.0 Network controller: RaLink RT2561/RT61 802.11g PCI
The brand on the box is Airlink101 and the model number is AWLH3026

---

### Post by joe57005 on 2008-05-17
I seem to have found a helpful bug report offering some solutions.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200142")
One of the posters recomends installing the linux-backports-modules, i shall try that and report the results.

---

### Post by joe57005 on 2008-05-17
After installing linux-backports-modules-2.6.24-16-generic via synaptic i seem to have no more problems, seem being the key word. I am currently doing everything that would have previously caused a crash, and it has not crashed. As far as i'm concerned, it's cured! i will post an update if it crashes again, but for now, case closed.

---

### Post by karhulitos on 2008-07-07
I have exactly the same. It has happened 2 times now, common nominator being Transmission running over night, so your idea of the problem being related to using internet would match here.

I will test that too after I get 3rd crash.

[edit] it's always Transmission when I get this. It takes few hours of full download or upload when it happens. I don't have rt61 wireless (Atheros ar5007) so I guess I get no help from backports.

---

### Post by zen77 on 2008-09-17
I've had the same problem with Hardy 8.04 on a Toshiba u300. with a different ethernet card. I've also had the problem when running transmission. So it might be when verifying or downloading large files. But recently its started hanging more quickly too!

Any advice would be most welcome.
Cheers!
Total newbie.

---

### Post by darnielng on 2009-02-16
I am using a IBM T43p laptop, model 2669-H2A on a Ubuntu 8.04.2  (Kernel 2.6.24-23)

Here's the problem I face.
1. Unable to caps lock
2. Shift key won't work.
3. Using mouse to highlight words, not working either.

Strange bugs in Linux.

---

### Post by arikitty on 2009-07-28
I have a very similar problem. I just installed Ubuntu 9.04, and I'm dual booting with Windows 2000 Professional. Maybe that has something to do with it? It's not even connected to the internet yet, I need to install the drivers for the dwl 520+ wireless card. Unfortunately, I haven't been able to do that because my computer freezes almost every ten minutes or so, with the caps lock and scroll lock LEDs flashing. I started Memtest before I found this thread, just to see if it would help.

---

