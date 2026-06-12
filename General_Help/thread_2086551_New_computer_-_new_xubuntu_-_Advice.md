---
title: "New computer - new xubuntu - Advice?"
date: 2012-11-21
forum: General Help
---

### Post by anichols on 2012-11-21
I put in an order a few days ago for a Toshiba laptop - specs below - and plan to scrub it clean of it's preinstalled Windows infestation in favor of the latest version of xubuntu (12.10, if I recall properly).  Since I'm using 12.04 right now (didn't upgrade because I was getting new hardware soon to replace this nearly unusable machine), I was wondering what advice you would offer for configuring this new machine.

1) What would you recommend for the swap partition (if any)?
2) How would you get NVIDIA's Optimus tech to work...or would you bypass it via BIOS?
3) How large of a root partition would you recommend (going to have a /home partition taking most of the drivespace)?
4) Would you recommend using RAID-1 for this configuration, and if #1's answer is greater than zero, RAID-0 for the swap partition for added performance when I do use it?

Tech specs:
```
Toshiba Satellite P870-BT3G22 Laptop

Intel®  Core&#8482; i7-3630QM Processor (6M Cache, up to 3.40 GHz) with Intel® Turbo  Boost Technology
Windows 8
8GB DDR3 1600MHz (4GB + 4GB)
500GB HDD  (5400rpm, Serial-ATA)
500GB 2nd HDD (5400rpm, Serial-ATA)
2GB GDDR3  NVIDIA® GeForce® GT 630M with NVIDIA® Optimus&#8482; Technology
DVD  SuperMulti drive
Glossy Black LED Backlit Tile keyboard
17.3" diagonal widescreen HD+ (1600x900) TruBrite® LED Backlit display
WiFi® Wireless networking (802.11b/g/n) with Bluetooth® version 4.0
Microsoft® Office (trial)
Norton&#8482; Internet Security 2013 (30-day trial  subscription)
1 Year Standard Limited Warranty (1 Year on Battery)
3 Year SquareTrade Accidental Damage Service + 2nd/3rd Year Extended Service Plan (1 Year on Battery)
**PSPLFU-05R011 + ****SQT-N1GQ3V7**
```Thank you in advance for any help you can offer me.  Been using ubuntu since Hardy Heron and xubuntu since Unity, but it's always best to get advice from others who have been using the OS longer. ^.^

- A

---

### Post by kurt18947 on 2012-11-21
Personally I'd think twice about totally nuking Windows.  Remove any crapware, included apps and anything else you'll you'll likely never use then shrink the partition to the result plus maybe 20% or so.  I have things like GPS or printer firmware upgrades which simply cannot be done except with Windows.  I'm not a heavy user but have 4 GB. RAM and no swap partition.  If I feel the need, I'll create a swap **file.**  This doesn't use up one of the 4 partitions I can have.  The only thing I know a swap partition can do that a swap file cannot is allow hibernation, or suspend to disk. If you wanted to use hibernation, you'd need a swap file the size of your RAM plus some.  I use suspend (to RAM) or just shut down.  Ubuntu boots pretty fast.  Your other questions I have no idea, sorry.  Good luck with your new machine, Toshiba has a pretty good rep.

---

