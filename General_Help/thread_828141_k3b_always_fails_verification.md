---
title: "k3b always fails verification"
date: 2008-06-13
forum: General Help
---

### Post by KingTermite on 2008-06-13
Still fairly new to Ubuntu. Everywhere I hear, k3b is the cat's meow for CD burning. So I've been using it to burn the few data CDs that I've burned.

So far I've burned about 4 or 5 discs probably since coming to Linux a month ago. I have learned from years past to not be impatient, but use a lower burning speed.

I set k3b to the lower burning speed (10x I think it was) and typically  have verification set to true.

I usually see it burn with no issues, then it pops the CD out and fails because it can't verify because it can't close CD tray (laptop). No problem, I manually close it and let it continue.

Then, however, at the end I get the "wah-wah-wah" failure sound and it tells me the disc failed verification. Bums me out. However, when I check CD and/or try to use it it seems fine.

Anybody else experience this behavior? Know why it is or how I can fix it?

---

### Post by wolfen69 on 2008-06-13
does this happen with Brasero?

---

### Post by KingTermite on 2008-06-13
> **wolfen69 said:**
> does this happen with Brasero?

Never tried it?

Is that installed by default or in the repositories?

---

### Post by cariboo on 2008-06-13
I've had the same problem, I usually just burn at 8X and never have a problem with making coasters. I believe there has been a bug report filed, but I can't find it at the moment.

Jim

---

### Post by wolfen69 on 2008-06-13
> **KingTermite said:**
> Never tried it?

Is that installed by default or in the repositories?

it comes with ubuntu hardy. works great for me.

---

### Post by avtolle on 2008-06-13
> **KingTermite said:**
> Never tried it?

Is that installed by default or in the repositories?
Brasero is installed as default under Gnome. I've used it multiple times and not had any problems with it on the verification unless there was a problem with the burn itself, which happened once with a lesser-quality CD-RW I used in a pinch.

---

### Post by KingTermite on 2008-06-13
I was on k3b's website, couldn't find it either.

Oddly, I only saw 2 speeds available this morning, whatever default high speed was and 10x (or maybe it was 16x, I can't remember). I usually burn at the slowest or close to it....too many coasters over the years (even more important when making audio discs).

> **cariboo907 said:**
> I've had the same problem, I usually just burn at 8X and never have a problem with making coasters. I believe there has been a bug report filed, but I can't find it at the moment.

Jim

---

### Post by KingTermite on 2008-06-13
> **avtolle said:**
> Brasero is installed as default under Gnome. I've used it multiple times and not had any problems with it on the verification unless there was a problem with the burn itself, which happened once with a lesser-quality CD-RW I used in a pinch.

OK then...I'll try Brasero next time. :) Thanks.

---

### Post by bingoUV on 2008-06-13
These questions are to determine checksumming ability of your system. It is NOT a joke : 

1. Do you run torrents? Can you complete large torrents successfully?

2. Take any large file (about 1 GB or more). Run the following command on it twice. Does it report the same output both the time?
```

sudo ionice -c3 sha1sum <filename>

```

---

### Post by KingTermite on 2008-06-13
> **bingoUV said:**
> These questions are to determine checksumming ability of your system. It is NOT a joke : 

1. Do you run torrents? Can you complete large torrents successfully?

2. Take any large file (about 1 GB or more). Run the following command on it twice. Does it report the same output both the time?
```

sudo ionice -c3 sha1sum <filename>

```

I'm at work and can't run it right now, but yes I run torrents. In fact, the CD in question that I was burning this morning was the ISO image for Ubuntu 7.10 that I got via torrent.

I did run md5sum on it and compare it against the official checksum and it was correct.

Usually I just download TV shows that are about 350Mb a piece. Never checksummed them, but never had trouble with them either.

---

### Post by bingoUV on 2008-06-13
> **KingTermite said:**
> I'm at work and can't run it right now, but yes I run torrents. In fact, the CD in question that I was burning this morning was the ISO image for Ubuntu 7.10 that I got via torrent.

I did run md5sum on it and compare it against the official checksum and it was correct.

Usually I just download TV shows that are about 350Mb a piece. Never checksummed them, but never had trouble with them either.

If you transmission or rtorrent, you are fine. If you use deluge or ktorrent, verify using the sha1sum command I gave. These 2 are not reliable. (ionice is just so that it does not interfere with your regular work, not necessary). Any other client, I am not sure, better verify.

---

### Post by KingTermite on 2008-06-13
Let me clarify...."all" the files I've tried to burn to CD were not from torrents. The one this morning, in particular, happened to be. The torrent client I use is Azerus.

---

### Post by bingoUV on 2008-06-13
Yes, I understand that. There could have been memory stick malfunction that can cause occasional checksum failure. I have faced exactly that.

Don't know about azureus. rtorrent and transmission are honest and repeat downloads when checksum fails (because of bad memory). Deluge and ktorrent are dishonest and say torrent completed successfully and start seeding. Only when you ask them to reverify do they see the problem.

---

### Post by KingTermite on 2008-06-15
> **bingoUV said:**
> These questions are to determine checksumming ability of your system. It is NOT a joke : 

1. Do you run torrents? Can you complete large torrents successfully?

2. Take any large file (about 1 GB or more). Run the following command on it twice. Does it report the same output both the time?
```

sudo ionice -c3 sha1sum <filename>

```

OK, I tried this just now. The largest file I could find was about 800MB. This is a file I got over the torrent.

I ran this command 3 times and got same result every time.

---

### Post by akudewan on 2008-07-06
IMO, it may be some kind of bug with k3b. I'm facing the same problem when burning ISO images.

I burned an Ubuntu iso, k3b said data verification failed. But when I booted the CD and ran "Check CD for defects", it showed that the CD was allright.

Verification with data CDs/DVDs succeeds, only images seem to have an issue

Edit: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265)

