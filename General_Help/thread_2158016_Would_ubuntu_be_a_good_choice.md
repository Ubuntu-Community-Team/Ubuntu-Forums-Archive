---
title: "Would ubuntu be a good choice?"
date: 2013-06-27
forum: General Help
---

### Post by thegutterpoet on 2013-06-27
I have recently purchased a second-hand HP mini 5101 notebook with specifications of...

[COLOR=#000000][FONT=Verdana]Intel Atom CPU N280 @ 1.66 GHz CPU[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]1GB DDR2 Ram[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]160GB Sata Hard Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]No optical drive as this is a netbook[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Bluetooth[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2MP Webcam

Running the pre-installed Vista Business with just the 1gb of ram seems OK. However, I am wondering if ubuntu or another easy to use linux distro would help me to get the best out of the hardware???? Are there any linux routines specifically designed for netbooks???

As for usage, I really only wish to create text documents, browse the net, stream the odd youtube video clip or football match...at a stretch, watch a film.

Are there any clear advantages to installing ubuntu or another linux OS over the present vista OS?

any help is greatly appreciated,
cheers,
TGP[/FONT][/COLOR]

---

### Post by zero2xiii on 2013-06-27
Hay,

Yes I would recommend Lubuntu, since it is REALLY lightweight, yet has everything you need. I am not sure of the ubuntu netbook remix is still around... But Lubuntu's minimum requirements are pretty low.

Only catch is, you will need to create a live USB to install it, or use an external optical drive and some people have had issues installing from them.

Cheers and good luck.

---

### Post by Mark Phelps on 2013-06-27
Some will argue with this, cause after all, you ARE in the Ubuntu forums, but Ubuntu is not some miracle cure that is going to turn a wornout old slow PC into a powerhouse of performance.  They will say that Ubuntu will run faster than Vista -- but while that is true, basically ANYTHING will run faster than Vista.  Vista barely runs, limping along, with your processor and only 1GB of memory.  IF you want to get more out of your hardware, you should boost that to 2GB of memory.  I did that on a old laptop and the boost in performance was amazing.

The main downside you're going to run into is drivers -- a long-standing weakness of the Linux distros in general. The more specialized hardware you have on your PC, the less likely it's going to work well in Linux.

If your PC can boot from USB, I would use the Universal USB Installer from PendriveLinux .com, together with an ISO file of the Ubuntu version you want to run, to create a bootable USB stick of Ubuntu, boot from that -- and see how well it detects your hardware and installs working drivers.  It will run slower than usual because it's reading from a USB stick, not a hard drive, but you will get a feel for how well it works and how it behaves.

---

### Post by snowpine on 2013-06-27
You can "dual boot" which means install Linux side-by-side with Windows, so that you can choose between them each time you turn on the computer.

I have a dual boot on my Atom netbook (Fuduntu and Windows XP). I use Linux for web surfing and word processing, and Windows for watching videos/movies and running a few Windows apps I need for work.

---

### Post by HermanAB on 2013-06-27
Lubuntu or Xubuntu would run fine on that machine. Regular Ubuntu will be slow as molasses.

---

### Post by thegutterpoet on 2013-07-18
I have now been forced into installing a linux iso as my windows vista has gone to the dogs and simply wont work anymore...As I am away from my home and traveling through south east asia I have downloaded an ubuntu 12.04 iso, used the program to create a bootable usb and am now typing from my booted ubuntu on usb. I have managed to locate the files on the windows vista business installation that is corrupt and am copying those over to another usb as I type now.

My plan is to install ubuntu straight after the files have copied over, but I need some advice with the partitions...

What size do I make my swap file??? and how do I create the partitions?? Is it essential I make a / AND /home partition????

From what I read above, if I am to use the netbook for mainly browsing, word processing and watching films...I am likely better off using lubuntu or xubuntu??? Which one suits my hardware better???

any advice is well appreciated.
cheers
TGP

---

### Post by snowpine on 2013-07-18
The installer will automatically choose the optimum partitions and sizes (unless you choose "something else"). :)

Full install instructions are here: [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

(no need for me to retype them for you, right? ;))

---

### Post by thegutterpoet on 2013-07-18
the first option it gave me was a simple straight REPLACE of windows vista...will that automatically suggest/create a swap and home partition??? Or must I head through the second option, which allows me to edit the partitions manually???

---

### Post by snowpine on 2013-07-18
I am confused whether you wish to completely replace Vista or install Ubuntu side-by-side?

---

### Post by kokoshmusun on 2013-07-18
I'm surprised you got Vista to work at all.  I would say if you don't absolutely need it, don't do a dual-boot with Vista.  Vista is the worst OS I've ever seen; it forced me to discover linux.  

On smaller/older machines, I've found Lubuntu to work the best.  It's a bit lighter than Xubuntu, which is also a great distro.  If you need über-fast, try Puppy Linux, but it's bare-bones and odd coming from Ubuntu.  So I'd say wipe out everything and install Lubuntu.

---

### Post by thegutterpoet on 2013-07-19
> **kokoshmusun said:**
> I'm surprised you got Vista to work at all.  I would say if you don't absolutely need it, don't do a dual-boot with Vista.  Vista is the worst OS I've ever seen; it forced me to discover linux.  

On smaller/older machines, I've found Lubuntu to work the best.  It's a bit lighter than Xubuntu, which is also a great distro.  If you need über-fast, try Puppy Linux, but it's bare-bones and odd coming from Ubuntu.  So I'd say wipe out everything and install Lubuntu.

