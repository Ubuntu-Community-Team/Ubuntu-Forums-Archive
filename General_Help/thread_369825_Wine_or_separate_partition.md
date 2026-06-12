---
title: "Wine or separate partition??"
date: 2007-02-25
forum: General Help
---

### Post by Jphenow on 2007-02-25
So, I clean installed my computer with JUST Kubuntu, if I want to some things like games and stuff like that, would be a horrible resource hog to us wine? in that case what's the easiest way to, in my position, setup a separate windows partition. Although, if it isn't a horrible resource hog I can just use wine, but this computer is very bottom of the line right now, meaning I need all the resources I can squeeze from this if I want to do much.

---

### Post by Mets on 2007-02-25
my knowledge on this subject is limited, but I would imagine that windows consumes more resources than Wine, especially if you are using XP or Vista.  The bigger question is what kind of games do you want to play and will they even work with wine.  

If you are resource strapped, don't use Kubuntu, because KDE takes up a lot more resources than GNOME or Xfce.  Give yourself a big swap space too.  A friend of mine refuses to part with his 5 year old desktop, but he has 2gig of swap and runs Xubuntu and loads most programs just as fast as I do on my relatively new lappy.

---

### Post by Jphenow on 2007-02-25
Swap space?

---

### Post by Mets on 2007-02-25
right, so swap space is a partition on your hard disk that you made during installation of your linux distro that is additional dedicated memory (as in RAM memory, not hard drive storage space).  Windows calls it a "Paging File" and creates "virtual" space (i.e. non-permament) when you boot up.  Linux uses an actual dedicated partition on your hard disk that is permanently set aside to act as additonal memory.  Since it is permanent it is faster.  The more memory you give your PC, the better performance you get, to a point of course.  So if you have hard drive space to spare, increase your swap partition.  On Ubuntu you could use GParted (works awesome).  Not sure what the KDE version is.  A high-end computer doesn't need a lot of swap.  You should have at least 500mb, unless you have like 1.5-2gig of ram, then you probably don't need much, if any.

---

### Post by Jphenow on 2007-02-25
That's AMAZING, I love linux more and more everyday

---

### Post by Mets on 2007-02-25
lol, true true.  How much did you give yourself though?

---

### Post by Jphenow on 2007-02-25
My brother set linux up so I'm really still in a large portion of the learning stage, but I just looked, I guess I only have about 200 mb right now

---

### Post by Mets on 2007-02-25
ok, if you could pass along your system specs that would be helpful.

Also, how big is your total hard drive and how much free space do you have?

---

### Post by Jphenow on 2007-02-25
unless I'm reading wrong, take a look

[I]
Tasks:  92 total,   1 running,  90 sleeping,   0 stopped,   1 zombie
Cpu(s):  9.9%us,  2.3%sy,  0.0%ni, 80.2%id,  0.0%wa,  0.0%hi,  7.6%si,  0.0%st
Mem:    255788k total,   249860k used,     5928k free,     3332k buffers
Swap:   746980k total,    20156k used,   726824k free,    69800k cached
[/I]

---

### Post by Mets on 2007-02-25
ok, what is your processor speed (ex. P4 2 Ghz)
what is your system RAM (ex 1 gig)
how big is your hard drive (ex. 30 gigs)
how much free space (ex. 5 gig)

---

### Post by Jphenow on 2007-02-25
Okay for HD size, I looked in my home folder properties, sayin only bout 55GB but I know for sure it was much bigger, I dont know where it could be hiding haha, also I have a 160gb external

---

### Post by Jphenow on 2007-02-25
processor is about a 2.4 ghz pent 4
RAM is 256mb but I recently ordered another 256, get that next couple days
As I said our HD says 55gb with 44 free at the moment,
but I know we had another internal HD and I have the external

---

### Post by Mets on 2007-02-25
Cool, so you definitely need more RAM.  Your total system ram is 1 Gig (250 MB from the chip, 750MB swap).  You'll be at 1.25 gig with your additional chip.  That's really pretty good.  I would probably give myself 1.5 gig of swap given how much free space you have for best performance.

