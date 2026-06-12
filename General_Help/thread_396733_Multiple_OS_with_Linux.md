---
title: "Multiple OS with Linux"
date: 2007-03-29
forum: General Help
---

### Post by KAL9000 on 2007-03-29
Ive not had much experiance with VMware but there is one very interesting thing I've thaught to  do with it. 

That is to make Ubuntu or whatever distro of linux my main OS and then use VMware to boot XP/NT/98/85/3.1/dos and/or other distros of Linux.

1, what is the proformance loss due to the emulation?
2, Does running VMware stop XP getting mardy when you change hardware.
3, Can you boot several at once (if your machene could manage it)
4, What compatability problems are there. I.E. does an operating system in VM work exactley as it would normaly or is it abit like Wine where things like .net dont work properly...

Sorry for the barage of questions but there is one last. and it could be the most important.

If the host OS goes belly up can ANY host running a simmaler version of VM boot the disk/partitions in VM and run them as if nothing had happend?

The reason for me thinking this is when i tried to run C&C on XP it realy doesnt like it. but if i could run windows 95 in VM then I could play the game through that.
Using that idea and think alittle to scale it up...would it work? 
The idea being that once that is done the OS's will ONLY ever be run thruough VM. unless neccesary.

---

### Post by zorkerz on 2007-03-29
Personally I have never used VMware so i have no first hand experience. 
My understanding is the performance loss can be pretty heavy as you are essentially running to operating systems at once. read this from /. today [http://slashdot.org/articles/07/03/29/1219218.shtml](http://slashdot.org/articles/07/03/29/1219218.shtml)

I do not believe they operate exactly the same my understanding is that vmware is not perfect yet.

You should check out the wine project [wineHQ.com]("http://winehq.com/") This has the ability to run many windows programs natively in linux. It is by no means perfect prolly more programs don't work than do but depending on which c&c you want i think there is a decient chance you could play it that way. Personaly i dual boot into windows for games. Actually it has helped me cut back alot by needing to restart to play a game.
theres my knowledge
cheers

---

### Post by KAL9000 on 2007-03-30
The problem is that C&C (the origonal one) doesn't work under XP even with compatability mode running. 
Plus I have a friend who is also interested in Linux but uses XP and 2K and this would be interesting for him. 
I know it would take a hit due to 2 OS's running at once but one would be Linux, Idealy a very thin client at that. And also my assumption would be that several OS's could be added and taken away without any MBR alterations or endless hours sorting GURB out. 

Yet annother reson whould be it "Could" and this is why I ask, "Could" sort out MSDos relient OS's even when running on 64bit systems? by translating the 16bit opperations and emulating them to the 64bit CPU 
(For those that dont know. 64Bit systems dont have ANY native or embedded 16bit support)
So I hope maybe VMware can iron out any of those considerations. 

I don't know maybe im asking too much. Maybe im defining what VMware should in a perfect worl be and now what it acctualy is. 
I will take a look at that link anyway and see what I can gather :)

---

### Post by Jose Catre-Vandis on 2007-03-30
If you are happy to accept the reduced operation of the emulated hardware, accept VMs won't run your graphics card etc, then Vmware is a good way of having a look at other OS's without having to install on your hard drive.

Yes, if the host OS goes down, and assuming your vmware files are not affected, they should load up find in anotherhost with an install of Vmware, because "it's all the same hardware!".

I run vmware server for quick access to XP, but have multiple partitions on my hard drive for proper installs of many distros at once, just on occasion means resetting grub (e.g. Ubuntu Live CDs automatically overwrite mbr with their grub on install

---

### Post by anaconda on 2007-03-30
> **Jose Catre-Vandis said:**
> Yes, if the host OS goes down, and assuming your vmware files are not affected, they should load up find in anotherhost with an install of Vmware, because "it's all the same hardware!".

I have understood that the virtual machine sees the processor of your machine. So if you change the machine windows will notice that your processor has changed. However my windows (in VMWare) has never needed reactivation when I have changed components or the whole machine..

I haven't noticed that big differences in speeds of the virtual machines compared to real installations. The only thing is that anything with fast graphics wont work in vmware.

---

