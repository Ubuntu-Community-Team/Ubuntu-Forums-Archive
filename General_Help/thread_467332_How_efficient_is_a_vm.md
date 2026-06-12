---
title: "How efficient is a vm?"
date: 2007-06-07
forum: General Help
---

### Post by Znupi on 2007-06-07
I'm thinking of "redesigning" my PC. Right now I dual-boot with XP. The thing is, I use XP very rare.

**What I want to do:** Reinstall everything. XP is full of viruses and adware, and it's way too slow than when I first installed it. On Ubuntu, I installed tons of software, removed it, I have halfway-compiled stuff, etc. This is due to the fact that it's my first Ubuntu installation, and I had to go through lots of software to see what I like.

**The question:** I would like to delete Windows' partition, and make a bigger one for Linux. After that, I'd like to use a virtual machine to run XP in Ubuntu. This I need to do mainly for [Paint.NET](http://getpaint.net), maybe UltraEdit-32 (although it works wined) and... **Games** ( <- important ).
. Would a vm work for this?
. Is it fast enough to play games on it?
. I have no knowledge about how a vm works, will I be able to install it? (I have a bit of experience with Ubuntu and I can use the command line)
. Do I still need to create a partition for Windows? Or will it install on the existing ext3 partition Linux is installed on?
. Will Windows be able to read ext3 if it's being run in the vm?

Last, but not least, what vm should I use? I've read somewhere that VirtualBox is the most user-friendly and easy-to-use. Is that right?

Thanks in advance :)

---

### Post by borahshadow on 2007-06-07
ok well
#1 probably
#2 depends on the game anything 3D and you're into trouble any FPS etc probably forget about it (also depends on your computer hardware mainly amount of ram) 3D is doable in some vm solutions (Vmware workstation and some have it working in vmware server too (I did but too slow to play most games)
#3 I don't know about virtual box I use vmware server but it is relly simple if you can install windows on a normal computer you can install it on a vm
#4 No the vm make a file (files) that is a VIRTUAL harddisk (you can have it split it into 2GB files)
#5 Windows will not see your ubuntu partition it will see VIRTUAL hardware as far as it is concerned it is running on it's own computer with its own mobo own ram own harddrive etc. 
You can share folders with samba and map them on your VM though that is what I do so I keep all my files on my linux and access them on my vm through samba
hope I helped

---

### Post by Hendrixski on 2007-06-07
Virtual machines are great!  I recommend VMware.  It's VERY easy to install in Ubuntu just click on applications-->Add/Remove and select VMWare Player.

you can then run windows inside of Linux.  You can take a "snapshot" of it so that if it gets a virus you just use the last uninfected snapshot... and this will never infect your Ubuntu box.

you can play games, and install any Windows program you'd like on it.  You canplay games... not really high-graphics intense games... but that's no big loss.

Depending on how old your computer is it may or may not slow down a noticeable amount.

---

### Post by Hendrixski on 2007-06-07
Oh... oopps forgot to answer the partitioning thing... Nope.  no need for a partition.  Just install ubuntu... then you can install any number of virtual machines without having to worry about partitioning or any of that crap.

You can try other operating systems on the virtual machine as well... like Solaris UNIX  :-) it's nnnnnniiiiiiiiiiiiiiiiiccccccceeeeeeeee

---

### Post by Znupi on 2007-06-07
Hmm... I was hoping I would be able to play high-res games (Like NFS Carbon, GTA San Andreas, etc)... (btw my PC spects are in my sig).

Here comes another question: if I make another dual-booting installation, is there any way to make a virtual machine that boots the windows partition? So I don't have to install it twice, once on the harddisk and once in the virtual machine. Why I'd like this: I can use the virtual machine when I want to just use windows apps, and when I want to get gaming, I boot directly Windows, so I get no performance issues. Is there anyway to do this?

---

