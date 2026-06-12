---
title: "Why does Ubuntu have problems with hardware and windows never does?"
date: 2006-09-16
forum: General Help
---

### Post by cobbweb on 2006-09-16
Hi, 
   I have been using Ubuntu for abou a year and love it, im now 100% Ubuntu, no more Windows. My question is, how is it that if windows is installed on a labtop everything hardware wise works but if ubuntu is installed on a labtop, you have to mess around with configurations and installing the drivers ect. What I mean is, how is it that windows has everything set up like that and Ubuntu doesn't. Is it just a matter of people making the driveres to work for linux and Windows just has the man power to do it? Thanks, just a little confused.

 Cobbweb

---

### Post by aysiu on 2006-09-16
It's a little bit that--you'd be an idiot hardware manufacturer to not make a driver for Windows.

But the other thing is that Windows usually comes preinstalled on laptops. That means the manufacturer (HP, Dell, Sony, etc.) takes the time to make sure everything works with Windows and includes the necessary drivers.

If you buy a laptop with Ubuntu preinstalled, everything will work just fine: [http://www.system76.com](http://www.system76.com)

---

### Post by orb9220 on 2006-09-16
This has been covered many times. I am suprised you have not read about  these problems before. 

The short answer is manufactures hire programmers to write device drivers to make a profit. 

Hence since 70-80% users are windows user's then it makes sense to write drivers for Windows.

Why would I spend adtional money for 5-10% of the computer population and would  have to maintain a staff for upgrading driver and working out the bugs. 

It dosn't have a high enough profit margin to do so.

---

### Post by jmeadows111 on 2006-09-16
It is not accurate to say that Windows never has problems with hardware. Just in my own experience, I've had a DVD burner that caused repeated blue screens in Windows but never caused any problems in Linux. Also, I have an old cheap digital camera that just won't connect to any modern versions of windows (due to lack of available drivers) but works fine in Linux.

That being said, we need to do our best to keep the heat on manufacturers to either release Linux device drivers, or at least specs for other developers to write the drivers.

---

### Post by Lord Illidan on 2006-09-16
I often had probs with hardware on windows...which is astonishing...given its price and market saturation ;)

---

### Post by GStubbs43 on 2006-09-16
I actually have a lot more problems with Windows than Ubuntu. Have you ever installed or reinstalled Windows yourself, or just had it preinstalled? On Windows I have to install about 20 drivers, including Wireless, Audio, Graphic... etc... On Ubuntu I just need to install wireless and since I have widescreen, Graphics, if I had a regular 1024x768 screen, I would just need Wireless! :D

---

### Post by Littleweseth on 2006-09-16
That's actually quite true. Linux doesn't seem to require me to feed it six different driver CD's after a reformat - it Just Works™. That said, I've never had to install wireless and never used anything that required video drivers.

---

### Post by Ziox on 2006-09-16
For me I had to install about 5 or 6 drivers for my laptop in order to make it useable...it was such a pain in the @$$ when just scrolling through a word dorcument would use 100% CPU...On Ubuntu, everything worked...even direct rendering worked perfectly, without installing any driver...

---

### Post by IYY on 2006-09-16
I've seen cases where Windows couldn't detect anything and I had to install dozens of obscure drivers from the net, whereas Ubuntu worked perfectly. I've also seen the opposite, which you describe. Depends on the hardware.

---

### Post by Ramses de Norre on 2006-09-16
The thing that suprised me the most was that my sound card worked lots better with the default ubuntu drivers than with the preinstalled windows drivers.
It's an onboard card and in windows it seems to catch pretty much interferention from the electronics around causing pretty loud humming. This effect is a lot less in ubuntu (but still a little bit there).
It surprised me a lot to notice this but it's quiet nice ;)

---

### Post by Pumm4 on 2006-09-16
Ubuntu is the first Linux distro that has detect all of my hardware and everything I've plugged in - Working fast and beyond perfect.

---

### Post by bogoliubov on 2006-09-16
I agree with what the others have said. But another thing that really impressed me was when I upgraded hardware. I changed mainboard, CPU and memory and tried to start the computer without reinstalling; and it worked! Whenever I've done the same with windows, I've always ended up reinstalling, since things just "broke".

Of course, laptops are usually trickier than desktops.

I think that what might be annoying to people switching from windows is that in Ubuntu the managing of driver is very different and not very straightforward for the new user. On the other hand, I've only been fiddling with the Nvidia drivers; the rest "just works".


Btw; what's your impression on dual-core cpus in Ubuntu? Is the Linux kernel good at taking advantage of the extra cpu core? Is it different between AMD and Intel? I'm thinking on upgrading... :)

---

### Post by handy on 2006-09-16
It depends on the hardware... For both OS's.

I'm sure I read in the forums somewhere that a Ubuntu install, incorporates support for far more hardware than any of the windoze's do...

---

