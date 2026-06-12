---
title: "need a floppy-based partition editor"
date: 2007-11-18
forum: General Help
---

### Post by bluepowder7 on 2007-11-18
i'm helping my dad reinstall win2k on his old ibm thinkpad, but the sucker won't boot from any of my ubuntu live cd's so i can't use GParted to clean up the HD.  is there a floppy-based partition editor that'll let me obliterate ALL partitions and set up just ONE basic FAT32 or NTFS partition?  he's only running win2k on it (for work stuff), and it's a small HD so i can get away with a FAT32 (i think it's only 4 or 8 gigs).

heading out for dinner now, but hope to be able to get his laptop working again in a few hours.

thanks in advance!!!


EDIT:

i did think of removing the HD and using one of my 3.5" cases, but i'm thinking that the IDE interface isn't the same size so i won't be able to temporarily re-house the laptop's HD.....  true?

---

### Post by Beaucephus on 2007-11-18
You updated the BIOS to boot from CD, right?  

If so and it still doesn't work there are boot floppies images available for ubuntu.  They should be on the install CD.  

Why do you need Ubuntu for this?  The W2k setup should have what you need.  Can't you just run the W2k install and use the whole drive?

Oh and all IDE is the same.  If the port is smaller, thats because it is for a FLOPPY drive.

---

### Post by bluepowder7 on 2007-11-18
win2k setup tends to crap out and barf out a message that it can't load some file (i have an authentic retail win2k pro cd), so my hope is that using a 3rd party software would help to erase whatever IS on there and give it a clean slate onto which to install itself.  currently, his laptop seems to have corrupted atapi drivers at least within win2k.

bios is set up to boot from cd, but for some reason it isn't actually doing it - at least not on my ubuntu cd's.  it appears to be booting from the win2k installation cd, though, but part way through the install it barfs anyways...

reason for ubuntu?  it's got gparted on it, which i was intending on using to blow away all existing partitions (a FAT that he was using for DOS and an NTFS that he was using for win2k) to reinstall just win2k on a single partition (no more DOS).

hmm, are you saying that a 2.5" laptop hard drive IDE port is the same size as the typical CD drive and 3.5" hard drive?  if that's the case, i may just try to mount his hard drive into one of my external cases, and format using the GParted that's on MY laptop (which has 7.10 installed)

time to whip out the screwdriver!

any other ideas before i take apart a ThinkPad?

---