---

### Post by KingTermite on 2008-07-06
> **akudewan said:**
> IMO, it may be some kind of bug with k3b. I'm facing the same problem when burning ISO images.

I burned an Ubuntu iso, k3b said data verification failed. But when I booted the CD and ran "Check CD for defects", it showed that the CD was allright.

Verification with data CDs/DVDs succeeds, only images seem to have an issue

Edit: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265)

Now that you mention it, I think it was always ISO images that I was burning too.

---

### Post by rbmorse on 2008-07-06
If you're burning iso images to disks, would you not expect to have the aggregrate of the individual files on the disc after the burn to generate a different md5sum value than the single .iso?

---

### Post by cariboo on 2008-07-06
This problem has nothing to do with md5sum. It tries to verify the disk after it was written. In Gutsy the verification worked. After the disk was burnt it ejected the disk and them reinserted it automatically and verified whether it as a good burn or not.

K3b in Haedy doe snot do that.

Jim

---

### Post by shirsch on 2008-09-04
> **cariboo907 said:**
> This problem has nothing to do with md5sum. It tries to verify the disk after it was written. In Gutsy the verification worked. After the disk was burnt it ejected the disk and them reinserted it automatically and verified whether it as a good burn or not.

K3b in Haedy doe snot do that.

Jim

I'll second this issue.  K3b is definitely broken in Hardy.  Every time I burn an ISO image, regardless of where it comes from or where it lives in storage, K3b reports a fail.  Using a script I found on the web to run a manual MD5 sum on both iso and dvd, things check fine.

See attached for the script.

Unbelievable that this has neither been acknowledged nor fixed after this many months.

---

### Post by Angelos72 on 2008-09-11
It seems that K3B always fails verification when it checks if an image is correctly written on a disk.

You can see the bug report here 

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265/](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/207265/)

---

### Post by triphazard on 2008-09-11
Just stumbled across this thread...I have nothing of any value to add but am interested as a K3B user with an ISO burning session coming up.

So, I'm just wondering, apart from failing verification for whatever reason, has anyone experienced any problems with the burned CDs/DVDs?  Do the Ubuntu images pass the built in CD verification for example?

---

