---
title: "Heavens no! Recovering ext3 partition?"
date: 2006-08-05
forum: General Help
---

### Post by iand675@gmail.com on 2006-08-05
I was planning on doing a clean install of dapper because I just got a cd in the mail, and was planning on deleting the hidden files out of my home directory which is a seperate partition from everything else. Unfortunately, I was going through the installer and I accidentally deleted the partition. I haven't formatted the area as anything else yet, so can I recover my personal files/undo the erase, or is it a lost cause?

---

### Post by Jagot on 2006-08-05
Did you write the changes to disk?  Why don't you boot with the Live CD and you'll be able to see which partitions still exist.

---

### Post by iand675@gmail.com on 2006-08-05
I was using the live disk, and I half wrote the changes. As in, I deleted the partition, but haven't *re*formatted it yet. I found this tool called gpart (not gparted) can anyone verify if it will work?

---

### Post by silvagroup on 2006-08-07
Great question :confused: 
I was trying to install Dapper to a sata drive, which is an impossible task. I had plainly selected sda for the install and Dapper decieded to use hda, all by itself:evil:  That had my working Breezy system and all my files:shock: Now my primary system is shot](*,) 
I was able to stop it as soon as I saw what Dapper had decieded to do, so I am not sure how far it got.
I wonder if I can just use the Breezy cd and install w/o format, will that restore my system[-o< 
We could use some help here](*,)
Just checked w/gparted and shows filesystem unkown, the option is "format to"  then many options. However fromat to mean means that the partion will be formatted and my Breezy files are gone !!!!????:-k
Weird, checked same disk with Ranish Partion Manager and it shows all partions being there as they are suppose to be MBR, ext2fs,swap all there yet  gparted show unkown file system and when booting grub gives me error 17, and my boot drive was this drive, hda. If I do a root (hd0,0) from grub it gives me "filesystem type unknown, patition type 0x83". Yet I can root to (hd1,0,a) bsd just fine.

---

### Post by asimon on 2006-08-08
> **iand675@gmail.com said:**
> I was using the live disk, and I half wrote the changes. As in, I deleted the partition, but haven't *re*formatted it yet. I found this tool called gpart (not gparted) can anyone verify if it will work?
I never used gpart (I usually still use use good old 'fdisk' from the command line), but if you are able to recreate the deleted partition with the exact same values as before, i.e. same start block, same size, same partition type etc., then you should be able to access your filesystem again as long as you didn't overwrote that disk space.

---

### Post by skryking on 2006-08-08
I've used this tool called testdisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

to recover from doing the exact same thing.

seemed to work good for me.

Skryking

---

### Post by bluefightingcat on 2008-01-28
Hi,

I am in a similar situation. By mistake I started formatting my ext3 /home partition when re-installing linux. I realised my mistake and resetted my machine before it the formatting got too far. I used "testdisk" to check my partitions and it seems to be ok (i.e. I have all my old partitions). 

GParted also confirms that all my partitions are there. However my NFTS and /home partitions produce a warning sign. 

Also my system refuses to boot to either windows or linux. Instead it demands that I enter some sort of "system disk" i.e. it is not recognising my NFTS or EXT3 paritions. 

I assume there is a problem with my MBR here?? How should I go about fixing it? 

What would be the best way to get my EXT3 partially-formatted partition back. In reality I only need a few files that I need to rescue from there. All the rest if backed up. 

[edit]I did some more digging around and it seems my NFTS is broken because of a corrupted MFT. According to Gparted I have the following problem:

> Failed to open $MFT/$BITMAP: No such file or directory
Failed to load $MFT: No such file or directory
Failed to startup volume: No such file or directory
Couldn't mount device '/dev/sda1': No such file or directory

I then went into Testdisk and tried to fix the MFT but all I got was this:

> MFT +  MFT mirror are bad. Failed to repair them.

BFC

---

### Post by articpenguin on 2008-01-28
> **bluefightingcat said:**
> Hi,

I am in a similar situation. By mistake I started formatting my ext3 /home partition when re-installing linux. I realised my mistake and resetted my machine before it the formatting got too far. I used "testdisk" to check my partitions and it seems to be ok (i.e. I have all my old partitions). 

GParted also confirms that all my partitions are there. However my NFTS and /home partitions produce a warning sign. 

Also my system refuses to boot to either windows or linux. Instead it demands that I enter some sort of "system disk" i.e. it is not recognising my NFTS or EXT3 paritions. 

I assume there is a problem with my MBR here?? How should I go about fixing it? 

What would be the best way to get my EXT3 partially-formatted partition back. In reality I only need a few files that I need to rescue from there. All the rest if backed up. 

[edit]I did some more digging around and it seems my NFTS is broken because of a corrupted MFT. According to Gparted I have the following problem:



I then went into Testdisk and tried to fix the MFT but all I got was this:



BFC

try running chkdsk on the voulume from windows if you can. If chkdsk fails then the ntfs parition is corrupted as ntfs wont work without the MFT. The MFT is where all the files info location is stored.

---

