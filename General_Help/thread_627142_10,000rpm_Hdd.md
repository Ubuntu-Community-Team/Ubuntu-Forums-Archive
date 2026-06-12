---
title: "10,000rpm Hdd"
date: 2007-11-29
forum: General Help
---

### Post by skymera on 2007-11-29
im thinking of buying a Rpator 10,000RPM drive.

mainly i want to know what will the benefit be of installing ubuntu on it with a JFS file system?

or even a EXT3 fielsystem?

thanks.
__________________

---

### Post by fjgaude on 2007-11-29
You notice somewhat faster throughput, read times, with that drive. I have four of them but for general work there are not worth the extra money. You will not see any real speed improvement due to the filesystem you use, IMHO.

---

### Post by skymera on 2007-11-29
its mainly for my games for Windoze.

but hoping i shall get faster bootimes for ubuntu

---

### Post by PmDematagoda on 2007-11-29
If you want a file system that is faster than JFS or Ext3 then you could have a look at [XFS]("http://en.wikipedia.org/wiki/XFS") or [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS").

---

### Post by fjgaude on 2007-11-29
All I can say these drives are not worth the money except in a business environment where money is not a primary issue.

The latest perpendicular read head drives are fast and you will need more than the PCI bus to get at their true throughputs. You need PCI-X or PCI-Express bus controllers to get over about 110 MB/sec throughput.

Your slow boot times with Ubuntu is likely another issue. Do a search for slow boot and you will find many posts on such. Luckily I don't have that problem.

---

### Post by PmDematagoda on 2007-11-29
Hey skymera this is just a question, what Windows games are you running on Ubuntu and how?

---

### Post by atlfalcons866 on 2007-11-29
JFS is the fastest file system. According to this [http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

JFS is recommened for mythtv. But jfs is very prone to fragmentation

---

### Post by skymera on 2007-11-29
> **PmDematagoda said:**
> Hey skymera this is just a question, what Windows games are you running on Ubuntu and how?

im running windows games on...windows believe it or not :lol:

---

### Post by PmDematagoda on 2007-11-29
:-k, so, you are using the new drive for Windows?

[-X, such a waste:D.

---

### Post by skymera on 2007-11-29
not al,l 50GB ubuntu
100GB..uhh NTFS for games.

im pretty sure my games will load faster, possible 30%+
and rpretty sure buntu will load quicker,

im torn betwwen standard and raptor. hmmm, i got a month to think anywhoo

---

### Post by PmDematagoda on 2007-11-29
Personally I would go for the raptor but what fjgaude said does make me think.

---

### Post by skymera on 2007-11-29
well when i get a new pc i most likely get a 300-500gb hd with it...soo im raptoring. :)

and gonna stick to what i know, the EXT3 FS :D

---

### Post by atlfalcons866 on 2007-11-29
ext3 fsck will take forever on a 500GB hdd.

Is the raptor your talking about the one with clear case window?

---

### Post by PmDematagoda on 2007-11-29
> **atlfalcons866 said:**
> ext3 fsck will take forever on a 500GB hdd.


No it won't, fsck takes only about 10-20 minutes for my 200Gb HDD which incidentally is not a raptor but is a SATA, so it may take only about 40 minutes on skymera's new PC......... ok that is a long time, I think you better reconsider what FS you are going to use skymera:D.

> Is the raptor your talking about the one with clear case window?

My goodness the way they are making HDD's look like these days you might think they were diamonds:D.

---

### Post by skymera on 2007-11-30
i decided gonna stick to the Raptor :)

50GB ubuntu 
100GB NTFS :)

---

### Post by anaconda on 2007-11-30
I wonder why no-one mentioned the noice..

with more rpm:s you will also get louder noice from the hd.

I prefer silent hd:s..

---

### Post by atlfalcons866 on 2007-11-30
> **anaconda said:**
> I wonder why no-one mentioned the noice..

with more rpm:s you will also get louder noice from the hd.

I prefer silent hd:s..

not always
my 7200 rpm 160Gb sata driver is louder than my 120GB 5400 RPM pata drive. They are both 3.5 inch disks

---

### Post by skymera on 2007-11-30
> **anaconda said:**
> I wonder why no-one mentioned the noice..

with more rpm:s you will also get louder noice from the hd.

I prefer silent hd:s..

i dont care about the sound :P

i have a loud GPU fan, a loud PSU fan so it can join the crowd :)

---

### Post by PmDematagoda on 2007-11-30
Join the club, my processor fan and the 2 cooling fans it has makes so much noise, it can even awake the dead:D.

---

### Post by IeU on 2007-12-11
so how was the performance gains ?

---

### Post by Lostincyberspace on 2007-12-11
I have 4 fans 3 hard drives, pretty old ones too, and they are all quiet as whistle.

---

### Post by IeU on 2007-12-14
not sure how reliable this test is, but . . .

```
[root@minwinpc home]# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1378 MB in  2.00 seconds = 689.46 MB/sec
 Timing buffered disk reads:  162 MB in  3.00 seconds =  53.92 MB/sec
[root@minwinpc home]# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1376 MB in  2.00 seconds = 688.37 MB/sec
 Timing buffered disk reads:  246 MB in  3.02 seconds =  81.55 MB/sec

```

sda -> Old 160Gb Seagete 7.2k rpm ( linux is here )
sdb -> XRaptor 150Gb 10k rpm ( windows / ntfs )

---

### Post by skymera on 2007-12-14
well its testing on different filesystems,

so not really reliable imo.

---