### Post by cobbweb on 2006-09-18
Part of the reason I asked the question is because my parents epson stylus 7800 printer/scanner doesn't work. Well the printing works, but the scanner won't work. I couldn't find the drivers or any help in getting the scanner to work. :( However I do program in c/c++ and java and would love to contribute in some way etc. Does anyone know how hard it would be to make a driver? or is it possible with licencing etc. 

 Cobbweb

---

### Post by kbuel on 2006-09-18
> **Ramses de Norre said:**
> The thing that suprised me the most was that my sound card worked lots better with the default ubuntu drivers than with the preinstalled windows drivers.
It's an onboard card and in windows it seems to catch pretty much interferention from the electronics around causing pretty loud humming. This effect is a lot less in ubuntu (but still a little bit there).
It surprised me a lot to notice this but it's quiet nice ;)

I had this problem too.  To fix it I muted the mirophone input and it went right away.

---

### Post by Tarvok on 2006-09-18
You know, I just realized that I had fewer problems installing Ubuntu onto my computer than I had installing Windows. NOTHING on this machine works in windows without going to a 3rd party driver CD (bunch of Dell stuff). The only thing that needed extra work in Ubuntu was that I had to change something in the BIOS to get the video card to work properly.

---

### Post by po0f on 2006-09-19
Linux does not like my motherboard.  Every live cd I have tried either does not boot for whatever reason, or requires serious kernel parameter magic to get booted.  And until I figure out how to turn off hardware module loading (or whatever that step is called) off in Ubuntu's boot process, all of my boots require my physical presence to ^C that step (I usually just leave my box on 24/7).  Windows had no problems whatsoever with this board.  (Of course, this is all due to a horrible BIOS implementation on Compaq's part, hoping to upgrade soon.)

Please don't get me started on printers.  I haven't tried to set up a printer under CUPS in a while, but the last time I attempted it, I had to try out two or three different HP drivers, and configure each of those mulitple times until I gave up.  Googled the hell out of it and figured it out eventually (long after the need for printing had passed; I used a friend's printer.  Under Windows).  Why are driver disks bad again?  Because they work?

My media keyboard's volume spinner works!  Yay!  The sixteen other buttons on it don't work!  Oh no!  Where's my driver disk??

Seriously, I like Linux as much as the next geek, but to say that you have less hardware probelems under Linux as you do Windows seems like bull to me.

[note] I will never move back to Windows, been using Linux exclusively for the past 3.5 years now.  But I have never witnessed the magical alignment of the planets that you people refer to as your hardware working right, ever.  Just thought I'd share my experiences.  [/note]

---

### Post by pppetter on 2006-09-19
Ubuntu is fantstic with drivers...the only thing I needed to fix was my printer, select what driver - and later type 710C in a configfile(this should be done automatically, and is a Bug, but not fixed yet) - not so hard really. Everything else just WORKS. I can even connect my mobilephone and transfer files...Just Plug'n'Play.

---

### Post by 3rdalbum on 2006-09-19
I'm running a Compaq computer right at this very moment, and everything really did just work. No kernel parameters needed, my Canon printer works fine (now that I've updated CUPS to the latest version), and on Windows I have a big hardware problem: It behaves as though my hardware is not capable of ripping a CD, downloading a file and playing MP3s at the same time. :-P

---

### Post by monktbd on 2006-09-19
> **cobbweb said:**
> However I do program in c/c++ and java and would love to contribute in some way etc. Does anyone know how hard it would be to make a driver? or is it possible with licencing etc. 


the hardest part to make a driver is to know the hardware.
the manufacturers rarely publish the hardware specifications or at least supply them to some interested devloper to develop some open source linux drivers.
so a lot of the drivers for linux that do not come from the manufacturer directly are developed by reverse engineering and spying on communication protocols when used in windows. that is a long and tedious process, error prone as well.
often it is also comparison of the parts of a device, e.g. for video card the bt 878 chipset is well known for years. so if a video card uses a bt 878 chip it is usually easy. but if there is a new chipset with different specs and protocols where no driver exists yet it gets difficult. 

keeping that in mind i find it absolutely astonishing how much hardware actually works under linux.

---

### Post by kick6 on 2006-09-19
> **po0f said:**
> 
Seriously, I like Linux as much as the next geek, but to say that you have less hardware probelems under Linux as you do Windows seems like bull to me.

I recently installed ubuntu on an old machine I had lying around.  This machine is a PII Xeon with junk harddrives, a riva tnt2 vid card (does anyone even remember those?), a tv tuner that I knew nothing about, and some old soundcard.

Ubuntu recognized everything.  I didn't even know what the tv tuner was (this machine was just given to me), but ubuntu had the driver.  I was utterly amazed.  It would have taken some major sluething to turn up drivers for the ghetto soundcard and no-name tv tuner if I had tried windows, and even then I would be limited as to what version of windows I could install.  turns out there are only 98 and XP/2000 drivers for this tuner.

---

### Post by bigken on 2006-09-19
wot a load of coblers I have had  loads of windows based machines and had to spend hours googling to find drivers to make hardware work in windows xp

---

### Post by cobbweb on 2006-09-20
can somone please kill this thread... thanks

---

