---
title: "Getting the best from a partition"
date: 2007-02-20
forum: General Help
---

### Post by andy_cowman on 2007-02-20
Hiya

I have been fully using Ubuntu for a couple of years now, I have also switched my parents to it aswell and for the last 6 months there has not been a problem.

There isn't a problem now either but I am after some advice. My father is into digital photography and is fairly well set up (canon 20D, i9950 printer etc) and it all works fine in linux and he is happy. He shoots in a mix of RAW and JPEG and is not great with computers regardless of the OS. everything has to be as simple as possible for him and it pretty much is! 

He likes Picassa and uses it to look, print and put photos on the web (for those interested its the latest web albums 2.6 running under Wine installed on Edgy through automatix. It works pretty well). Sometimes it gets a bit a sluggish though. Its still very usable though just a slight annoyance. The photos are all quite large and there are lots aand lots of them stored on a 55gb fat32 partition. This partition has been accessed by windows and linux for a year or so and I think it is noticably slower now than before. In picasa this becomes noticable when you scroll down through all the photos. It stutters slightly. I plugged the drive into a windows box and it said to defrag it but there wasnt enough free space then to do it. I have since backed all the photos up to DVDs and cleaned out some old films that were cluttering up.

Anyway to my question, I am in a postion to reformat this partition and I am thinking of using Ext 3 on it. This should perform better than fat32 (which was massively fragmented)? What do people think?

 Any other ideas on improving performance? Its only a celeron 2.6ghz, 1gb ram, Nvidia 6200 gfx card but when bought all the parts were of reasonable quality. To improve picasa so far I have set wine to run it as an XP prog and turned it to emulation (not hardware) direct 3d graphics. All the useless gimmicks in picasa are off aswell?

Thanks

Andy

---

### Post by chggr on 2007-02-21
> **andy_cowman said:**
> 
Anyway to my question, I am in a postion to reformat this partition and I am thinking of using Ext 3 on it. This should perform better than fat32 (which was massively fragmented)? What do people think?


It's a fact that ext3 is a better filesystem than FAT32.
I think that FAT32 is used in most USB sticks. Here's what happened to me once: I own a 1GB Usb stick and two weeks ago I wanted to copy a large number of files (>1024) on it. I got an error message saying that in a FAT32 folder, only up to 1024 files are allowed!!!

---

### Post by Ramses de Norre on 2007-02-21
ext3 will certainly perform better, it can be used in windows too with an app like [this](http://www.fs-driver.org/).

---

### Post by Olav on 2007-02-21
> **chggr said:**
> It's a fact that ext3 is a better filesystem than FAT32.
No question about that.

> I think that FAT32 is used in most USB sticks. Here's what happened to me once: I own a 1GB Usb stick and two weeks ago I wanted to copy a large number of files (>1024) on it. I got an error message saying that in a FAT32 folder, only up to 1024 files are allowed!!!
I believe that is only true for the root folder of a FAT32 file system. If you make a new folder and copy your files there, it should work. Silly, I know...

---

### Post by Olav on 2007-02-21
> **Ramses de Norre said:**
> ext3 will certainly perform better, it can be used in windows too with an app like [this](http://www.fs-driver.org/).
I am using that driver on a friend's Windows computer to be able to use the external USB harddisk I have. Which I formatted as EXT3, of course :cool:

Anyway, works perfectly. Very easy way to transfer large amounts of data between computers.

---

### Post by chggr on 2007-02-21
> **Olav said:**
> 
I believe that is only true for the root folder of a FAT32 file system. If you make a new folder and copy your files there, it should work. Silly, I know...

That's what I finally did!! ;)

---

### Post by andy_cowman on 2007-02-22
Thanks for the replies everyone, I have formatted the partition in EXT3 and it does seem quicker in Picasa to scan through. Still a bit slower with RAWs but I am just impressed that Google bothered to support RAWs since there is no standard format for them! Plus they are really quite large files!

Looking forward to more increased performance now!! Think I may well make my external USB drive EXT3 now and just keep the windows drivers on a small memory card so that if i do use it on someone elses machine with windows I can just install them

Thanks guys!

And

---

### Post by alenis on 2007-11-12
Hello Andy, you say that you have a Canon i9950 perfectly working under Ubuntu. I have the same printer and I can't use it with Ubuntu so I wonder how you did it. 
Thank you
Alessandro

---

