---
title: "Long term effects using a OS on a flash drive?"
date: 2020-09-02
forum: General Help
---

### Post by josephchrzempiec on 2020-09-02
Hello i was curious I'm running viewing monitoring security cameras off of a old desktop i have. The problem is i do not have a hard drive so i decided to run ubuntu onto a Flash drive. I don't have any other use for this computer but to view my office cameras at home on this pc. So i was curious what would be the long term effects to running ubuntu on a flash drive not recording but just viewing only? Would it kill this drive or would it be okay?



Joseph

---

### Post by guiverc on 2020-09-02
Flash drives in my experience suffer no damage from reading.  The writes are what can cause them to fail, so if you're only reading from the thumb-drive I'd expect good life.

I've used thumb-drives on laptops with dead internal drives for weeks-months without issue, but the more writing you do on them, the shorter their life

(*Of a recent 5 pack of verbatim thumb-drives, 3 of the 5 are worthless.. so I'd not recommend verbatim brand be used!*)

---

### Post by josephchrzempiec on 2020-09-02
Hello Guiverc, Thank you. Yes only reading no writing. It's not a slow system but it is a older system a Core two Dual with 3Gb of memoy and a 32GB flash drive only displaying the cameras that is all.



joseph

---

### Post by josephchrzempiec on 2020-09-02
Hello just a quick note. I have been reading Jump drives been really good to run OS system reading and writing. The one i have [https://www.staples.com/LEXAR-32GB-S50-JUMPDR-USB-2-0-2-Pack/product_2607204](https://www.staples.com/LEXAR-32GB-S50-JUMPDR-USB-2-0-2-Pack/product_2607204) I got mine before they went on sale but never used them. But mine are usb 3.0 not the 2.0 like the one in the link. They are 32GB same thing.



Joseph

---

### Post by C.S.Cameron on 2020-09-02
There are many types of flash drives, from SLC NOR good for 1000000 writes to TLC NAND only good for up to 1000 writes. I have a 4GB that I use almost daily for over 13 years, for testing different OS installs, several dozen installs last week alone. I have used Micro SD cards for servers using Live, (read only), Ubuntu installs that have each lasted less than six months. It is hard to tell why a flash drive dies. Wikipedia has a chart showing write endurance for the different flash technologies: [https://en.wikipedia.org/wiki/Flash_memory](https://en.wikipedia.org/wiki/Flash_memory)

I asked a similar question in Ask Ubuntu back in 2015: [https://askubuntu.com/questions/588035/lifespan-a-flash-drive-running-ubuntu](https://askubuntu.com/questions/588035/lifespan-a-flash-drive-running-ubuntu)

---

### Post by josephchrzempiec on 2020-09-03
Thank you all for the hrlp and information. It looks like i might be okay.



Joseph

---

### Post by HermanAB on 2020-09-03
All Apple Macs use solid state drives.  

My Macbook Pro is now eight years old and working better than when I bought it.

So, a SSD may outlast you!

---

### Post by sudodus on 2020-09-03
- A live-only system does not write at all to the drive.

- A persistent live drive does not write much to the drive (except when you save some file or install some program). See [this link](https://help.ubuntu.com/community/mkusb/persistent).

- An installed system may write a lot to the drive. But there are some tweaks, that can reduce the write operations.  See [this link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks).

---

### Post by C.S.Cameron on 2020-09-03
> **sudodus said:**
> - - A persistent live drive does not write much to the drive (except when you save some file or install some program). See [this link](https://help.ubuntu.com/community/mkusb/persistent).

This was my thought when trying to use a Lexar Micro SD card as a movie server for the house while I was on holidays

The first time I just used a persistent install and did not save while I was gone. I was told it died after about six months, no read, no write.

The next year I used a persistent Micro SD set to boot toram. It was still working as a server when I returned six months later but it had gone read only.

I think there may be other factors involved than just the number of writes. The computer I was using sometimes runs a little hot.

---

### Post by HermanAB on 2020-09-03
We have been using SD cards and SSDs in military systems for many years.  Failures are very few and far between.

---

### Post by C.S.Cameron on 2020-09-03
> **HermanAB said:**
> We have been using SD cards and SSDs in military systems for many years.  Failures are very few and far between.

SD cards come in different qualities.
I do not think the military gets their SD cards from Amazon or eBay.
I own at least a dozen bricked Flash drives, SD and micro SD cards.
I can't blame any of the failures on too many writes though.
(I got a great price on a Kingston Traveler in India that was hollow inside).

---