I've erased Vista now...chose the first installation option and am now running Ubuntu 12.04 LTS which seems fine. At the same time as advised I am downloading the latest iso of 32 bit Lubuntu and also Xubuntu and will most probably make a bootable usb drive of the iso and return to the forum here later and aim for even more confirmation that Lubuntu is my best bet for what I need to use the netbook for.

My only reservation is the drivers...ubuntu seems to have found all the drivers, or most of them it needs to run on my netbook with ease, internet and display and sound all working fine straight after the install and I am yet to even start the update manager downloading its 281 updates. Will Lubuntu install, most likely, with similar compatibility???

Lastly...would I choose the first option with the Lubuntu install again??? And let the install program choose whats best and write over everything already on the HD or am I better off attempting to re-partition manually???? I just have this nagging concern about the lack of a swap partition...or does the install program create one automatically??? Do I even need one??? Ubuntu seems OK for now, but I will be trying Lubuntu...why not eh!

keep the advice flowing, ubuntu folks...please and thanks

After watching some youtube reviews of lubuntu and xubuntu I am ;leaning towards xubuntu 12.04...If this Ubuntu seems to run okay on this hardware then surely Xubuntu will run even smoother???? I don't want to insult the hardware by treating it like a machine 10 years its senior!!!

---

### Post by 3rdalbum on 2013-07-19
Xubuntu and Lubuntu are the same as Ubuntu underneath the graphical user interface. The drivers are the same.

The Ubuntu installer automatically creates a swap partition. Same with Xubuntu and Lubuntu. They don't automatically create a special /home partition, but you don't need one these days.

If everything is working okay, why change to Xubuntu? I use Ubuntu on my netbook.

---

### Post by thegutterpoet on 2013-07-20
> **3rdalbum said:**
> Xubuntu and Lubuntu are the same as Ubuntu underneath the graphical user interface. The drivers are the same.

The Ubuntu installer automatically creates a swap partition. Same with Xubuntu and Lubuntu. They don't automatically create a special /home partition, but you don't need one these days.

If everything is working okay, why change to Xubuntu? I use Ubuntu on my netbook.

Indeed, I may stick with this ubuntu installation, which seems to be solid if far from speedy. Still an improvement over the previous vista business routine. With only 1gb of RAM I can't expect too much...however, would lubuntu or xubuntu offer a marked improvement in speed over this ubuntu 12.04 OS on my current system????

---

### Post by snowpine on 2013-07-20
> **thegutterpoet said:**
> Indeed, I may stick with this ubuntu installation, which seems to be solid if far from speedy. Still an improvement over the previous vista business routine. With only 1gb of RAM I can't expect too much...however, would lubuntu or xubuntu offer a marked improvement in speed over this ubuntu 12.04 OS on my current system????

Quite possibly... it would take you a couple of mouse clicks and about 5 minutes to find out. ;)

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by thegutterpoet on 2013-07-20
So...using the above method in your link will pretty much give me the same experience as if I installed xubuntu or lubuntu over the current ubuntu installation??? Is the graphical interface really the only difference??? If so, and it gives me a marked improvement in speed then I am happy to lose some aesthetic charm. I will give your link guide a roll of the dice. Cheers for that!

---

### Post by snowpine on 2013-07-20
You don't need to reinstall to get a different desktop environment; you can install them from the Software Center. 

Lots of other great tutorials on that site, I suggest an hour or two of browsing and learning. :)

---

### Post by thegutterpoet on 2013-07-20
Apologies for likely appearing lacking PC knowhow, but I assumed that lubuntu and xubuntu were fully different operating systems, like ubuntu but much slimmer in all ways...from what you are telling me, its purely the desktop environment that differs, and using the technique outlined in the link, I can use Lubuntu or Xubuntu as simply different desktop environment options running from the same OS and choose when I boot...rather than needing to completely re-install???

---

### Post by kokoshmusun on 2013-07-20
Lubuntu would most probably be significantly faster than Ubuntu and a bit faster than Xubuntu.  I would say do a clean install if you're just starting.  Yes, you can change your DE from the command line but if you are a newbie it needs a few hours of learning and if you break something, that time will increase.  Just do a fresh lubuntu install.  Lubuntu is aesthetically pleasing in its own way, I really like it and it's very efficient.  My only problem was some Gnome (back in the day)/Unity era apps don't integrate with LXDE and XFCE the same way.  So what apps you heavily rely on and how they look and function under Lubuntu/Xubuntu is another consideration. 

Lubuntu is a really good compromise for someone who wants to go a bit minimal but not as minimal as Arch/Debian/PuppyLinux.  You're still connected to the Ubuntu eco-system, things still look and sound more or less familiar.

---

### Post by snowpine on 2013-07-20
Yes, you can add the "X" or "L" to an existing Ubuntu install. :)

---

### Post by thegutterpoet on 2013-07-20
> **snowpine said:**
> Yes, you can add the "X" or "L" to an existing Ubuntu install. :)

And what of this...
'**Warning**: having Xfce and Gnome together means you'll have cluttered application menus full of Xfce applications *and* Gnome applications.'

Its purely speed I am after,, snowpine...I MUST HAVE MORE SPEED!

---

### Post by snowpine on 2013-07-20
Having cluttered application windows will not make your comptuer slower. However, the site I linked to has instructions to remove Unity/Gnome if you wish and achieve "pure LXDE" or "pure Xfce." :)

---

### Post by cmcanulty on 2013-07-20
I would do something else for partitions- 10-15 GB for /, 2GB for swap, and the rest for /Home. It keeps your docs and settings separate from the OS so you can switch around as you like. Also you can install Xubuntu, Lubuntu etx from synaptic and choose which one at login experiment a bit and you can always uninstall the ones you don't like without messing up your system

---