Also, you have plenty of space to make a windows partition.  If you are new to linux you have two options.  You can install a windows partition to play your games and use programs that aren't linux friendly, or you can install wine and try to get your windows programs running.  Wine can be a pain to setup, and getting programs to run under it can be a further pain.  I'm working on it  at the moment myself.  It really depends on what you feel like doing.

Also, get Automatix - it will help you install basic programs and get your computer nice and functional with not to much effort.  [www.getautomatix.com](www.getautomatix.com) - however the site is down atm due to a snow storm.

---

### Post by Jphenow on 2007-02-25
HAHA I live in minnesota, I'm smack dab in that storm, took me half hour to get like 5 miles cause i got stuck.

So yea I'll look up that first program you mentioned and attempt to throw on some more swap memory.

On the wine aspect, I'm not worried bout setup because well... the broski already set it up because he knew I'd wanna do some windows stuff, so now i just need to figure it out!

Ones last question, what's the easiest way to get GNOME, and once you have it is it easy to switch between? and lastly i already have beryl running if that means anything

---

### Post by Mets on 2007-02-25
Seems like you have the works going :)

GNOME is just another windows manager like KDE.  You could download GNOME and then you get to choose what windows manager you want at startup, but you don't need it for this one program.  I'm not 100% sure how to do the joint GNOME/KDE thing, and what affect beryl has on it.  However, if you just want to get GParted, then type "sudo aptitude install gparted" in the terminal without the quotes.

---

### Post by Jphenow on 2007-02-25
Yea the only reason i was wondering about getting the GNOME manager is be cause you said, as my brother has, that GNOME uses less resources than KDE, I actually prefer KDE over GNOME and Beryl kicks everyone's *** so that's that. I would essentially use the GNOME for when I needed all the resources

And thanks A lot for all the help and suggestions!

---

### Post by Jphenow on 2007-02-25
Once I install gparted where do I find it in order to use it?

---

### Post by Jphenow on 2007-02-25
since this is partition editor, how do i actually make a separate partition into memory?

I have too many questions

---

### Post by Patrick K on 2007-02-25
Let's throw a bit more confusion into this. **There is another option**; VMware Server (Google it). This sets up a virtual machine inside your Ubuntu OS. Inside this virtual machine you can install Windows. It will, provided everything goes right, run Windows just like a regular install except it is running inside Linux. No need for reformatting or dual booting. Just run Windows like any other application. Games will never know they are running in Linux. 

I've been looking at this option myself but haven't made the move, yet, so I can't really provide anymore info.

---

### Post by Mets on 2007-02-25
ok, not sure where it would end up under KDE, but just type "gparted" in the Konsole and it should start up.  From there, it's pretty straightforward doing the partitioning.  Just follow the on screen instructions, and use the tool to decrease the size of your main hard drive partition the amount you want to increase the swap partition size by.  Then do one of two things.  Either delete swap partition and make a new one of the total size you want, or try to resize existing swap.  It's probably easier to delete swap, reduce size of primary hard drive, and make a new swap.

I haven't looked into VMWare since I dual boot, and I'm not sure about things like audio, but it would be pretty cool.  You do have to buy it though, which kind of stinks.  Is Qemu good enough Patrick?

---

### Post by Patrick K on 2007-02-25
> I haven't looked into VMWare since I dual boot, and I'm not sure about things like audio, but it would be pretty cool. You do have to buy it though, which kind of stinks. Is Qemu good enough Patrick?
Reply With Quote 

VMServer is free. As is VMConverter, which converts an existing Windows (or other supported OS) install into a package to install in VMServer. I've not looked into QEMU. If/when I go this route, I have to make sure it supports W98, which VMServer does. Several others do not. I don't have XP or Vista and do not plan on buying them. 

From what I understand, if your Linux install has sound the OS running in the VM will have sound. The guest OS inherits all the hardware capabilities of the host OS.

---

### Post by Mets on 2007-02-25
oh sweet, I may have to do that.  I could get rid of my windows partition and dual booting.  Have to check out performance though.  Thanks for the tip.

---

