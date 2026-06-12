---
title: "CD burning issues and limistations"
date: 2007-07-23
forum: General Help
---

### Post by FeraTech on 2007-07-23
Ok so I have some data that I need to burn to CD around 300 meg in data but I have a ton of small sub folders going way past 11 levels.

Every time with any program I have tried Ubuntu hangs up. I found a special burning program from the repos for music CDs with the ability to burn data too and it can only go 7 levels deep.

What is this? I need to burn this CD and get the data saved. Why can't Ubuntu do this? The burner does work and most CDs copy and burn fine except when the directory structure goes too deep. The Nautilus burner simply crashes trying to get to the files.

I am running Fiesty on a AMD64 TL 30 Laptop with 1gig ram.

Please help are there any solid burning programs for Gnome?

---

### Post by AlexThomson_NZ on 2007-07-23
The ISO-9660 spec imposes this (very annoying) restriction.  I believe the RockRidge thing is supposed to override this, but I think it might be broken in nautilus-cd-burner.

I have yet to find a really slick CD/DVD burner for Linux (although I haven't tried K3B)

---

### Post by FeraTech on 2007-07-23
That is not good. It is looking more and more like I need to have a dual boot setup in order to get my work done. 

*There should be a list of things Ubuntu needs to do to stand apart on it's own from Windows. Being able to burn data to a CD should definitly be included. While it can, a sub folder limitation seems very restricting especially for business uses and data backup, which is VERY important.*

---

### Post by stchman on 2007-07-23
> **FeraTech said:**
> Ok so I have some data that I need to burn to CD around 300 meg in data but I have a ton of small sub folders going way past 11 levels.

Every time with any program I have tried Ubuntu hangs up. I found a special burning program from the repos for music CDs with the ability to burn data too and it can only go 7 levels deep.

What is this? I need to burn this CD and get the data saved. Why can't Ubuntu do this? The burner does work and most CDs copy and burn fine except when the directory structure goes too deep. The Nautilus burner simply crashes trying to get to the files.

I am running Fiesty on a AMD64 TL 30 Laptop with 1gig ram.

Please help are there any solid burning programs for Gnome?

Install K3b.  it is the best CD/DVD burner you can get for Ubuntu.

sudo apt-get install k3b libk3b2-mp3

---

### Post by FeraTech on 2007-07-23
THANKS STCHMAN

K3B is the best burning program I have used. It should be included in the Core Ubuntu installation since Nautilus abviously have some flaws in it's CD burning capabilities.

---

### Post by AlexThomson_NZ on 2007-07-23
Sounds good, what a shame there is no native gnome equivalent :(

---

### Post by will_in_wi on 2007-07-24
GnomeBaker?

---

### Post by stchman on 2007-07-24
> **will_in_wi said:**
> GnomeBaker?

While Gnomebaker is a decent CD/DVD burner it does not have near the capability of K3B.

---

### Post by FeraTech on 2007-07-24
Just out of curiosity what does it take for a program to get adopted into the core ubuntu installation?

---

### Post by stchman on 2007-07-24
> **FeraTech said:**
> Just out of curiosity what does it take for a program to get adopted into the core ubuntu installation?

The LiveCD is sitting at about 697MB for a 700MB CD.  It would take getting rid of something.  There is a LiveDVD for Ubuntu and it probably has more programs on it.

---

### Post by ezsit on 2007-07-24
> Ok so I have some data that I need to burn to CD around 300 meg in data but I have a ton of small sub folders going way past 11 levels.

Every time with any program I have tried Ubuntu hangs up. I found a special burning program from the repos for music CDs with the ability to burn data too and it can only go 7 levels deep.

What is this? I need to burn this CD and get the data saved. Why can't Ubuntu do this?

ISO level 1 standards prevent folder hierarchies going past 8 levels deep (the root being the first level). This is to maintain backwards compatibility with older operating systems and software. K3B buring software allows one to over-ride the 8 folder deep restriction, at the cost of possibily making your CD unreadable by some or many computers.

My solution, since CDs are read-only media and I have to copy the data from CD to HD in order to edit and save, is to ZIP all my folders prior to buring to CD. I can have a folder hierarchy well over 8 levels deep, ZIP it up and burn the ZIP file to CD. The ZIP file maintains the directory structure and file permissions, provides built-in CRC checking, and saves space. Think about it.

Now if you must access the files directly from the CD, then you need burning software that allows you to loosen the ISO restrictions on burning, or rearrange your data to fit within the ISO level 1 specification.

PS. Most operating systems now have built-in ZIP file handling anyhow, so just ZIP those deep directories up and burn away!

---

