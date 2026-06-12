---
title: "Windows to Ubuntu"
date: 2007-05-27
forum: General Help
---

### Post by StrykeInferno on 2007-05-27
Before I install, will the programs/software I have on windows be compatible with ubuntu? And I want to install on a laptop and not a desktop.

---

### Post by pointone on 2007-05-27
Installing on a laptop is no problem.

However, Windows programs are not directly compatible with GNU/Linux. There are equivalent programs, though. For example, OpenOffice.org provides the same functionality as Microsoft Office, the GIMP replaces Photoshop and similar programs, and so on. If there are certain Windows programs you absolutely must use, you can possibly run them using Wine or Cedega, or use a virtual machine.

---

### Post by Alterax on 2007-05-27
These are some pretty valid concerns.  I made the switch to Ubuntu from Windows about a year ago; the only previous Linux experience I had was a stint where I used Mandriva 2007 for a couple of months.

Most Windows programs won't run on Ubuntu, or any other form of Linux.  Sometimes you can use the Wine API to run Windows apps, but using Wine can be difficult, especially for the newbie, and there are many programs that it won't run. I tried it for a while, decided my time could be put to other pursuits, and it wasn't long before I found linux-based software that does exactly what I was wanting to do.

My recommendation is to try using Wine for what you can at first, but also to look for native Linux programs that will do what your old Windows apps do:  Firefox works in place of Internet Explorer, OpenOffice replaces Microsoft Office (with more functionality), X-CD Roast works in place of Nero, GIMP replaces photoshop; you get the idea.

What programs are you wanting to use on Ubuntu on your laptop?  We may be able to come up with some alternatives to help you make the transition.  

--Alterax

P.S.  My own experiences with Ubuntu on Laptops has been pretty darn good; especially since Feisty was released, if that helps you any.


"It is logically impossible for one thing to be superior to another, while at the same time being identical to it"

---

### Post by jrusso2 on 2007-05-27
I disagree forget about using one unless there is one program that has no native Linux equivalent.  There are free Linux equivalents for most Windows applications.

These should be your first choice.  Only when there is no viable alternative should you try to use WINE

---

### Post by StrykeInferno on 2007-05-27
Applications should be no problem. The main thing is games because that is what my laptop is mainly used for.

---

### Post by Crafty Kisses on 2007-05-27
> **StrykeInferno said:**
> Before I install, will the programs/software I have on windows be compatible with ubuntu? And I want to install on a laptop and not a desktop.

I switched from Windows to Ubuntu, I must say it's kinda a pain at first, but after it's the best thing ever, you'll thank yourself for switching. ;)

---

### Post by randell6564 on 2007-05-27
There is also the option to dual-boot.

---

### Post by bmartin on 2007-05-27
> **StrykeInferno said:**
> Applications should be no problem. The main thing is games because that is what my laptop is mainly used for.
If you're talking about using emulators and such, then you won't have a problem. If you're talking about playing a lot of 3D games, you should have a look at the [Wine Database]("http://appdb.winehq.org/") to see if your games are supported. If they're not and you **must** have them, then I recommend you stay with Windows.

---

### Post by Twintop on 2007-05-27
> **randell6564 said:**
> There is also the option to dual-boot.

That, and in addition to Wine, you might be able to get VMWare working with a copy of Windows running under Linux. For newer games and whatnot though, this would probably only be a real option if you have massive amounts of RAM (2GB +).

---

### Post by strabes on 2007-05-27
If you're a gamer just dual boot the laptop. Install windows first on a 12-15gig partition and then install ubuntu on a different partition.

---

### Post by randell6564 on 2007-05-27
> **Twintop said:**
> That, and in addition to Wine, you might be able to get VMWare working with a copy of Windows running under Linux. For newer games and whatnot though, this would probably only be a real option if you have massive amounts of RAM (2GB +).
I would suggest **VirtualBox** before **VMware**. Especially if one is new to the whole thing.

---

### Post by StrykeInferno on 2007-05-29
apparently ubuntu needs a decent disk space because i have 15gb left and it wouldnt install. i didnt quite understand which "guide" installation style to use. also it seems that my wireless driver doesnt work = /

---

### Post by bmartin on 2007-05-29
> **StrykeInferno said:**
> apparently ubuntu needs a decent disk space because i have 15gb left and it wouldnt install. i didnt quite understand which "guide" installation style to use. also it seems that my wireless driver doesnt work = /
Ubuntu needs a few gigs, but 15 is plenty, Wireless often needs some tampering to get it going. Do you know what wireless chipset/card you have, or at least what brand it is?

What error did it give you to indicate that you didn't have enough space to install?

---

### Post by randell6564 on 2007-05-29
Yeah.,15 Gig is about 11 gig more than enough!  As far as your wireless goes, I use a Linksys.  It worked right out of the box, (which is wonderful considering the folks at linksys run scared when you mention the fact that you use Linux). When I upgraded to Feisty, I too had connection problems.  But after restarting a few times it worked! Don't really know why.
Please post the output of **iwconfig **
```
iwconfig
```
AND your **/etc/network/interfaces**

---

### Post by StrykeInferno on 2007-05-29
let me check a few guides on partitioning because it gave me three options: guided- use entire disk space, guided- use larget continuous free space, and manual

option 2 said there isnt enough space

---

