---
title: "Migrating from Windows."
date: 2008-01-12
forum: General Help
---

### Post by tom_the_drummer on 2008-01-12
I am considering going from Windows XP home to Linux - I figure if I don't like it I can just go back! However I Have a couple of questions:

1) How easy is it to get my windows PC to talk to this what would be ubuntu PC?

2) My router and various bits of hardware have "designed for windows" on them. Does this mean my linksys wireless G router for example will no longer work with my laptop?

3) What programs are there so far as internet security go?

4) Are there any programs out there which can emulate windows because I have some software that I would like to install but I think it may be windows only.

5) How many applications come with Ubuntu?



EDIT:

6) If I have two partitions on the hard drive one for Windows and one for Linux which has to be installed first? The windows OS or the Linux OS?

7) How do I select which OS I want to boot?



Thanks for all the help guys!!!!


Tom

---

### Post by kool_kat_os on 2008-01-12
The router will work
I wouldnt worry about security (that)much

---

### Post by kool_kat_os on 2008-01-12
About the Apps, the ones that are included are very useful

---

### Post by krendar on 2008-01-12
> **tom_the_drummer said:**
> 
1) How easy is it to get my windows PC to talk to this what would be ubuntu PC?


You mean they are two seperate PC's over network or the same PC but different partitions? First case you can install Samba and have your linux box act like a Windows Network Share, second case you can "mount" your Windows Partitions in Linux and copy files that way from system to system. Both are pretty easy, I even think Ubuntu comes with GUI applications to do it for you.

> 
2) My router and various bits of hardware have "designed for windows" on them. Does this mean my linksys wireless G router for example will no longer work with my laptop?


You router does not "care" which OS your PC runs.

> 
3) What programs are there so far as internet security go?


There are some firewall applications, antivirus-apps exist but they are mainly meant to scan for Windows viruses as there really are no viruses to speak of on Linux (as far as I know)

> 
4) Are there any programs out there which can emulate windows because I have some software that I would like to install but I think it may be windows only.


Wine works pretty well with some exceptions. You can also get VMWare for Linux if you don't mind the speed penalty it implies to run it.

> 
5) How many applications come with Ubuntu?


Lots :)

All your typical desktop applications are installed by default. OpenOffice, webbrowser, email, music/movie player. You can get a ton of network and programming applications as well. Games are probably better in Windows though.

> 
6) To have two partitions on the hard drive one for Windows and one for Linux which has to be installed first? The windows partiotion or the Linux partition?


Install Windows first as Ubuntu will install a bootloader and set up a Windows entry automatically.

> 
7) How do I select which OS I want to boot?


See previous answer

---

### Post by kool_kat_os on 2008-01-12
The os boot thing..... When your computer boots it will have GRUB bootloader load and it lets you select the OS

---

### Post by avik on 2008-01-12
There are plenty of applications preloaded, and you can easily get new ones (and I do mean easily).

You want to install Windows first, then Ubuntu.  This will set up GRUB, a boot loader that will allow you to choose with OS you want to boot from.  Installing Windows second will overwrite GRUB with the Windows boot loader, preventing you from accessing Ubuntu.

There are firewalls, and you don't have to worry about viruses or other malware.

There's something called WINE, a compatibility layer that allows you to run many Windows software.  However, there are many alternatives to most applications, so look around before defaulting to WINE.

---

### Post by vanndrage on 2008-01-12
1. this is fairly simple to do with little to no configuring
2. your linksys router (or any router) will still work just fine with linux, you just cant load the cd that came with it, but you can still configure it using the web gui
3. there are tons of different internet secuirty programs for linux, once you get ubuntu running just go into your synaptic manager and do a search, will have lots to pick from
4. you can use wine to emulate windows programs, this only works with some programs though, just google yoursoftwarename wine and you should be able to find out if it will work.
5. many applications come with ubuntu, and the ones that done come pre-installed can easily be installed using the synaptic manager

---

### Post by kool_kat_os on 2008-01-12
ya.

---

### Post by deejross on 2008-01-12
I can try to answer a couple of questions based on my experience. To give you a little background, I have both a Ubuntu machine and an XP machine. After about of month of running both, I have totally switched to using Ubuntu all the time, and I leave my XP machine running because it has all my files. Based on this, I will answer the obvious ones for me:

1) It is easy to share out folders from the XP machine and mount those shares in Ubuntu.
2) Alot of things are designed for Windows, but that doesn't make them exclusive to Windows. Routers really don't care what kind of OS it's talking to, so it's not an issue. However, I would load up a Live CD to make sure that Ubuntu has drivers for your wireless card in your laptop.
3) Linux has built-in security that protects you against 99% of internet threats...it locks the user out of system critical files. This prevents viruses, spyware, adware, malware, etc. from running on Linux machines unless you are actually trying to run them. There are virus protectors for Linux, but really all they do is scan for Windows viruses so you don't accidentally send something to a Windows-using friend.
4) You have a few options for emulation. You can use QEmu, but you should really use a virutalization product. VMware Server is free and runs on Linux. VirtualBox is also free (and open source), though I personally prefer WMware.
5) Ubuntu comes with LOTS of programs. Office products, games, communications applications, etc. In fact the default install includes enough applications for the average user's needs.
6) The easiest way is to install Windows first, then use the Ubuntu installer to partition the hard drive for you.
7) After you install Ubuntu it will install grub, which is a bootloader that will ask you what you want to run when you turn your computer on.


Hope this helps and feel free to ask more questions if you need to.

---

### Post by kool_kat_os on 2008-01-12
One Very useful tip, if your boot time is really slow with ubuntu do the following changes:

Go to terminal and type in :
```
sudo gedit /boot/grub/menu.lst
```

Then the configuration file will open:

Make the following changes to this entry:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cf025937-1e2d-4d5b-8135-fe7ecd6998fd [COLOR="Red"]ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]

```
remove the

ro quiet splash

and the

quiet
So it looks like this:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cf025937-1e2d-4d5b-8135-fe7ecd6998fd 
initrd		/boot/initrd.img-2.6.22-14-generic

```

---

### Post by tom_the_drummer on 2008-01-13
What is this "terminal" of which you speak? And what is this synaptic manager?

Sorry but Linux is completely new to me!!!

---

### Post by xtreme- on 2008-01-13
A terminal is just a command-line-interface. This is a contrast to a graphical user interface (GUI) that you probably normally use when you use a computer. In a terminal, you just type commands and get (text) responses, but in a GUI you can enjoy pressing buttons and viewing dialog boxes.
You will probably learn using the terminal over time, but it's not needed - don't worry about it.
A terminal can be opened just like any other program from the Ubuntu menu.

Synaptic Package Manager is just a program for managing your installed programs. It lets you install and remove programs, and by installing through it you will ensure that they will stay updated through the internet. But for installing "normal" programs (i.e. not drivers and such), you will probably find "Add/remove" easier to use (also in the menu).

I recommend you to download Ubuntu and start playing around with it. You can run it directly from the CD without touching your hard drives. Or you can install it on a partition.

Learning by doning is nice.:)

Good luck!

---

### Post by r57 on 2008-01-13
Hi!

terminal is something like command line in windows. U will find it in ubuntu in "Start menu" in accesioners. 

If U are as beginner as U say I wouldn't edit that file if I was you, beacause it isnt necessary and relevant to run ubuntu, it is just speedup :)
e will be lost after installatio
Synaptic manager is program that u will use to install software. U simply select what U want and it downloads and installs all that  stuff. U will find it also in "Start menu" (It will look like strat menu to U, so I am calling it Start menu ;) )

If U dont have experience with linux. Don't install ubuntu immeadly. First burn Live CD. Boot it. And look around. I suppose U will like ubuntu. Ubuntu will of course run much faster after installation on hard disk. But if U are just curious, Live CD is ok.  If U like it, U can install ubuntu from Live CD. Just double click install icon on desktop and do setup.

Note that that when booted to Live CD, U cannot save data to hardisk, therefore everithing U save will be lost after reboot.

---

### Post by tom_the_drummer on 2008-01-13
So to get this live CD I take it I just download from the main website and burn the file onto a CD?

---

### Post by deejross on 2008-01-13
That is correct. You will need an application to burn the ISO file once it's downloaded. There are several programs out there for doing it: Nero($), ImgBurn(free), etc. But, you will need to check your BIOS and make sure that it will boot from the CD once you've burned and inserted it.

---

### Post by Sef on 2008-01-13
Read [Psychocat's Ubuntu]("http://www.psychocats.net/ubuntu/index.php") and the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by tom_the_drummer on 2008-01-13
Thanks for all the help everyone. I think I shall download the ISO, burn it to as disk and then try ubuntu from the live CD.

And doing this will definaetly not loose me any documents or anything?

---

### Post by deejross on 2008-01-13
No, the live CD just loads Ubuntu up into memory, without touching your hard drive. Only when you run the Install program does it make any changes.

---