### Post by pqwoerituytrueiwoq on 2012-11-21
[http://askubuntu.com/questions/203400/nvidia-optimus-and-ubuntu-12-10](http://askubuntu.com/questions/203400/nvidia-optimus-and-ubuntu-12-10)

raid 1 copies the data on to both drives allowing faster read speeds and if one drives fails your data is safe, you would have 500GB storage
raid 0 woud give you faster read/write speeds if one drives fails all data is lost since part of each file is on both drives, you get 1tb of storage

the installer on 12.10 does not support raid, i think you can use the mini iso or the server iso and get raid

---

### Post by anichols on 2012-11-21
> **pqwoerituytrueiwoq said:**
> 
raid 1 copies the data on to both drives allowing faster read speeds and if one drives fails your data is safe, you would have 500GB storage
raid 0 woud give you faster read/write speeds if one drives fails all data is lost since part of each file is on both drives, you get 1tb of storage

I'm thinking of doing RAID-0 on the swap partition (if I have a swap partition)....if I lose a drive, who cares, it's a swap partition.  I'm not losing any vital data.
RAID-1 would be for Home...not only will it protect the data, but it allows me to voluntarily degrade the array on occasion (swapping in a new 500 GB drive and rebuilding) to take the twice-yearly full backup of the system.

But if XUbuntu's current revision doesn't support software RAID, then I'd have to rethink the usage of sdb.

---

### Post by anichols on 2012-11-21
> **kurt18947 said:**
> Personally I'd think twice about totally nuking Windows.  Remove any crapware, included apps and anything else you'll you'll likely never use then shrink the partition to the result plus maybe 20% or so.  I have things like GPS or printer firmware upgrades which simply cannot be done except with Windows.  I'm not a heavy user but have 4 GB. RAM and no swap partition.  If I feel the need, I'll create a swap **file.**  This doesn't use up one of the 4 partitions I can have.  The only thing I know a swap partition can do that a swap file cannot is allow hibernation, or suspend to disk. If you wanted to use hibernation, you'd need a swap file the size of your RAM plus some.  I use suspend (to RAM) or just shut down.  Ubuntu boots pretty fast.  Your other questions I have no idea, sorry.  Good luck with your new machine, Toshiba has a pretty good rep.

I might keep windows as an ISO file (and virtualbox to it should I ever need it)...as for RAM, the laptop can go up to 32GB...but I'm not paying for that out of the starting gate.  The laptop's pricey enough as it is, after all.  But if you think I can go without a swap partition without issue (either in using the OS or from the installer screaming at me the way older versions did when I tried to go swap-free)...

---

### Post by pqwoerituytrueiwoq on 2012-11-21
> **anichols said:**
> I'm thinking of doing RAID-0 on the swap partition (if I have a swap partition)....if I lose a drive, who cares, it's a swap partition.  I'm not losing any vital data.
RAID-1 would be for Home...not only will it protect the data, but it allows me to voluntarily degrade the array on occasion (swapping in a new 500 GB drive and rebuilding) to take the twice-yearly full backup of the system.

But if XUbuntu's current revision doesn't support software RAID, then I'd have to rethink the usage of sdb.
the alternate cd is required for a raid install, they quit doing those for non-lts, there may be a way to install the installer used in the alternate cd and run it in a terminal

---

### Post by anichols on 2012-11-22
> **pqwoerituytrueiwoq said:**
> the alternate cd is required for a raid install, they quit doing those for non-lts

So grab the latest LTS's alternate CD and then do an upgrade from there to the current version after the LTS is fully installed?

Editing with more info:
I found the alternate for the latest version of Xubuntu in the Daily Builds section... would that be a better idea than going the LTS -> Upgrade route so I can install to RAID-1?

[http://cdimage.ubuntu.com/xubuntu/daily/current/](http://cdimage.ubuntu.com/xubuntu/daily/current/)

---

### Post by anichols on 2012-11-23
Bump

Should I even bother with a swap partition for this new machine?
Would disabling Optimus in BIOS allow me to use the discrete card, or restrict me to onboard graphics?
How much space should I allocate to root (assuming a separate home partition)?  I'm guessing 5 GB....maybe 10 tops?

---

### Post by Cheesemill on 2012-11-24
As of 12.10 the standard desktop installer lets you set up RAID during installation.

---

### Post by Impavidus on 2012-11-24
> **anichols said:**
> 
How much space should I allocate to root (assuming a separate home partition)?  I'm guessing 5 GB....maybe 10 tops?
I don't think it really matters whether your /home is 480 or 490 GB (if you can fill 480, you'll fill 490 just two weeks later), so you can better make sure that you'll never run out of space in /. For the OS and basic programs 10 GB is enough, but it's best to keep some reserve, so you don't run immediately into trouble when your log files start to grow uncontrollably as a result of some error (it does happen) or when you decide to install a program that comes with a lot of data (flight simulators and the like), although you could always move large amounts of program data to /home.

I'd say between 10 and 30 GB for /, but it really depends on how you want to use your computer. And I'm sure people will disagree with me.

---

### Post by kurt18947 on 2012-11-24
> **anichols said:**
> I might keep windows as an ISO file (and virtualbox to it should I ever need it)...as for RAM, the laptop can go up to 32GB...but I'm not paying for that out of the starting gate.  The laptop's pricey enough as it is, after all.  But if you think I can go without a swap partition without issue (either in using the OS or from the installer screaming at me the way older versions did when I tried to go swap-free)...

Scream at you? No, but it'll ask if you're sure.   Another approach you could take with Windows would be to do an initial install, remove what you want then create an image.  I've done this and the image restored nicely.  I've never tried to image a restore partition, delete the restore partition then try to reinstall so don't know if that would work or not.

---

### Post by anichols on 2012-12-03
> **kurt18947 said:**
>  Good luck with your new machine, Toshiba has a pretty good rep.

Thank you for the good luck, but I had anything but.  The machine's Secure Boot was enabled by default (expected), BIOS/UEFI was inaccessible (not expected and required a call to Toshiba), Toshiba ended up passing me to an 'advanced technician' who immediately tried to get me to sign up for an 'upgraded service plan' worth $159....which I refused.  The rep told me he was unable to help me unless I agreed to be shaken down for the additional cash (in spite of an extended 3 year service plan I paid over $200 for), so now I'm in the process of returning the laptop, it's accompanying backpack...demanding a full refund (nearly $1500).

I am now firmly against Toshiba as a company, and strongly recommend any Ubuntu user avoid this company as if it had the plague.  I will never purchase another product from this company, even secondhand with Ubuntu preinstalled.  Thanks, but no thanks...now I'm in the market for yet another new laptop, using one that's highly unstable and prone to breaking down at the drop of a hat.

Any suggestions on a better company to spend my money with?  Requirements: Quad-core processor, NVIDIA graphics, full-size lighted keyboard with 10-key, dual hard drives, DVD R/W or better....basically a computer comparable to what I had but actually usable?  I'm -not- using Windows 8 for the same reason I'm on XUbuntu instead of Ubuntu (dislike of Unity and Gnome 3)...plus the added reasons I'm not on Windows (unstable, prone to viruses, prone to malware, prone to rootkits, insecure out of the box)...

---

### Post by Cheesemill on 2012-12-03
For laptops with Ubuntu pre-installed you could take a look at System 76.

[https://www.system76.com/](https://www.system76.com/)

---

### Post by anichols on 2012-12-04
> **Cheesemill said:**
> For laptops with Ubuntu pre-installed you could take a look at System 76.

[https://www.system76.com/](https://www.system76.com/)

I actually was giving them a look yesterday, but I was half-asleep so I didn't go through it in depth.  Going back for a second look at some point tonight or tommorrow morning. :KS

---

