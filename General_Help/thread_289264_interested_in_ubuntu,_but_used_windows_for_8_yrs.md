---
title: "interested in ubuntu, but used windows for 8 yrs"
date: 2006-10-30
forum: General Help
---

### Post by noktekniq on 2006-10-30
so recently i have enjoyed the life of computers as i age from my teenage years to college/adult years. i have started learning more about computers since high school years, from installing an OS to building my own computer, then to overclocking. But here is the thing, those were all window based systems. 

i have recently been introduced to linux in college computer class.  my professor showed me ubuntu and told me to try it out for about 35 mins. and so i did. after doing so, i realized it looks cooler and much better then windows. from then i have been interested. 

i've never had the courage to download ubuntu and install it at home yet. so i have a few questions that i turn to in the forums. 

1. is ubuntu easy to use? for example is it easy to navigate and install programs just like windows or do i have to type long path of codes in order to execute the installation?
2. i have a a64 amd comp right now with 2gb ram and a 7800gt graphix card. is it possible for my to install nvidia drivers for my graphix card?
3. also, how would i install stuff like printer and other stuff like it?
4. i have a server up and running that is window based. is it possible to easily share folders over ubuntu then as in windows? can the network run correctly? 
5. i have drivers that i run for my motherboard and such, how do i install those? would i need it?

those are general questions.

---

### Post by blind0wl on 2006-10-30
Ok, theres heaps to read online in regards to Linux and the pros and cons.  You really should install it at home and play with it. As an example once you have it installed, set yourself some challenges..like finding out how to see a windows share (see samba for further details), how to read/write to that share and how to create your own shares.use the search function in the forums and ask questions.  Or read [http://www.ubuntuguide.org]("http://www.ubuntuguide.org") for more info.

Programs are easy to install, aptitude is a very easy program to use, and unlike Windows, you can install any application thats available to linux via one program.

You can get nvidia drivers for your card, there are plenty of howtos on the forum on doing so

Dont worry about the drivers for your motherboard, windows needed them to interface with it correctly...Ubuntu should do that for you.

Give it a go, it cant hurt, just make sure your armed with the information you need before dual booting and such on your home PC if you do install it.  Or get another PC together and run it to just get used to the ins and outs.

Welcome to the land of no sleep..hehe

Cheers

Blindy

---

### Post by noktekniq on 2006-10-30
so does this mean that anything i bother to install would not require a bunch of codes that i have to type?

i'm so used to windows, i have a lot of wonders when it comes to linux/ubuntu

---

### Post by autocrosser on 2006-10-30
I'm a old-timer--used Unix systems back in the 70's & then went to windows (3.1:-k)--from there I went to the Mac OS & looked at Linux every couple of years--I made the switch when Ubuntu came out (Hoary Hedgehog!!) & have never looked back--am running a Intel Pent D 840 with about a year or so old set-up---no problems with almost any of my system (HP 4370 scanner is the stand-out & we now have a beta driver for it)--Do a Dual-boot & ease yourself in--you won't believe the difference!!

---

### Post by blind0wl on 2006-10-30
If you use the GUI aptitude, you wont have lots of codes to type in...but that doesnt mean you dont need an understanding of how it all works...sometimes Linux just isnt as easy as Windows and requires quite a bit of troubleshooting.

You should have an understanding of what does what, kind of like knowing how to use DOS under Windows...they are basic's that give you a foundation for learning about your system

---

### Post by lancecasual on 2006-10-30
I am someone who has been trying the switch to "Linux" on and off for the last 8 years so I might have some insight for you.

Edgy is *extremely* close.  However, I still find myself needing to drop to the command prompt more often than not.  I'm quite comfortable with the command prompt at this stage in the game so I am confident that Edgy will replace Windows on my home desktop (the wife still has a Windows laptop).

That said, here's what I suggest:

Get an extra hard drive and stick it in your system.  Use the BIOS setting to cause the system to boot from this hard drive (unplug your current one just to be safe).  Then install Edgy and start tinkering.  Once you've got it up and running, plug in the old hard drive and use the BIOS to swap boot devices so that you can go back to Windows in an instant.  You *will* require Windows if you aren't well versed in the command line.  After you've broken and repaired Edgy a few times, you'll either start to become accustomed to the nuances and stick with it, or you'll run.  This is proportional to the amount of free time that you have.

But breaking it is good because it is the only way that you'll learn.

Now that Edgy isn't painted with mud (there's more orange in there than brown), it is tolerable.

GRIPES:

1) During the course of following instructions, I'm constantly pasting between the browser and the terminal.  Can we just get some sort of downloadable package script to replace this process?

2) Add a freakin' SUDO button to the file browser, which is worthless when you can't move files around because you don't have proper permission.  Or at least prompt for a password instead of telling me that I've got to open the terminal YET AGAIN.  Cheese and rice...

There's more... I just won't push it.  If I could get these two wishes, I'd be a happy camper.

---

### Post by noktekniq on 2006-10-30
i'd have to try to look for a spare harddrive to run on.

---

### Post by Charles Hand on 2006-10-30
> **noktekniq said:**
> 1. is ubuntu easy to use? for example is it easy to navigate and install programs just like windows or do i have to type long path of codes in order to execute the installation?
2. i have a a64 amd comp right now with 2gb ram and a 7800gt graphix card. is it possible for my to install nvidia drivers for my graphix card?
3. also, how would i install stuff like printer and other stuff like it?
4. i have a server up and running that is window based. is it possible to easily share folders over ubuntu then as in windows? can the network run correctly? 
5. i have drivers that i run for my motherboard and such, how do i install those? would i need it?



