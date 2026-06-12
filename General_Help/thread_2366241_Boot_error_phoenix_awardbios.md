---
title: "Boot error phoenix awardbios"
date: 2017-07-15
forum: General Help
---

### Post by mariophile on 2017-07-15
Allright so I am new to linux and such so there might be some rookie mistakes here but I believe I've done most of what I could.
Here's the pc specs: 
CPU Amd athlon XP 1900+ 1.46Ghz
RAM 768MB (1x 256 and 1x 512 mb i believe)
GPU a9550/td/128m/a
MOBO k7vta3 v6.0

So I made my usb bootable with unetbootin for lubuntu and when i set boot priority to usb-zip 1st hdd 2nd 3rd disabled and enable boot from other device it just stops before boot and says "boot error" every time and then I have to turn pc off.
Here's the video: [https://youtu.be/-yRI6wdEtu8](https://youtu.be/-yRI6wdEtu8)

---

### Post by yancek on 2017-07-15
I seriously doubt that USB-zip is going to work.  You could try USB-HDD or one of the options under the HDD since you seem to have several available.

---

### Post by mariophile on 2017-07-15
none of the usb options work but bruh i burned a dvd and it seems to work like a charm!!! thanks for the quick reply

---

### Post by mariophile on 2017-07-15
but then it doesnt work again when i try to load with safe mode...
its like this
```
sr0 tag#0 sense key : medium error current
sr0 tag#0 add. sense: l-ec uncorrectable error
sr0 tag#0 cdb: read 10 28 00 00 03 cc 37 00 00 02
blk_update_request: I/O error, dev sr0 sector 995572 (changing a lot)
blk_update_request: I/O error, dev loop0, sector 993914( also changing a lot) 
```
and itz going at it for a long time and now i got a blackscreen but the pc and dvd 
and now it does the same thing and it said no support in radeon module

---

### Post by mariophile on 2017-07-15
ok i got lubuntu to start and now when installing it says i have a problem with my media.... probably the disc or whatever the reason but can i seriously be this unlucky to spend 10 hours installing linux/ubuntu or smth and not get a single positive result. I run the lubuntu without installing and i cant open mozzila to do anything. im going slightly mad.

---

### Post by pqwoerituytrueiwoq on 2017-07-15
use the test disk media in the dvd's boot menu, could be a bad burn (use lowest burn speed) or download (using the torrent download will prevent that)
some old systems are finicky about what usb if any can be used to boot from

---

### Post by mariophile on 2017-07-16
The worst thing is i dont have any dvds left to try and burn. What software do you suggest for burning and cleaning discs? And I used a torrent download.

---

### Post by pqwoerituytrueiwoq on 2017-07-16
on windows i use infra-recorder ( [http://infrarecorder.org/](http://infrarecorder.org/) ), on linux i use what ever comes with the distro eg xfburn

---

