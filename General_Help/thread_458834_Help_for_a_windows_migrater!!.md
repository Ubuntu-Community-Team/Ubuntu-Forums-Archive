---
title: "Help for a windows migrater!!"
date: 2007-05-30
forum: General Help
---

### Post by Don Corleone on 2007-05-30
Hi all

So I've finally made the jump. To be honest it was far less painful than anticipated and I don't know why I didn't try Linux sooner. I am impressed with what I have seen so far of Ubuntu 7.04 and my mouth is watering at learning more. 

However, I do need some assistance in trying to get my set up how I want it as certain things do not seem straightforward.

Firstly, I have Vista and Ubuntu installed on my first hard disk in seperate partitions. No problems there. However, now I am faced with the problem of how best to share data between the two operating systems on my 2 other hard disks (both 240gb). Is NTFS OK to use seeing as I found and installed the NTFS Configuration tool? I had previous planned to use FAT32 as I had read that it was the only compatible FS between the 2 OS'es but was stumped when trying to implement this as I was unaware of Microsoft's 32gb limit on formatting and I haven't yet found a way to accomplish this within Ubuntu. I would like to know your own previous experiences with this and any recommendations as to the way I should proceed.

Secondly, I already had a steep learning curve when trying to activate my Wireless internet connection but this is happily accomplished. However, when installing my network card drivers I was greeted with an error when installing the drivers about not being able to compile followed by 2 other prompts and culminating in an error. This did not however seem to prevent the driver from working but I am repeatedly getting the same error whenever I install packages with the add/remove programs, though again this doesn't seem to prevent the packages from installing or functioning. I would like to know how to cure this fault in my set-up so that installations run smoothly.

The error in full is:

A package failed to install.  Trying to recover:
Setting up driverloader (2.26tiabocom) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.26tiabocom

No pre-built modules for: Debian-4.0 linux-2.6.20-16-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.20-16-generic/build] 


Thirdly, I have used Emule for a couple of years now on windows but am now wondering whether to switch to BitTorrent. Any thoughts from people that have used both apps?

Thanks for anybody that has taken the time to read this. Your input will be very appreciated.
Now gimme some answers or I'll send the boyz round!

DC

---

### Post by Don Corleone on 2007-05-30
And just one more thing! Whats the deal with firewalling Ubuntu?

---

### Post by Famicommie on 2007-05-30
I haven't personally tried it, but it seems as though NTFS read/write drivers work pretty well in Ubuntu. There are numerous success stories, but there are definately some horror stories out there as well. A better option might be to install drivers to your Windows drive that will allow you to read/write to/from an ext3fs. You might consider expirimenting with both and using the one that works more naturally for you.

As for your wireless, it sounds as though it is complaining about not being able to find gcc. Have you installed gcc?

I was an eDonkey user for years, then an eMule user for years, and now I am a bittorrent user. I love bittorrent, and I don't think I'd ever go back to anything else. If the torrent is well seeded, then there are no horrendously long queue times and downloads seem to be much faster than what I was able to get on the eMule network. I would certainly recommend giving bittorrent a shot.

I *believe* that Ubuntu has built in iptables or some such firewall protection built in. If you are behind a router, it is even less of a necessity. But, if you insist on using a firewall, then I recommend Firestarter. It is quite a handy little app.

---

### Post by Don Corleone on 2007-05-30
I have installed GCC. See pic

Any other ideas? where does it keep getting called up from or alternately where can I point it to that it will be happy? all my files are in default locations.

It seems that driverloader is producing the error?

edit: can't insert the pic. Anyway it said I have GCC, GCC 3.4 Base, and GCC 4.1 installed.

---

