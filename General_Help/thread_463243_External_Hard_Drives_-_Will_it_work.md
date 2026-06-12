---
title: "External Hard Drives - Will it work?"
date: 2007-06-03
forum: General Help
---

### Post by Fireblend on 2007-06-03
Hello. I currently am using Ubuntu 7.04 on a notebook with really limited storage space. It just has 50GBs and it's about to get full. So I was wondering, is buying an external hard drive a good option? I was browsing amazon for prices and I think I can get a 100GB one at least. 

But are these Ubuntu compatible? Will they be recognized? I'm not sure about compatibility issues they might have with Ubuntu so I thought I would better check. I'm also interested in installing Windows on this machine too since I need it for work, so dual-booting and this machine and handling my files on an external hard drive seems like a good idea, unless I couldn't access it from my favorite OS, of course :p

Thanks in advance!

---

### Post by pseudonym on 2007-06-03
External hard drives made by the major disk manufacturers (eg. Western Digital, Seagate) shouldn't pose any kind of problem at all with *buntu. Just plug it in and it will be autodetected straight away. I had a problem with an external drive enclosure (Vantec Nexstar) in Ubuntu Edgy - trying to mount it locked up my system. When I upgraded to Feisty, however, I was happy to find out that this device works fine now with *buntu.

---

### Post by Fireblend on 2007-06-03
Alright then, thanks for the answer!

---

### Post by Tucatts on 2007-06-03
I use a WD external drive for back up on my dual boot dapper Drake and Win XP syatem. Works like a charm. Shoot the thing is just a BIG flash drive anyway. Go ahead and get one, very good move.
Tucatts

---

### Post by jerremy-tamlin on 2007-06-04
Pseudonym  how did you get your Vantec Nexstar to work on Edgy? I am running Ubuntu Fiesty but my drive, which works fine on my sisters windows machine, isn't detected by Ubuntu. Did yours connect via USB? My Ubuntu doesn't detect it like it does other USB drives.

Any Sugestions?

---

### Post by vanadium on 2007-06-04
Standard USB external drives should work out of the box and connect automatically. I have a Lacie Silverscreen, a big Lacie and a Maxtor, and all are used without any hastle. I reformatted the Lacie from ntfs to fat32, and the big drives to the ext3 filesytem.

---

### Post by indytim on 2007-06-04
I just built my own a couple of months ago.  Included a 320 G Seagate SATA and a case  (Rosewell).  Case supports USB 2.0 and E-Sata.  Cost me about $110USD.  After formatting the HD with GParted Live, works like a charm with Kubuntu 7.04 & 6.10.  

IndyTim

---

### Post by jerremy-tamlin on 2007-06-04
I know it **Should** just work out of the box but it doesn't

I plug in the USB cable, Turn on the HD and ........ Nothing.

My system doesn't have /dev/hda1, etc entries for some reason if this makes any difference. That's a seperate issue on a different thread but I just thought it might be related. I should have a /dev/hda1 entry right the UUID hasn't replaced those entries in /dev/ has it?

Most USB storage devices are detected as /dev/sda1, etc. I have /dev/sca* entries but the NexStar 3 drive just doesn't come up.

---

