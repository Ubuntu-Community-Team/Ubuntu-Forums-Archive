---
title: "Partition:how to combine these partitions."
date: 2007-08-13
forum: General Help
---

### Post by Ananth on 2007-08-13
Hi,

This is my secondary hard disk. I want to combine all the (2) partitions to make a single NTFS drive.

[IMG]http://i16.tinypic.com/4ygzgad[/IMG]

The problem is, Gparted won't let me move/resize my data partition (~100gb, sdb5) into the unallocated freespace  (~40gb) sitting before it.

**Little bit of history:**
This drive had a Primary partition, and some logical partitions. I had data in only one logical partition, like this -
[ _Primary_ |  _extended(_ Logical1, **Logical2(Data)**, Logical3)]

I deleted all unnecessary partitions. Enlarged my Data partition to take up the space that follows. I COULDN'T extend the _start _of my Data partition to take up the first 2 partitions. However, I could extend the whole Extended partition so that it spans across the whole harddisk, destroying the primary. 

Then I was able combine first 2 empty partitions (1-formarly primary, 2-logical1) 

Now my problem is, I could not bring the ~40GB unallocated space into my NTFS partition (sdb5) because I couldn't move the NTFS backwards.
[IMG]http://i16.tinypic.com/4qxvl0m[/IMG]

Any help to combine them to make a single NTFS drive, without loosing data, is greatly appreciated.

Note: now gparted allows me to create ONLY logical partitions, not primary ones.

---

### Post by be4truth on 2007-08-13
Try this: Format allocated space with NTFS.
Then shrink this partition as much as possible.
The either move or rezeice your NTFS data partition.
You might have to live with a 8 MB dead partion in front of this.
Can take quite some time. Make sure you have a backup of this data(??) and a UPS depending where you live. A power cut or shut-down will destroy the data.

---

### Post by Ananth on 2007-08-13
Some more info:

Same Hard-disk. Before Surgery. Windows. [note: *Unallocated* and *freespace* are different.]
[IMG]http://i10.tinypic.com/66jm8th[/IMG]

Now:
[IMG]http://i16.tinypic.com/4ygzgad[/IMG]

I want:
|<- /dev/sda5  150 GB -> |

Thank you.

---

### Post by Ananth on 2007-08-13
> **be4truth said:**
> I would format the unallocated space as ntfs and then merge this partitions. Can take quite some time. Make sure you have a backup of this data(??) and a UPS depending where you live. A power cut or shut-down will destroy the data.

Formatting unallocated to NTFS -> done. no issues.
Merge -> how do I it? gparted didn't provide any option, neither did windows disk manager. (reading about partition logic now. will it help?)

