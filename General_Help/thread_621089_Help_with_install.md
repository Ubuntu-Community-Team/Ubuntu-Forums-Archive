---
title: "Help with install"
date: 2007-11-23
forum: General Help
---

### Post by fiddilydee on 2007-11-23
Alright I have already posted this problem a couple times but I think I put too much information because everybody who replied did not understand the problem.

I installed ubuntu (first time xtreme noob) after booting into it from the cd. I have one Hard drive 230 gb. I decided to partition into 60 for my os and the rest for media. I currently have all my media on the seperate partition. I installed it on the small partition and the installation created a couple of small locked partitions (I assume these are needed to run ubuntu). 

After install I reboot and the username/password does not work. I check on the forums for ways around this. Everything I do to try to change it results in username not found, so after much screwing around I decide to reinstall it.

It will not reinstall properly because of these extra locked partitions. During installation it says that these partitions are full and cannot be written to. 

When the reinstall finishes it still will not allow me to login and it is still going off the user info created from the first install.

Here is what I need to do, and what I need help with. I want to format these extra partitions without losing my media partition so I can try a fresh install but I can't because these partitions are locked. I can still run Ubuntu from the cd to do this stuff.

Failing this I could copy my media onto my extrenal HD but Ubuntu cannot mount it. I don't even know what this means. I was able to use the External HD in Ubuntu before I actually installed it but now it won't work.

So if anyone can explain to me (A linux Noob) how to format these locked partitions while maintaining my media partition or how to mount this stupid HD, I would be extremely greatful... I don't want windows back but I'm running out of options.

---

### Post by TNakos on 2007-11-23
when you pop in the live CD or ALT... It should just give you a option to Format.... I dont know if i understand your question.

---

### Post by fiddilydee on 2007-11-23
I dont think it gives me an option to format, but if it does will it allow me to format the locked partitions? When I try to do this from ubuntu it will not work.

---

### Post by banewman on 2007-11-23
Pull out the internet connection cable so there's no connection during install is my first tip.
(makes the install longer with the updates)
From the live cd use gparted manual partitioning to remove all partitions except your media one.
Create one partition that is 10 gig and mount that as root and as ext3.
Create one partition that is 1 gig and mount it as swap - swap has it's own file system.
Create one partition from the rest of the free space and mount it as /home.
That should get you past this prob hopefully. :)

---

### Post by hellion0 on 2007-11-23
At least on the Edgy and Feisty Live and Alternate CDs (I'm assuming this is still the case with Gutsy), when you get to the point where you want to partition your drive, instead of doing so in a guided manner, do so manually. It's not as hard as it seems.

While in that menu, you should be able to nuke those small locked partitions and remake your OS partition (if necessary). I'd still back up first, you may need to ditch the media partition as well and start completely from scratch.

---

### Post by fiddilydee on 2007-11-23
Im am using Gparted, (i think, that is included with ubuntu, right?) but it wont let me format those other partitions.

---

### Post by hellion0 on 2007-11-23
Weird. If you're running gparted from the CD, it should be able to partition anything.

---

### Post by fiddilydee on 2007-11-23
If i ditch my media partition I have to get the data onto the external usb. And It will not mount, I don't even really understand this.

---

### Post by banewman on 2007-11-23
Are you on the live cd now?
If you are open a terminal and type -        fdisk -l
and post the output here please. :)

---

### Post by fiddilydee on 2007-11-23
Im at work right now So i'm just kind of gathering information and planning my attack for when I get home. I'm off in 6 hours so I can tell you then at the latest.

---

### Post by fiddilydee on 2007-11-23
b b b bump

---

### Post by banewman on 2007-11-23
Can't help more  without more info
> Im at work right now So i'm just kind of gathering information and planning my attack for when I get home. I'm off in 6 hours so I can tell you then at the latest.
:)
Shouldn't that be at the earliest?

---

### Post by fiddilydee on 2007-11-23
Astute point, but I did not mention that my going home at lunch is an option. Although I don't think I'll bother. It can wait until after. I was just trying to amass as much as i could so when I got home I would have a couple things to try. I have been messing with this for 3 or 4 days.

---

### Post by fiddilydee on 2007-11-23
> **banewman said:**
> Pull out the internet connection cable so there's no connection during install is my first tip.
(makes the install longer with the updates)
From the live cd use gparted manual partitioning to remove all partitions except your media one.
Create one partition that is 10 gig and mount that as root and as ext3.
Create one partition that is 1 gig and mount it as swap - swap has it's own file system.
Create one partition from the rest of the free space and mount it as /home.
That should get you past this prob hopefully. :)

What do you use as a mount point for /home?

---