### Post by merlinus on 2007-05-29
If you choose "use entire disk space," everything on your hard disk will be wiped out.

;)

-merlin

---

### Post by randell6564 on 2007-05-29
> **StrykeInferno said:**
> let me check a few guides on partitioning because it gave me three options: guided- use entire disk space, guided- use larget continuous free space, and manual

option 2 said there isnt enough space
Are you attempting to dual boot with windows?  What kind of HD's are you using? SATA, IDE...? Mixed?

---

### Post by StrykeInferno on 2007-05-29
dual boot yes type i have no clue

---

### Post by randell6564 on 2007-05-29
> **StrykeInferno said:**
> dual boot yes type i have no clue
Well.,if you're running Windows, open System Information, and look under Hardware.

---

### Post by randell6564 on 2007-05-29
>  also it seems that my wireless driver doesnt work 
BTW.,If Ubuntu is not even installed yet, how do you know that your wireless is not supported?  LiveCD?

---

### Post by StrykeInferno on 2007-05-29
well now i know it's a hitachi.

also the wireless thing i got settled so no need to think about it too much now

---

### Post by bmartin on 2007-05-29
Normally in the installer there's an option to resize the existing partition. Before running the installer, try running **qtparted** (or gparted) and resizing your Windows partition so that you have 10-15GB of unpartitioned space (you might want to save some of the space for Windows).

If in doubt, open a terminal and type in **sudo qtparted** (or sudo gparted); one of those should be available.

After that, run the installer. You should then be able to use the unpartitioned space to install Ubuntu.

---

### Post by randell6564 on 2007-05-29
> **bmartin said:**
> Normally in the installer there's an option to resize the existing partition. Before running the installer, try running **qtparted** (or gparted) and resizing your Windows partition so that you have 10-15GB of unpartitioned space (you might want to save some of the space for Windows).

If in doubt, open a terminal and type in **sudo qtparted** (or sudo gparted); one of those should be available.

After that, run the installer. You should then be able to use the unpartitioned space to install Ubuntu.
Yes but be VERY careful!  Resizing existing partitions that house OS's can be very dangerous!

---

### Post by merlinus on 2007-05-29
I have found it imperative to defrag the windows partition several times and set virtual paging to zero before trying to re-size.

After partitioning for ubuntu, you can change the virtual paging back to somewhere near where it was.

Otherwise, gparted will not work as well, and there is an excellent chance the windows bootloader will be trashed.

ymmv.....

-merlin

---

### Post by blacksadness on 2007-05-30
the install should have had a 3rd guided option to resize windows, probably you have windows partition loaded, right click on it and unmount it then try the install process, also a defrag is indeed recommended.
for games, you might want to take a look at cedega ([www.transgaming.com](www.transgaming.com)) they have a good database if wine didn't manage to run the game..

---

### Post by StrykeInferno on 2007-05-30
paritioning windows resulted in an error that said partition could not be applied, but when i look at the new partition it did partition it/

so i have 10gb of unallocated space

---

### Post by Shadoweater12081980 on 2007-05-30
If you want games, grab hold of cedega, its pretty sweet. Either that or grab the Loki installers (not used them myself but they look ok)

Otherwise dont try and port windows apps over, just use the ones designed for the system. Windows apps for Windows, Linux apps for Linux

I'd personally reccommend adapting to the Linux system as most of the methods are fairly similar in certain apps so it should be fairly painless but expect some heartache at first. You will get there

Hope it works out for you

---

### Post by StrykeInferno on 2007-05-30
the only two things i really worry about that won't work on linux is world of warcraft and itunes. everything else i can live without or with another version

---

### Post by bmartin on 2007-05-30
I can guarantee that [iTunes]("http://appdb.winehq.org/appview.php?iVersionId=5774") won't work. [World of Warcraft]("http://appdb.winehq.org/appview.php?iVersionId=6482") will. You'll need to use Wine, which is actually pretty easy to use. The links I've provided will take you to the relevant Wine Application Database pages, which tell you about what works and what doesn't.

There are other ways to load up your iPod with songs in Linux, and there are other programs which allow you to purchase music, if that's what you desire. However, you'll have to fight with iTunes if you want it to work. You can use Google to look for instructions, but I doubt it'll be easy if it works at all.

---

### Post by StrykeInferno on 2007-05-30
the songs i purchased from itunes are saved to my account right? so when i log onto another windows computer to install itunes, it  will redownload?

---

### Post by randell6564 on 2007-05-30
> **StrykeInferno said:**
> the songs i purchased from itunes are saved to my account right? so when i log onto another windows computer to install itunes, it  will redownload?
Yes. Your iTunes account is saved on the iTunes server.

---

### Post by sk1dr0w on 2007-06-28
Amarok works entirely well with ipods. amarok is also what i would consider an awesome alternative to itunes, except for being able to download directly from the program (which is what torrents are for). also, it won't (as far as i know) play your password-protected songs you've gotten from the itunes store, SO i would definitely suggest converting them to .mp3 if you can.

---

### Post by Qu4k3R on 2007-06-28
I just use Wine - it is a great program to "run" Windows Applications (some games) .. few, but it works.
I have a dual-boot (40 G for windows, 16 G for ubuntu) it works perfectly.
Whenever I want to use windows, I use windows, whenever I want ubuntu linux (almost everytime).
I do it.

I almost do not use windows (XP)..

---