Power - no problem. Backup - not possible :( Anyway I'm ok with taking reasonable risk.

Thanks for the instant help be4truth.

---

### Post by be4truth on 2007-08-13
Pls reread my post. I edited it.

---

### Post by Ananth on 2007-08-13
> **be4truth said:**
> Try this: Format allocated space with NTFS.
Then shrink this partition as much as possible.
The either move or rezeice your NTFS data partition.
You might have to live with a 8 MB dead partion in front of this.


I've tried it, with a slight variation. I created a very small ext3 file system at the beginning of the disk, later tried to resize my NTFS partition. Didn't work.

Now I'm retrying it as you told. formatted the space to NTFS. But while shrinking it I get an error message - simulation fails. (may be I should restart. NTFS needs some consistency check or something)

I'll restart, try again and update here.

---

### Post by surfer63 on 2007-08-13
I have no solution to the problem itself, but I had the same issue also once.

What I did was the following (a bit like be4truth).

- formatted the  unallocated partition to NTFS
- shrunk the original NTFS as much as possbile
- moved the original, shrunken NTS partition as far as possible to the end
- increase size of new NTFS partition at the beginning
- Copy over as much as possible from the original NTFS partition to the new NTFS partition.

- repeat steps if necessary.

Please note that GB (windows) and GiB (gparted) are not the same.
108.97 GB = 116.9 GiB. 
However, this still does not make up for the difference.

---

### Post by ajgreeny on 2007-08-13
I don't know which version of gparted you are using but I suggest you get a copy of the newest **gparted liveCD**, burn it to disk and then use that, as it is more up to date than the version in ubuntu live and can do lots more things.


Now boot into that and delete the 37.25 unallocated space.  Now you should be able to move/resize the ntfs partition to the beginning of the disk (not possible with older versions of gparted), though it will take a very long time.  Having done that it should be possible to increase the size of the ntfs partition to the full disk size.  You may be able to carry out both actions in one go, but I've never tried so can't be certain about that.

God luck with the attempt!

---

### Post by Ananth on 2007-08-13
> **surfer63 said:**
> I have no solution to the problem itself, but I had the same issue also once.

What I did was the following (a bit like be4truth).

- formatted the  unallocated partition to NTFS
- shrunk the original NTFS as much as possbile
- moved the original, shrunken NTS partition as far as possible to the end
- increase size of new NTFS partition at the beginning
- Copy over as much as possible from the original NTFS partition to the new NTFS partition.

- repeat steps if necessary.

Please note that GB (windows) and GiB (gparted) are not the same.
108.97 GB = 116.9 GiB. 
However, this still does not make up for the difference.

Yeah, that'll do. But that will be my last resort, when everything else fails. If have to move my data out I have some space in my primary hard disk too. 

Right now i'm looking for some straight forward way to merge/resize using any tool, so that  I don't have to manually move files.

Thanks for the tip.

---

### Post by Ananth on 2007-08-13
> **ajgreeny said:**
> I don't know which version of gparted you are using but I suggest you get a copy of the newest **gparted liveCD**, burn it to disk and then use that, as it is more up to date than the version in ubuntu live and can do lots more things.


Now boot into that and delete the 37.25 unallocated space.  Now you should be able to move/resize the ntfs partition to the beginning of the disk (not possible with older versions of gparted), though it will take a very long time.  Having done that it should be possible to increase the size of the ntfs partition to the full disk size.  You may be able to carry out both actions in one go, but I've never tried so can't be certain about that.

God luck with the attempt!

Thanks ajgreeny. I was using gparted 0.2.5 which is supposed to be the latest in ubuntu repositories. I can't believe I was using such an outdated tool. Latest version seems to be 0.3.3/livecd 0.3.4-8

Downloading livecd now.

---

### Post by Ananth on 2007-08-13
> **be4truth said:**
> Pls reread my post. I edited it.
Done :)

---

### Post by be4truth on 2007-08-13
> **Ananth said:**
> Yeah, that'll do. But that will be my last resort, when everything else fails. If have to move my data out I have some space in my primary hard disk too. 

Right now i'm looking for some straight forward way to merge/resize using any tool, so that  I don't have to manually move files.

Thanks for the tip.

I wouldn't use that at the last but the first resort. Didn't imagine you tried to do that from within Ubuntu. I thought you were on Gparted LiveCD. Sorry for not asking you.

---

### Post by Ananth on 2007-08-13
> **be4truth said:**
> I wouldn't use that at the last but the first resort. Didn't imagine you tried to do that from within Ubuntu. I thought you were on Gparted LiveCD. Sorry for not asking you.

Sorry for not making it clear that I am in Ubuntu.

first resort? I thought (am thinking), if gparted or any other tool allows me to merge my partitions graphically, just as how gparted allowed me to merge other partitions, it is much nicer than moving over 80 gigs of files around *manually.* 

Of course I wouldn't allow gparted/any tool to mess up my data. But expecting that there should be a tool to merge 4 partitions without data loss, where 3 of them are empty sounds reasonable to me.

If the risk of data loss is extremely high, I'll be happy having 2 partitions (40G+100G) rather than desperately trying to combine them.

ps: I'm burning latest partition logic livecd, Will try with that once.

---

### Post by be4truth on 2007-08-13
To use the live cd has 2 advantages:
more features and independent from the operating system.

---

### Post by Ananth on 2007-08-13
Thanks a ton to ajgreeny, be4truth and surfer63 for helping me out.

Latest gparted liveCD did the trick. Here's the final result:

[IMG]http://i10.tinypic.com/5xzufz5[/IMG]

---