### Post by sdowney717 on 2008-09-11
yes, it fails verification for me.
And it happens on simple copying of a file onto a dvd+rw
So, use Brasero, it passes verification. Why bother with something that is broken?

---

### Post by Gina on 2008-09-11
It generally works fine for me though I have had the odd time when it's said there was an error when there wasn't.  I'm using Hardy with Gnome desktop.

---

### Post by heyup on 2008-12-18
I used K3b version 1.0.5 to write a data CD. Verification failed/hangs after writing the data to the CD. The written data CD seems OK.

I'm using Ubuntu 8.04 Hardy.

---

### Post by stoian on 2009-01-28
> **avtolle said:**
> Brasero is installed as default under Gnome. I've used it multiple times and not had any problems with it on the verification unless there was a problem with the burn itself, which happened once with a lesser-quality CD-RW I used in a pinch.
you cannot create a CD image with Brasero.
i've used both k3b and Brasero, but today Brasero refused to use 2 perfectly new CD-R dics, it told me they are not writeable. k3b was able to use both of these, but it failed the verification... now i think both programs suck, trying to find a reliable one...

---

### Post by cat2005 on 2009-09-05
I am using Ubuntu 9.04 with k3b.  I get the same problem with image files.  The data burns fine, according to k3b, but fails verification, according to k3b.

Regular data files have no problem.

I wonder if the image file is safe to use?  The md5 match but since it states "written data in track 1 differs. . ." I decided not to trust k3b image burns.

---

### Post by sumeshgupta on 2009-09-05
Is it not better to use CLI tools like wodim or growisofs?
Do they also fail verification?

---

### Post by cat2005 on 2009-09-23
> **cat2005 said:**
> I am using Ubuntu 9.04 with k3b.  I get the same problem with image files.  The data burns fine, according to k3b, but fails verification, according to k3b.

Regular data files have no problem.

I wonder if the image file is safe to use?  The md5 match but since it states "written data in track 1 differs. . ." I decided not to trust k3b image burns.


Exact same problem here.  This is silly.  I had to user Nero in Windows to get a successful iso burn verification.  

Are there any command line tasks that could be used to burn and verify?

---

### Post by An85Zk9tc8rfjV8i on 2009-09-30
Workaround for k3b ISO verify failure

> **cat2005 said:**
> Are there any command line tasks that could be used to burn and verify?
solution based on : [HOWTO: Checking the integrity of a LiveCD or LiveDVD]("http://wiki.sabayonlinux.org/index.php?title=HOWTO:_Checking_the_integrity_of_a_LiveCD_or_LiveDVD")

this example:
```

ubuntu-9.04-desktop-amd64.iso
MD5SUM=cace6ea9dde8dc158174e345aabe3fae
```

in  k3b:
Settings > Configure K3b > Devices
find system device name for your DVD or CD burner ($cd)
for example $cd=/dev/sr0

do
isoinfo -d -i $cd
in terminal :
```
isoinfo -d -i /dev/sr0
```

result is :
```

CD-ROM is in ISO 9660 format
System id: LINUX
Volume id: Ubuntu 9.04 amd64
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993 E.YOUNGDALE (C) 1997-2006 J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT TEAM
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 356716
El Torito VD version 1 found, boot catalog is in sector 145
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found
Eltorito validation header:
    Hid 1
    Arch 0 (x86)
    ID ''
    Key 55 AA
    Eltorito defaultboot header:
        Bootid 88 (bootable)
        Boot media 0 (No Emulation Boot)
        Load segment 0
        Sys type 0
        Nsect 4
        Bootoff 89 137
```

the info we want is:
Logical block size is: $blocksize
2048
Volume size is: $blockcount
356716

do
dd if=$cd bs=$blocksize count=$blockcount conv=notrunc,noerror | md5sum
in terminal :
```
dd if=/dev/sr0 bs=2048 count=356716 conv=notrunc,noerror | md5sum
```

result is :
```

356716+0 records in
356716+0 records out
730554368 bytes (731 MB) copied, 5.73725 s, 127 MB/s
cace6ea9dde8dc158174e345aabe3fae  -
```

---

