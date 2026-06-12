---
title: "Please help me. Im in big trouble"
date: 2007-05-26
forum: General Help
---

### Post by Prisma on 2007-05-26
I downloaded and installed ubuntu 7.04 using the wubi installer.

I have 2 partitions with windows XP. For some reason i was playing with ubuntu and trying to install guild wars with cross over when my PC freezed. I restarted it and but now it said that a file is missing:

Windows root\ system 32\ hal.dll

I can restart my other XP partition, the one where i installed Ubuntu with wubi. But my main XP partition with my whole documents is now unreachable, i cant see anything inside everything is blank. However, the documents still there since there are only 11 GB free, so my files are there is just that i cant see them. 

Instead there is a 1 folder with this name:

2dd12d3e133e8fc6ef67651d1190


Please help me guys, im really in trouble, i thougth this wubi was a completily safe way to try ubuntu, it said that in its reviews. Help me at least to recover my precious pictures, the rest i dont care. 

God bless you for your help

---

### Post by Prisma on 2007-05-26
Please anybody.... please help me

---

### Post by Prisma on 2007-05-26
i just want to know how can i access the hard drive again so i can make copies of my files, please guys help me.

---

### Post by hasimir44 on 2007-05-26
do you have a 2 cd/dvd trays - one of which can burn? or do you have a thumb drive? if so, then just boot the ubuntu live cd and burn the pictures to a cd or copy them to your thumb drive.  if not, then it's a little trickier.. 

the live cd should auto mount your xp partitions and since it doesn't depend on the missing dll file, it should be able to read them both fine (writing is a different story though..). 

if it doesn't auto mount the partitions, then run this command from the live cd and post the output: 

```
cat /etc/fstab
```

we'll help as much as we can.. good luck

---

### Post by Prisma on 2007-05-26
Thank you for your reply.

Why i cant see anything on XP? why those numbers in the folder? is my whole drive's info encrypted somehow and i cant just burn it on XP? because Im on my other partition now.

---

### Post by syntaxerror64 on 2007-05-26
First off, relax...   don't get impatient and do something that might destroy your data.  It's all likely still there, it appears something has just happened to the XP install that is causing it to hang on startup.

If I were you, I'd just boot into XP and then attempt to go into safe mode.  See if you can get into XP that way, and then verify that all your data is intact.  If you can't get XP going in safe mode, do as the other post suggested and boot with your Ubuntu Live CD and take a look at the partitions in there.

Another important lesson here is if you have data that you can't afford to lose you should be making 2 and 3 levels of backups on a regular basis.  You never know when disaster will strike.  If this is data that you just cannot lose, you might just want to shut the computer off and hire someone to come over to your house who knows what they are doing.

In any event, good luck!

---

### Post by Prisma on 2007-05-26
Is my other XP partition broken? ifis a windows partition why i cant see anything?

---

### Post by Prisma on 2007-05-26
Hey thank you for the reply. I will try to calm down as you suggested and find a solution to this mess. Its just that i dont understand why i cant see my data if is there and is a windows partition.

---

### Post by aidanr on 2007-05-26
sounds like the filesystem got corrupted

boot up your xp install disk, go into recovery console and run chkdsk /r

---

### Post by Prisma on 2007-05-26
aidanr, that command can repair the file system?

---

### Post by aidanr on 2007-05-26
yes, see [here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true")

---

### Post by SonicSteve on 2007-05-26
Hi Prisma,
Check this one out. I think that you most likely will need to do a repair install. 
[http://www.computerhope.com/issues/ch000490.htm](http://www.computerhope.com/issues/ch000490.htm)

Be careful though, this gets more complicated with a dual/triple boot system. You have grub to worry about now, not just XP boot files.
you probably don't but....if you need a boot disk try [www.bootdisk.com](www.bootdisk.com)
if you can access the partition then perhaps this will help [http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)
edit for future reference; 
this site has very useful info
[http://www.hardwareanalysis.com/content/topic/14666/](http://www.hardwareanalysis.com/content/topic/14666/)

---

### Post by Prisma on 2007-05-26
Its fixed!!!!!!!!   :p

Guys you are geniuses I repaired my windows XP partition with recovery console and chkdsk /r like you suggested my file system was indeed corrupted by this Ubuntu Wubi installer.  Everything is back to normal now and my precious wedding pictures are safe. I will burn lots of DVD to backup my data.  I learned this lesson in a hard way. I am impress with Ubuntu i will switch as soon as i can backup and secure all my data to make a clean install. However, i will keep an small XP partition just in case something like this happen again. 


Guys I owe you a lot   :popcorn:

Thanks again and God bless   :KS

---

### Post by Prisma on 2007-05-26
Hey thanks Steve for those links. They are really nice info to know and for future issues. Thankfully i didn't mess the grub or anything else on my PC LOL. I'm just so thankful that people like you guys are always around in this forums to help dumb people like me. :D 

Thanks again Aidanr. :p

---

### Post by aidanr on 2007-05-27
no problem, just a couple of things for reference though

while the wubi installer is easy and great for newbies, it is still running on your ntfs xp partition, so a bad crash can corrupt that partition, it would be better to use the default install method

when your playing around with emulation (wine, crossover etc) the chances of a crash are much higher, and if your pc does freeze don't just hit reset, you can still safely reboot with a few keystrokes, see [here]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by carusoswi on 2007-05-27
> **aidanr said:**
> no problem, just a couple of things for reference though

while the wubi installer is easy and great for newbies, it is still running on your ntfs xp partition, so a bad crash can corrupt that partition, it would be better to use the default install method

when your playing around with emulation (wine, crossover etc) the chances of a crash are much higher, and if your pc does freeze don't just hit reset, you can still safely reboot with a few keystrokes, see [here]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

Golly, what a great tip.  Absent your having posted the link, is there some other source I should be reading to see all this stuff?  I am new to ubuntu, but have tried to read all that I can get my hands on - never came across anything like your post - I am certain there are other tricks I of which I should be aware.

Thanks for sharing that great tip.

Caruso

---