1. One thing easier about installing Linux applications is you don't have to pay for them.:-?  Well, lots of things you don't have to pay for. Anyway, Ubuntu has a built-in application downloader/installer thingy with search capability. Very easy.
2. Definitely Ubuntu supports Nvidia cards well. I think mine is 7600gt.
3. Printers are very easily managed in Linux/Ubuntu these days, via the "Cups" system.
4. You can share files/folders/printers back and forth with Windows using Samba. I think it's comes pre-installed in Ubuntu, but if not it's easy to install and configure (you sound like you're accustomed to doing some work under the hood).
5. Ubuntu these days, it just looks around at your computer and loads all the appropriate drivers like magic. Sometimes there are problems, naturally. Wireless networking cards are sometimes problematic. But there is an NDIS wrapper which allows you, if all else fails, to use Windows network adapter drivers on Linux.

And as has been said, you can always dual-boot for a while in order to build your confidence. I think Ubuntu can read and write NTFS filesystems pretty well now, so you can share your data between the two. Or you can share data between Windows and Ubuntu via a Fat32 file system. But honestly, I didn't keep my windows partition very long. Within a month I was completely on Ubuntu.

---

### Post by d3v1ant_0n3 on 2006-10-30
When I first started using Ubuntu (well, Linux in general), the terminal scared the beejesus out of me. You'll find that 90% of the time, there are GUI programs that will do the job for you instead of having to get your hands dirty. But on forums, etc, it's much easier to follow 'copy this into terminal' instructions, than trying to explain where to click on a GUI.

I actually find, after a few months of use, that I actually prefer using terminal to do things- It's generally faster once you're used to the commands. And it all slowly starts to make sense.

I'd give the live cd a try, see how it detects your hardware.

And most of all, don't expect Ubuntu to behave like Windows. It's not windows.

---

### Post by gargoyle on 2006-10-30
noktekniq you sound like you brain is turning into stone.
[B]     
interested in ubuntu, but used windows for 8 yrs [/B]

I am a fairly new uses of Ubuntu, however I have dealt with a few other versions of Linux.
I do have to say that Ubuntu has been the friendliness of the all.
Do not get me wrong it is not 100% user friendly but it is getting there.
Linux and Window share some thing but many items are forgein and only found in Linux operating systems.

You must be willing to spend some time in learning the in and out of it.  I am sorry to say if you do not put any effort in to it you will not get it.

Problems you might expect to run into
[LIST=1]
[*]How do you connect to the Internet?
[*]Modem? Wireless? , NIc ? Each of these can pose some problems.
[*]Do you want to watch DVD? This is not enabled by default.
[*]There  is not ** Internet Explorer**. Firefox is default browser.
[*]Not all programs are polished as window.
[*]So programs only run under command line.
[/LIST]

If you have an older computer sitting around why not load Ubuntu on to that and play around with it, that is what I am doing.

I have been using computer since Texas instruments made the TI94a and you hand coded in the computer program because there was not commercial programs yet.

So if I find Ubuntu to be fairly user friendly then I believe it is.

Good luck.

---

### Post by noktekniq on 2006-10-30
not quite a stone brain yet, but ti's getting there... 
i'm gonna download ubuntu via bt or something. what is the difference between regular cd iso and dvd iso?

---

### Post by Coelocanth on 2006-10-30
> **noktekniq said:**
> 
1. is ubuntu easy to use? for example is it easy to navigate and install programs just like windows or do i have to type long path of codes in order to execute the installation?
2. i have a a64 amd comp right now with 2gb ram and a 7800gt graphix card. is it possible for my to install nvidia drivers for my graphix card?
3. also, how would i install stuff like printer and other stuff like it?
4. i have a server up and running that is window based. is it possible to easily share folders over ubuntu then as in windows? can the network run correctly? 
5. i have drivers that i run for my motherboard and such, how do i install those? would i need it?

those are general questions.

1) Very easy. I'm an old gaffer that used nothing but Windows and have been able to learn Ubuntu with relatively little pain. There is a learning curve, but it's not too bad if you're willing to do some research.

2) My box has an Athlon 64 3200+, 1 GB RAM, and a 7900 GTO card. nVidia drivers installed, no problems.

3) Should be no troubles. There are some printers that have problems, but most are detected easily and 'just work'.

4) Can't answer this one, sorry.

5) Probably not needed. I didn't need any extra drivers for my mobo.

The great thing is you can try the live CD without installing the OS on your box. Play around with it for a while, then go for a dual-boot if you like what you see. It's a fun OS, and well worth the time to get to know it. And you can always ask here for help. People here are very willing to lend a hend if you need it.

---

### Post by songo on 2006-10-31
> **noktekniq said:**
> 
1. is ubuntu easy to use?
someone here in the forum has on his signsture that win is easiest than linux as doing it on your pants is than go to the bathroom. that's the best description that i've seen! let's say that isn't easiest but is more cleanear.

> **noktekniq said:**
> 
those are general questions.
take this as a complement: if those are general questions you'll be just fine. welcome!

> **lancecasual said:**
> 
2) Add a freakin' SUDO button to the file browser, which is worthless when you can't move files around because you don't have proper permission.  Or at least prompt for a password instead of telling me that I've got to open the terminal YET AGAIN.
true!

---

### Post by cotcot on 2006-10-31
The point 6 from the previous poster is to be corrected. Replace "So programs ..." by "Some programs ..."
Most of them you start like you do in windows with an icon on a desktop.

Do not forget that linux distros are very well supported by forums. These are all people encouraging you to try linux for an enough long period BEFORE judging about linux. A try is more convincing than a talk about. 

First step is playing around with a LiveCD before installing. That shows you how good your hardware is recognised.

---

