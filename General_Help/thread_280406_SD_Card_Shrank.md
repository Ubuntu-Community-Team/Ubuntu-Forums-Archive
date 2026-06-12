---
title: "SD Card Shrank?"
date: 2006-10-19
forum: General Help
---

### Post by x64Jimbo on 2006-10-19
So here's a real conundrum. I have an SD flash memory card that claims to be 2GB, and I have previously stored far more than 1GB on it, but I had some corruption issues (because I never did a good job of unmounting it first - d'oh!) so I decided to back up all the files and reformat it from scratch. I copied all salvageable files off it last night (about 1.4GB) and reformatted, but now it says I only have 1GB of space. Fdisk and qtparted agree on this. I don't get how this could have happened. Nothing has happened to the device - it wasn't even unplugged in between backing it up and reformatting it. 
Is there a command that I can run to examine the disk at a hardware level and determine its true capacity so that it will show up right in my formatting programs?

---

### Post by chudder on 2007-01-04
Yeah I have the same problem except I there was no corruption at least not that I know of.  I haven't had to reformat.  Ubuntu says it's 1 GB but my treo says it's 2 GB so I'm not sure what this problem is.  I found one other thread but no responses there either.  So this means I can only put 1 GB of music, not 2.  Sorry I don't know what to do.  Anybody know what's causing this and how to fix it?

Thanx to anybody for helping or investigating.

Chud

---

### Post by fragos on 2007-01-04
Some devices don't understand the posibility of SD cards larger than a certain size.  They see a larger capacity card as only having a smaller size.  At one point in time, few devices recognized more than 1GB.  Perhaps the issue relates to which device you formatted the SD on.  Part of this problem relates to difference in FAT versions.

---

### Post by chudder on 2007-01-04
> **fragos said:**
> Some devices don't understand the posibility of SD cards larger than a certain size.  They see a larger capacity card as only having a smaller size.  At one point in time, few devices recognized more than 1GB.  Perhaps the issue relates to which device you formatted the SD on.  Part of this problem relates to difference in FAT versions.

The card is supposed to be 2 GB and actually I just tested it on a windows machine heaven forbid and it said roughly the same amount as the Treo which makes sense since it [the card] never has quite the amount advertised.  So that makes the problem Ubuntu which is bad because it won't let me load on anymore information.  That is my dilemma.  I run Dapper and the Treo runs Palm OS Garnet 5.4 and I formatted the card on the Treo.  Is there a way to remedy this problem?

Thanx for the info.

---

### Post by x64Jimbo on 2007-01-05
Just to update this thread, I installed Edgy and now it works just fine.

---

