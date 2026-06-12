---
title: "GParted Help [Resolved]"
date: 2006-12-31
forum: General Help
---

### Post by fredster001 on 2006-12-31
Hi,

I installed ubuntu successfully the other day, and now i like it i wanted to increase the partition of the hard drive for it.

So i downloaded and installed gparted. Once i had done that, i successfully made the windows partition smaller. This left an "unallocated" space which i wanted to merge the ubuntu partition with, however i cant.

The screenshot attached shows the screen i get, there is a padlock next to that partition.
(and yes i know i only have a 20 gig hard drive!!!)

How do i go about making the hard drive space for linux bigger??

Thanks

fredster001

---

### Post by bigken on 2006-12-31
ytou need to download and burn gparted liveCD boot from it and then resize you cant resize a mounted drive ;)

---

### Post by fredster001 on 2006-12-31
ah, ok. Thought that might be why, but wasnt sure.

Thanks

---

### Post by petteriIII on 2006-12-31
Second option is to use that CD you installed Ubuntu from. It has also gparted. Access to it is:
System/Administration/GnomePartitionEditor

---

### Post by fredster001 on 2006-12-31
hi again, 

i ran ubuntu from the live cd again, so i could attempt to change the size of the partition for linux. However it wouldnt let me. 

I havent got a screen shot, but it's the same screen as the first one, except there are no padlocks.

It doesnt seem to want me to drag the ext3 partition to merge with the unallocated one.

Is there a way i can do this, or a way i can merge the two without removing the whole thing and starting from scratch.

Thanks

---

### Post by bigken on 2006-12-31
like i said in my 1st reply download gparted liveCD ](*,)

---

### Post by fredster001 on 2006-12-31
is that really necessary though? I can use Gparted and change the size of the partition, as it is on the Ubuntu live CD. 

However i cannot make it any larger, or make it 'merge' with the un allocated partition.

I dont see how burning the cd for Gparted will help if i already have it on another cd...

thanks

---

### Post by bigken on 2006-12-31
because you dont have any rights to change the partition I would imagine
where as in the live cd you have full rights ;)

its a 2 minute download

---

### Post by smoker on 2006-12-31
in gparted you can only resize a drive to take up unallocated space behind it. there are a few ways around this, probably the easiest would be to, though i am not sure how the naming of partitions and the grub boot list would be affected, maybe someone can comment on that.

you could, create a new partition (ext3) in the unallocated space,
resize you ubuntu partition to the same size as the new partition.
copy your ubuntu partition to your new partition.
then delete your original partition which will be behind the new ubuntu partitoin.
then you should be able to resize your new ubuntu partition to take up all the new unallocated space behind it.

if you don't want to do this, there are other repartition programmes available, or maybe someone could suggest a better way to do this

---

### Post by fredster001 on 2007-01-01
Thanks guys,

The problems solved. I burned the gparted the live cd and ran it.
You were right, there are more functions on the gparted cd than on the ubuntu live CD.

Its all good

Thanks guys

---

### Post by g0pbe on 2007-01-03
Hi

I have exactly the same problem so was really glad to see that I wasn't on my own. Unfortunately, I have not been able to solve the situation as the CD I created from the downloaded file will not boot.

Can you list the extracted files that you have on your CD so I can check they are the same.

When I put the Live CD in and boot up, the system ignores it completely and carries on loading as normal.

I have used Ubunto 5.10 Live to check and that works fine

Your help / comments would be appreciated

g0pbe:

---

### Post by bigken on 2007-01-03
> **g0pbe said:**
> Hi

I have exactly the same problem so was really glad to see that I wasn't on my own. Unfortunately, I have not been able to solve the situation as the CD I created from the downloaded file will not boot.

Can you list the extracted files that you have on your CD so I can check they are the same.

When I put the Live CD in and boot up, the system ignores it completely and carries on loading as normal.

I have used Ubunto 5.10 Live to check and that works fine

Your help / comments would be appreciated

g0pbe:

Download the gparted liveCD ISO from my signature

---

### Post by g0pbe on 2007-01-03
That's what I did - when I extracted the file, it made a folder with 7 files but there was a file that would not extract and it left it on it's own - sorry for not being too accurate but I am writing from work and this happened on my Laptop at home. I think the folder was called Isotonic - or something like but i cannot remember the name of the file that was left. That's why I would like to know exactly what files should appear so I can check.

I hope the fact that I burned a R/W CD and not a R only isn't the cause of the problem

G0pbe

---

### Post by bigken on 2007-01-03
you dont extract it you burn it as an iso if your using windows use the windows iso burner its in my signature if your using ubuntu to burn it just right click and select burn to disc ;)

---

### Post by fredster001 on 2007-01-03
yeah, burn it as an iso, leave it in the drive.
When your computer starts you need to select the boot selection drive menu, (normally by pushing f2 or f12). The first screen your computer shows at startup shows this. 

Select the CD drive with the disk in and your away.

---

### Post by g0pbe on 2007-01-03
Things are becoming clearer - the Ubuntu mist is clearing. I will let you know how I get on - fingers crossed

---

### Post by g0pbe on 2007-01-04
Hi all

Pleased to say that my problem is now solved. It worked like a dream. 

My own stupidity I suppose but initially I didn't know that I was not supposed to extract an ISO file. That is what caused me the problem earlier in the week. All part of the learning curve I guess.

Having got Cinerella - Video editing, working on my system, I am very close to getting rid of Windows once and for all. Would it be as simple as reformatting the Windows partition using GParted Live and extending the Linux partition??

Am I likely to come across any hiccups upon boot up??

Anyway, I am extremely grateful to everybody for help and comments

g0pbe

---

### Post by bigken on 2007-01-04
no it should be ok ;)

---

