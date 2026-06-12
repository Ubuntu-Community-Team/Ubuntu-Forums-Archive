---
title: "Noob needs some answers"
date: 2013-01-06
forum: General Help
---

### Post by pnr2501 on 2013-01-06
Hello folks,

today I've been trying out Linux for the first time.

I consider myself as an experienced computer (I know this term is relative^) user and managed to get through installation (12.10) without any problems.

After my first boot I was kinda shocked. I thought Ubuntu was a noncommercial OS - but in my Launcher or however it is called I found an "Amazon" Button. Also I get suggested Applications that I have to pay for in the Ubuntu Software Center.

The first thing I did was uninstalling Ubuntu One and this Ubuntu Music Store (forgot how it's called). It's kinda funny. I know Windows is the real commercial OS, but from the lookings I'd describe Ubuntu as commercial.

I still have got some Ubuntu One stuff in my context menu. How can I finally remove it? And how can I disable paid apps (and just those) in the Ubuntu Software Center? Is there any other kind of application integrated that I could spend money on and that therefore should be removed?

Another problem I have is driver related I guess. My System is much louder under Ubuntu than in Windows. I think it's because there is no proper graphic cards driver installed and my GPU fan is running at a higher speed than it needs to. - It could also be the CPU fan of course. How do I get my PC as quiet as it runs in Windows?

In System Setting > Details it shows no information on the installed graphic cards driver. It seems it didn't install one even tho I was connected to the internet when installing Ubuntu from the live system.

I tried manually downloading the latest catalyst (12.10). I got a .run file which I need to compile in a .deb file, as google told me. However, the instruction I found were for older versions of Ubuntu and did not work for me. Can anyone link me to a detailed instruction? That would be very appreciated.

Sadly my PC crashed two times in like 4 hours of running linux and I had to reset it manually. Also, an app named "compiz" crashed several times. Could it be related to a missing graphic cards driver? 

Nevertheless I'm still interested in learning Linux and I know that I will need a lot more patience. My goal is to be able to setup my own Arch linux at some day (far away) in the future.

Did I make the right choice to start with Ubuntu? Are my expectations too high? Any advice is welcome.

regards,
Ian

edit: Also I'd appreciate if you could hint me some good beginner guides. The ones I have found didn't seem to be too good. I'm just scratching at the surface right now. :-(

---

### Post by JiuJitsu500 on 2013-01-06
Hello and welcome to linux!

Ubuntu is awesome for beginners, but when they run into issues like yours first go they get turned off. Too bad too, but it's hard to keep up with tecjhnology without M$ or Apple salaries and millions of independent developers.

Up until 12.10, I didn't think unbuntu was proprietary at all either, and still isn't when you remove everything. First though, we need information about your computer, RAM, Graphics, etc... most of it should be easy fixes to get you up to speed. It took me a couple hours to customize and tweak my ASUS ROG G53 with a lot of hardware upgrades, but now it runs better than anything. I can almost travel time and see through walls. You don't have to pay for ANYTHING if you don't want to either, I've donated, but never paid for a single app and can do everything I can on windows or Mac, better, for free - except do things on my Zune or new iDevices (without virtualizing, once I do that there is no limit to what I can do except gaming).

So computer info first, and I'd reccomend going to ubuntu 12.04 since it's supported for 5 years, 12.10 is 18 months. More than enough, but the LTS releases are always more stable.

I'm not a huge fan of what cononical did with 12.10, but it does work very well on every computer I've put it on, even a MacBook Air after some tweaking. That's the fun part though, is the tweaking... welcome to true computer and software freedom.

---

### Post by howefield on 2013-01-06
> **pnr2501 said:**
> And how can I disable paid apps (and just those) in the Ubuntu Software Center?

[http://askubuntu.com/questions/47997/how-to-remove-the-for-purchase-section-from-the-software-center](http://askubuntu.com/questions/47997/how-to-remove-the-for-purchase-section-from-the-software-center)

You can also disable the shopping lens by toggling the switch in System Settings > Privacy and or uninstall the package unity-lens-shopping.

> My System is much louder under Ubuntu than in Windows. I think it's because there is no proper graphic cards driver installed and my GPU fan is running at a higher speed than it needs to. 

Have you tried the Additional Drivers tab in Software Sources to see if there are any proprietary drivers available for your system ?

> Sadly my PC crashed two times in like 4 hours of running linux and I had to reset it manually. Also, an app named "compiz" crashed several times. Could it be related to a missing graphic cards driver? 

Have you updated your system since installing ?

---

### Post by Calinou on 2013-01-06
> **pnr2501 said:**
> 

After my first boot I was kinda shocked. I thought Ubuntu was a noncommercial OS - but in my Launcher or however it is called I found an "Amazon" Button. Also I get suggested Applications that I have to pay for in the Ubuntu Software Center.

```
sudo apt-get remove unity-lens-shopping
```In a terminal, type this, then reboot. Or, you can install another desktop environment, try Xfce for an example:
```
sudo apt-get install xubuntu-desktop
```Then log out and switch to Xfce by clicking on the Ubuntu logo.

> **pnr2501 said:**
> The first thing I did was uninstalling Ubuntu One and this Ubuntu Music Store (forgot how it's called). It's kinda funny. I know Windows is the real commercial OS, but from the lookings I'd describe Ubuntu as commercial.
It is commercial by default. Windows and OS X are always commercial. Ubuntu (and especially its derivatives) are not.

> **pnr2501 said:**
> I still have got some Ubuntu One stuff in my context menu. How can I finally remove it? And how can I disable paid apps (and just those) in the Ubuntu Software Center? Is there any other kind of application integrated that I could spend money on and that therefore should be removed?

You can use Synaptic or the command line to install software instead.

> **pnr2501 said:**
> Another problem I have is driver related I guess. My System is much louder under Ubuntu than in Windows. I think it's because there is no proper graphic cards driver installed and my GPU fan is running at a higher speed than it needs to. - It could also be the CPU fan of course. How do I get my PC as quiet as it runs in Windows?

What is your hardware? If you have switchable graphics, note that switchable graphics were always "experimental" regardless of the OS... which is why I stay away from laptops.

> **pnr2501 said:**
> Sadly my PC crashed two times in like 4 hours of running linux and I had to reset it manually. Also, an app named "compiz" crashed several times. Could it be related to a missing graphic cards driver?

Use another window manager (if you use another desktop environment, you will probably use another one).

> **pnr2501 said:**
> Nevertheless I'm still interested in learning Linux and I know that I will need a lot more patience. My goal is to be able to setup my own Arch linux at some day (far away) in the future.

Harsh Linux. There is no point in running that unstable, insecure distribution. It is not any faster than Ubuntu.

*Noob answers answered.®*

---

### Post by pnr2501 on 2013-01-06
Thank you guys for your quick answers!

> So computer info first

Gigabyte P55a UD-3
Intel Core i5 750 (4C/4T) @ 3,4GHz
12GB RAM (DDR3-2133MHz @ ~1600MHz CL-8..)
AMD Radeon 7970

> and I'd reccomend going to ubuntu 12.04 since it's supported for 5 years, 12.10 is 18 months. More than enough, but the LTS releases are always more stable.

That sounds logic. I will do as you suppose and erase my linux drive and install 12.04 within the next 16 hours.

> You can also disable the shopping lens by toggling the switch in System Settings > Privacy and or uninstall the package unity-lens-shopping.

Appreciated! - Thank you very much!
I hope it works like that in 12.04 too. :)

> Have you updated your system since installing ?

I'm not exactly sure what you mean by 'updated', but I guess no - I didn't make any major changes to my system since installing. I remember that one crash came when I changed a theme back an forth.

> Have you tried the Additional Drivers tab in Software Sources to see if there are any proprietary drivers available for your system ?

No, I did not do that yet. I will keep that in mind for my 12.04 install and report here again.

> but it's hard to keep up with tecjhnology without M$ or Apple salaries and millions of independent developers.

True words. I love the idea of open source software and I want to support it at all (reasonable :neutral:) cost. If I stay with Linux I'm sure I will donate a fair amount (comparable to the price of a windows license) to my distribution of choice.

Thanks for all your replies so far. I'm curious about more hints and ideas and will keep an eye on this thread.

edit: Also thanks to calinou for your reply and giving me code for terminal. This is exactly what I want to learn because it feels much more real and powerful.

> Harsh Linux. There is no point in running that unstable, insecure distribution. It is not any faster than Ubuntu.
Well, the idea behind is that you need a lot of knowledge to be able to set it up. Right now I'm not to keen on running a certain distribution rather than to learn how to handle a linux system. But maybe there are other ways to achieve this. It is likely that I will give up this goal as I dive deeper into the matter of linux.

---

### Post by arpanaut on 2013-01-06
Just my perspective on Ubuntu becoming "commercialised" 
This is an effort to bring in revenues to finance the continued development of a Free ($) operating system.
The offered ability to purchase things from within Ubuntu is purely optional. 
Ones ability use the system is not impaired by not purchasing software, and not using the shopping lenses.
I don't use the music store and it does not bother me that it is there.
I enable the Amazon lens when I am shopping and am happy that Ubuntu sees monetary gain from my purchase, otherwise it is disabled and out of the way.
I use synaptic or the command line to install software so I never see the commercial products.
But I do not have a problem with these products being there for those who want them, and it helps finance those developers, and Ubuntu.  No Harm, No Foul!

I think it is a Win/Win any way you look at it, Ubuntu gets added financial support and if one does not want to participate disable that aspect of this Free Operating System. 
As for the paranoia about searches being logged etc. don't use the shopping lens... simple.

Some food for thought for the newbie.

---

### Post by pnr2501 on 2013-01-06
> Some food for thought for the newbie.
:popcorn: Doesn't taste too bad. ^^

> Ones ability use the system is not impaired by not purchasing software, and not using the shopping lenses.
That is true.

It's hard to tell why it annoys me. I will have to think about an explanation. I disgust advertising of all kinds, I also use my adblocker to block even non-intrusive advertising.

I would have loved to opt-out for this amazon lense and music store and stuff. I rarely buy stuff on amazon - not to talk about music.

But, just as you, I think it is undeniable that Ubuntu deserves to get supported from its users. I also will contribute, i I stick to Ubuntu. But I will do it in my way.

I don't need the music store and shopping lense or how it is called. And "I don't need" in this case is synonymous for "I don't want".

Here a short summary of my next steps:

-create a bootable stick with Ubuntu 12.04 (LTS ftw)
-install
-sudo apt-get remove unity-lens-shopping
-sudo apt-get install xubuntu-desktop
-learn more about Synaptic and/or the command line
-check this thread

Are there any other desktop environments that can be recommended? I'm glad about every hint or link.

I hope to get further advice about how to optimize, customize and tweak Ubuntu for my hardware.

---

### Post by howefield on 2013-01-06
> **pnr2501 said:**
> I'm not exactly sure what you mean by 'updated', but I guess no - I didn't make any major changes to my system since installing...

When you installed 12.10 you installed the package set which was available at the time of release, one of the first things to do on a fresh install is make sure that you have the most up to date packages, run Software Updater in 12.10 or Update Manager in 12.04.

In 12.04 you will probably find a couple hundred updates waiting for you.

---

### Post by pnr2501 on 2013-01-06
> **howefield said:**
> When you installed 12.10 you installed the package set which was available at the time of release, one of the first things to do on a fresh install is make sure that you have the most up to date packages, run Software Updater in 12.10 or Update Manager in 12.04.

In 12.04 you will probably find a couple hundred updates waiting for you.

:roll:... now I see what this Number 2xx on the launcher icon meant.
-.- The error often sits 1 meter away from the monitor. Now this is even a bit embarassing. I should have gotten this idea myself. :-D

Thanks howefield!

Update:

[LIST=1]
[*]create a bootable stick with Ubuntu 12.04 (LTS ftw)
[*]install
[*]run Update Manager
[*]look in Software Sources / Additional Drivers tab for available proprietary drivers
[*]sudo apt-get remove unity-lens-shopping
[*]remove Ubuntu One following [these instructions]("http://hex.ro/wp/blog/removing-ubuntuone-from-ubuntu-12-04/") (could fail because of my noobishness)
[*]sudo apt-get install xubuntu-desktop
[*]learn advantages and disadvanteges of the different desktop environments
[*]learn more about Synaptic and/or the command line
[*]check this thread
[/LIST]

The Update Manager is self-explanatory, I guess?

In the meantime I have found an [interesting article]("http://scriptevolution.com/blog/2012/08/top-10-ubuntu-desktop-environments-and-shells/") about the different desktop environments for Ubuntu and I'm looking forward to try them out tomorrow.

While I skimmed through the text it turned out that I am too used to windows, not to say I am infected with windows. I will have to read some stuff about window managers, tiling and that stuff...

- Anyways.

Further advice on how to customize and tweak Ubuntu (12.04) for my hardware is still welcome.

[INDENT]P55 Chipset (Gigabyte P55A-UD3)
i5-750 (4x3,4GHz)
12GB DDR3
Radeon 7970[/INDENT]

---

### Post by howefield on 2013-01-06
If you are going to install xubuntu-desktop, you may consider simply installing Xubuntu 12.04 in the first place.

Will remove steps 5,6 and 7 from your plan.

Although one point of note is Xubuntu 12.04 comes with 3 years of support, whereas Ubuntu 12.04 has 5 years of support, depends on how long you plan on keeping it of course but before Xubuntu 12.04 becomes end of life you'll most likely find that Xubuntu 14.04 is lilkely to be an LTS also :)

---

### Post by pnr2501 on 2013-01-06
I think thats a good piece of advice howefield. Leads to some more question tho.. :-D

Are there any differences between Ubuntu and Xubuntu regarding the installation?

I want to take a look at all the (common) desktop environments. I've read that its possible to install multiple desktop environments on Ubuntu and chose the one to use upon startup. Does that apply for Xubuntu aswell?

--> I mean can I install KDE on Xubuntu and then chose between KDE and XFCE?

And it is possible to use Unity (is it a Gnome??) on Xubuntu?

I chose the LTS version in the first place because JiuJitsu said that "LTS releases are always more stable". To be honest I'm not sure about how long I will use it tho. Could be between few days and few years. :-D

It will depend on my user experience within the next days. :o

---

### Post by howefield on 2013-01-06
> **pnr2501 said:**
> Are there any differences between Ubuntu and Xubuntu regarding the installation?

They are virtually identical, if you can install one, you can install the other.

> I've read that its possible to install multiple desktop environments on Ubuntu and chose the one to use upon startup. Does that apply for Xubuntu as well?

Sure, you can indeed.

You will end up with a mix of applications though, eg you'll have thunar file manager with Xubuntu and if you install KDE you will also have Dolphin, in  other words the menus will fill up with the default applications from each desktop.

> --> I mean can I install KDE on Xubuntu and then chose between KDE and XFCE?

And it is possible to use Unity (is it a Gnome??) on Xubuntu?

Yep.

Install them all and choose which you want to use from the login screen.

> I chose the LTS version in the first place because JiuJitsu said that "LTS releases are always more stable".

All releases are meant to be stable, however LTS (which stands for **L**ong **T**erm **S**upport) releases tend to be built using a more conservative base than non LTS releases and so one could/should reasonably expect to have fewer issues with them.

---

