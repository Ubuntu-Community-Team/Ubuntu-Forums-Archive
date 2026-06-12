---
title: "Ubuntu based distros very slow after fresh install (dual boot)"
date: 2017-02-11
forum: General Help
---

### Post by joegp on 2017-02-11
Hi, as you can tell this is my first post.

I'm having a weird and annoying issue, i'm running win 10 and i'm trying to also dual boot into linux, preferably some sort of ubuntu based distro, those seem to be the most friendly towards new users, at least from what i can gather.

I tried Ubuntu Mate 16.04.1, KDE Neon LTS user edition-20170119-0019-amd64, and kubuntu-16.10-desktop-amd64 (all 64bit)
All of them ran fine in a live session (while installing from a USB drive) and all of them run incredibly slow after installation finishes, tried rebooting, didn't help. 
In fact with many of them i couldn't even get the shutdown menu to show up so i had to hard restart.

By slow i mean it took 30 minutes to install Grub customizer (from the terminal), it takes 5-30 seconds for a "start" menu to appear, 15-30 seconds for text i paste to appear, etc.
For the first 30 second they ran kinda OK but then they quickly slow down and i checked in Mate's system monitor, my CPU was barely being used, like 1-3%, normal ram usage (~800MB), nothing unusual.

I already posted about this on linuxforums.org/forum/installation/209083-linux-incredibly-slow-after-fresh-install.html (in case anyone wants to read that), they couldn't help, i figured i'd have more luck here.

But that is a long read so i'll try to sum it up here.

Windows 10 is running off of an SSD and i'm trying to install linux on a spare 1.5TB HDD i have (i hear it's safer this way)
My Bios was in Legacy mode (not UEFI) and in IDE mode (not AHCI) the first 2 times i installed linux, we figured that might be a problem so i fixed that and even reinstalled win 10 and changed the boot record over to GPT (for both the SSD and the linux HDD), this seemed to improve things slightly on Ubuntu Mate (the 2nd time i installed it), although Kubuntu had nasty visual glitches even after installing the proprietary nvidia drivers. The first time Kubuntu booted it froze, i didn't even get to log in.
I tried Kubuntu because i like KDE and because it used a newer kernel than the other two, 4.8 if i'm not mistaken.

System specs: Intel i7 3440 CPU, Asus P8H77-V LE mobo, 16GB RAM, nVidia Geforce GTX960 4GB, 128GB Samsung SSD, 1TB HDD, 2x 2TB HDD, 1.5TB WD Green HDD (this is the one used for Linux)

I made a 50GB ext4 partition for the root partition, 10GB for swap, in some instances i didn't make a home partition in others i did.
I did a hard drive test before any of this with HDD Scan, drives runs better than i expected, only 7 sectors below 500ms access time.

In case i missed anything feel free to ask but there is a high chance i already mentioned it in the linuxforums thread.

My only options now are to try a non-ubuntu based distro, i downloaded Manjaro Deepin 16.10.3, couldn't even get it to boot into live or install, seems i didn't use the proper tool for making a bootable USB drive.
I also downloaded but have yet to try Fedora 25-KDE-x86_64-20170202 and GeckoLinux_Plasma_NEXT.x86_64-422.170205.0.
It was also suggested that i install from DVD instead, have yet to try that, but i don't see how that would help.
My BIOS is not the latest version, but i'm affraid to flash a newer one on it, never done it before, i hear it can be quite risky.

Forgot to mention i only have on machine available and i do my work on it. Barely have time for the 1-2 hours it takes to install linux.

Any help would be appreciated.

EDIT:

Not a single view or reply in 7 days, sorry to say but this forum is useless.

---

