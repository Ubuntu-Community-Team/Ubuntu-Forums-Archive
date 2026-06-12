---
title: "Lubuntu 14.04 partly broken after just trying mate 16.04 live usb"
date: 2016-08-15
forum: General Help
---

### Post by Halbarad on 2016-08-15
Hi,

Lubuntu 14.04 64 bits is the only OS I have installed on my laptop (HP, UEFI boot). I wanted to try Mate 16.04: I downloaded the 64 bit ISO file and made a USB live key using the system tool Startup Disk Creator. I checked the box for a persistent area of 1 GB. I always proceeded like this when I wanted to try a new Linux distribution, I wasn't aware of any caveats against Startup Disk Creator with persistence. Anyway, this happened some one month ago and I found no warnings against Startup DC on the web. I tried Mate and found out that no persistence was enabled. Alright, little harm: I left for a journey abroad and stayed away for one month.
On my return (today) I have run Software Update. First it has told me that it can update my system only partly, because... (a list of possible reasons follows, including partial upgrade and ill-behaved third party software). For example, updates of the kernel are disabled. Ok, let's try to update the rest at least. But Software Update says: 
```
CD/DVD 'Ubuntu-MATE 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)' is required

Please insert the above CD/DVD into the drive '/media/cdrom/' to install software packages from it.
```
The weird thing is, I never had that CD. I've tried to plug in my usb key but this isn't what Software Update requires.
Thus, I've run Synaptic Package Manager, clicked the tab "Origin" and had a look at the repositories and the corresponding installed packages. The list of the origins now includes xenial (main, restricted and universe) from Ubuntu MATE 16.04.1 LTS Xenial Xerus.  The following packages turn out to have been installed on my system from Xenial Mate main:
```
dkms
fakeroot
gcc
grub-efi-amd64
grub-efi-amd64-bin
grub-efi-amd64-signed
libatomic1
libc-dev-bin
libc6-dev
libfakeroot
libitm1
libtsan0
linux-libc-dev
manpages-dev
```.

I feel fairly sure that my system is broken. This is the PC I daily use for working, I have tuned it up to meet my needs. I simply cannot afford reinstalling everything now because I don't have time. But the decay of my system is deep and radical, I am afraid that there is no reasonable way of rolling back -- it's not a matter of a version of the kernel; even the grub has been affected. However, someone may know better than me. I'd be VERY grateful if anyone could suggest a way for recovering my system.
(I am shocked at the thought that all the screw up is the consequence of a mere attempt at trying a live usb. This seems to me sort of enormous, disproportionate. If the cause of all is the Startup Disk Creator tool -- I mean, IF that system tool can bring about results like this, it would have been serious to disable it, to deprecate it, to put on it a red cross as big as a house.)

---

### Post by grahammechanical on 2016-08-15
In what way is your system broken? Did you accept the offer of a partial upgrade? I am using the development version of Ubuntu 16.10 and I often see that dialog offering a partial upgrade. I never accept the offer. I simple click continue and the update takes place as normal.

I have no idea how the Ubuntu Mate CD/DVD/USB (it makes no difference) came to be added as a software source. But it can be removed. You need to use the utility where we can change the setting for the frequency at which Update Manager checks for updates. In Ubuntu it is called Software & Updates. I do not know what it is called in Lubuntu.

I have no idea how the Xenial repositories came to be added as software sources in the sources.list file of an install of Lubuntu 14.04. But they can be removed. I do not think that USB creator did it. Has anybody had access to that machine while you have been away?

You will find the sources.list file here: etc/apt/sources.list. It can be opened in a text editor but you will need to be working as administrator or root to edit this file. But at least you can examine the file. Does it actually have URLs for "xenial?" Does it still have URLs for "trusty?"

Apart from this, what else is happening to cause you to feel fairly certain your system is broken?

Regards.

---

### Post by kansasnoob on 2016-08-15
> **Halbarad said:**
> Hi,

Lubuntu 14.04 64 bits is the only OS I have installed on my laptop (HP, UEFI boot). I wanted to try Mate 16.04: I downloaded the 64 bit ISO file and made a USB live key using the system tool Startup Disk Creator. I checked the box for a persistent area of 1 GB. I always proceeded like this when I wanted to try a new Linux distribution, I wasn't aware of any caveats against Startup Disk Creator with persistence. Anyway, this happened some one month ago and I found no warnings against Startup DC on the web. I tried Mate and found out that no persistence was enabled. Alright, little harm: I left for a journey abroad and stayed away for one month.
On my return (today) I have run Software Update. First it has told me that it can update my system only partly, because... (a list of possible reasons follows, including partial upgrade and ill-behaved third party software). For example, updates of the kernel are disabled. Ok, let's try to update the rest at least. But Software Update says: 
[CODE[B][COLOR="#FF0000"]]CD/DVD 'Ubuntu-MATE 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)' is required
[/COLOR][/B]
Please insert the above CD/DVD into the drive '/media/cdrom/' to install software packages from it.[/CODE]
The weird thing is, I never had that CD. I've tried to plug in my usb key but this isn't what Software Update requires.
Thus, I've run Synaptic Package Manager, clicked the tab "Origin" and had a look at the repositories and the corresponding installed packages. The list of the origins now includes xenial (main, restricted and universe) from Ubuntu MATE 16.04.1 LTS Xenial Xerus.  The following packages turn out to have been installed on my system from Xenial Mate main:
```
dkms
fakeroot
gcc
grub-efi-amd64
grub-efi-amd64-bin
grub-efi-amd64-signed
libatomic1
libc-dev-bin
libc6-dev
libfakeroot
libitm1
libtsan0
linux-libc-dev
manpages-dev
```.

I feel fairly sure that my system is broken. This is the PC I daily use for working, I have tuned it up to meet my needs. I simply cannot afford reinstalling everything now because I don't have time. But the decay of my system is deep and radical, I am afraid that there is no reasonable way of rolling back -- it's not a matter of a version of the kernel; even the grub has been affected. However, someone may know better than me. I'd be VERY grateful if anyone could suggest a way for recovering my system.
(I am shocked at the thought that all the screw up is the consequence of a mere attempt at trying a live usb. This seems to me sort of enormous, disproportionate. If the cause of all is the Startup Disk Creator tool -- I mean, IF that system tool can bring about results like this, it would have been serious to disable it, to deprecate it, to put on it a red cross as big as a house.)

When you insert a live DVD or live USB a dialog widow will open asking if you want to install software from that source. You must have clicked yes as evidenced by the highlighted line above.

Lubuntu uses Synaptic. So open Synaptic, go to Settings > Repositories. Under the Ubuntu Software tab look at the bottom where it says Installable from CD-ROM/DVD and you may find that source enabled. If so un-tick it. You may also want to look under the Other Software tab to be certain it's not enabled there.

Once you have found and un-checked the source(s) of the problem you may as well use Synaptic to try and update the system because it has some "smart" tools to try and sort out Broken packages in Custom Filters.

---