### Post by borahshadow on 2007-06-07
hmm Hi-res games you can try but you'll have to google on how to enable 3D in vmware
I'd reccommend atleast 1GB of ram so you can give your vm i'ts own 512MB ram is realy cheap right now so if you can upgrade
about your question I don't know I too have wondered this but I don't think there is a way(due to your computer haveing different hardware than the vm. windows would probably die if it booted up one day with mobo brand X and then booted up with mobo brand vmware XXX)

---

### Post by Hendrixski on 2007-06-07
> **Znupi said:**
> 
Here comes another question: if I make another dual-booting installation, is there any way to make a virtual machine that boots the windows partition? So I don't have to install it twice, once on the harddisk and once in the virtual machine. Why I'd like this: I can use the virtual machine when I want to just use windows apps, and when I want to get gaming, I boot directly Windows, so I get no performance issues. Is there anyway to do this?

YES.  You can do that with VMWare Server (which I don't think is in the repositories... you'd have to compile it yourself).  It's kind of hard to set up, and VMWare doesn't recommend that you do it because they can't support it... 

The benefit is that you can pause and resume windows... so that if you turn it off and hibernate Ubuntu... then restart Ubuntu and think "i'd like to check something in windows" it would only take about 10 seconds to resume the VM.  pretty sweet, eh?

but again... don't let it be said that I didn't warn you.  It's hard to set up, even if it is easy to use afterwards.   .... (oh, and some kernel updates can crash VMWare so you'd have to re-install VMWare tools from Add/Remove programs if that happens and it should fix it).

---

### Post by Znupi on 2007-06-07
Is [this](http://www.vmware.com/support/reference/win/rawdevices_win.html) what I need? It says it works with VMWare Workstation (I haven't got the slightest clue what the difference between Server and Workstation is).

I know, I know, I'm a complete noob when it comes to virtual machines and my questions probably sound really stupid... oh well :)

---

### Post by beerorkid on 2007-06-07
- vmware workstation costs $ It has advantages though

- vmware player can "play" virtual machines, but cannot create them

- vmware server allows you to create vm's which is probably what you will need.  Cuz you are going to have to install XP again.  There are many vm images you can download, but not windows ones.

I do not think you will be happy with gaming inside of a XP vm.  The RAM issue and well I doubt the graphics and framerates will be very good.  When gaming you want it to look good and run fast.  You will take a performance hit for sure trying to game in a VM.  That is just not what a vm is for.

You might be better still dual booting.

I dual boot at home for games only.  I use vmware server and their enterprise ESX at work.  I use vmware player at home because I have golden images of XP that I do some specific stuff with.  I have used workstations at home as well.

---

### Post by TekNullOG on 2007-06-22
If VMware desktop costs something and I am not willing to pay, what is the best way (easy and cheap) to create an XP Virtual machines? (already have an xp license)

Can it be done with vmware server and how easy is it to make a virtual machine of windows? (installing windows is def not a prob for me)

Thx

---

### Post by beerorkid on 2007-06-22
workstation is the one that costs $

Server will allow you to create a XP VM and it will work great.  I use it at work and home.

The differences between workstation and server are not that big of a deal.  I find it is easier to burn discs inside of workstation.  It seems that hardware is better supported in workstation.

I use VM's I made in workstation with server and player.  I use dvdshrink, DVDfree, and DVDfAB CONVERTOR IN THOSE vm's without any issues.

srry capslock issue

(for personal backups of DVD's I own)

---

### Post by kuja on 2007-06-22
One side note that you might want to be wary of: When you got to setup the VM for Windows, Get the hardware the way you want it set, then install it, then don't touch the hardware settings in vmware. I know it's easy and maybe tempting at times for whatever reason, but especially with regards to things like the amount of RAM or processor cores you can very quickly invalidate the windows license.

---

### Post by shadows85 on 2007-06-22
> **Znupi said:**
> 
Last, but not least, what vm should I use? I've read somewhere that VirtualBox is the most user-friendly and easy-to-use. Is that right?

Thanks in advance :)

Hmm easy to use yet I wasted the last five days on it..

---

