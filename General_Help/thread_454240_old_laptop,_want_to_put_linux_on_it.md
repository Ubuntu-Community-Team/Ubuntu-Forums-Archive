---
title: "old laptop, want to put linux on it"
date: 2007-05-25
forum: General Help
---

### Post by codyr on 2007-05-25
i have a really really old laptop, it has a cd player and floppy, no usb ports.
it has a 2 gb hard drive and 32 mb of ram

i was gonna put xubuntu on it but it still does not have enough ram to run the live cd, so i tried DSL, and that requires 64 mb of ram...

i cannot really find anything else on it, it came with win98 but it has a lot of problems, someone tried to clean it and deleted a bunch of system files, i have a win98 cd just dont have the key thats on the laptop.

is there any os i could put on it preferably linux that would work, also i heard about alternative cds that work better with really old computers, would that work for my laptop?

---

### Post by scrooge_74 on 2007-05-25
Puppy linux or Damn Small linux are your best options for this laptop, bot are Debian base

---

### Post by Daniel_Walker on 2007-05-25
It depends what you would want to do with it, really, and how deep you want to go. The simple answer would be too simply try to beg, borrow or steal some extra RAM - upto the point where an OS, that you are familiar, with will run. Dozens of Freecycle users may live, within walking distance of your house, with old broken down, or unwanted laptops that could be butchered and broken up, to expand your aging system. I did this, recently, and actually ended up using some of the bits from the computer I had *originally* intended to install my system on, to beef up the much nicer Toshiba Satellite, I was given as a result of putting a Want-ad on Freecycle :).

Getting further under the hood (which is what the rest of this reply deals with), you could (if you wanted) reduce the amount of resources your system needs to run itself, in quite radical ways, by compiling a custom kernel. This sort of thing is almost never worth doing on a modern system, simply because the efficiency of the machines is so great, that *'the gain isn't worth the candle'*:). However, on an old system, it may be worth considering.

Why would playing with sourcecode and a compiler help, on, say, an old Pentium II, then? you may ask.

Well, notwithstanding the resource-usage of (for instance) modern desktop software, a deeper problem with today's systems lies in the fact that moderen operating systems contain great swathes of functionality to support hardware that just didn't exist in the days of Windows 98 computers. Much of this isn't actually used, in any one hardware installation, which is why fans of 'monolithic Kernels' (where the entire operating system kernel is loaded at boot time, and remains in memoiry, all the time, until shut-down) like to compile their own custom kernels. (Please bear with me, here - I am, to some extent, one such fan, when it comes to older PCs).

In a monolithic kernel,removing support for hardware, that your system will either never contain, or will never use (even if it *is* there), is obviously a **Good Thing**, since it will make a permanent improvement to the amont of memory the system uses, by reducing the size of the core operating system.

All well and good, you say. Why don't we all do that?

Well, the truth is, that in a standard installation, modern PC operating systems like Linux, FreeBSD, etc., make use of a 'monolithic microkernel' model, whereby the basic kernel loads into memory, and then loads and unloads exterior sections, of additional kernel functionality, as and when they are called upon.

This is good, in reducing memory footprint. However, hotswapping kernel functionality also carries it's own overhead - one which can become noticable, on an oldewr system. Thinking of our old laptop; if you knew which parts of your old laptop's (probably quite limited) hardware, you were ever going to use - and were fairly certain that you'd be using it, pretty much all of the time that it was switched on - there could well be an argument for compiling a monolithic kernel, in which great swathes of kernel functionality had been removed, because you knew you'd never use it - while the rest remained available, for immediate use.

If I was to recomment an operating system to do this (perhaps quite daunting) process on, it would probably be FreeBSD, simply because that's what I use, in these situations. Here, the Kernel compilation process is controlled by one, human-readable, Kernel configuration file, which contains fairly extensive comments describing what each compilation option covers. You add or remove sections of kernel functionality by commenting or uncommenting each line of support - while making reference to the online FreeBSD manual, to help understand which particular parts of the last *thirty years*, of computing, you blithely writing out of your kernel's skill-set :).

It doesn't have to be new kit, that gets the chop, either. For instance, your laptop probably has an old fashioned line printer port on the back of it: you'll never use it (in fact, you probably don't even have a printer that you could plug into it). However, a vanilla instal of any OS that came straight off a disc, would diligently try to support that port - *simply because it was there*. Answer? Comment it out - *Line printing? What's that?* And what's with that built-in 56Kbip modem? This is the broadband era, man! Do you really need that PCMCIA slot? How much easier it would be, if we didn't have to think about hot-plugging...?

You get the picture, I'm sure.

Start by just loading a simple stripped down OS, without a desktop. Work on the command line, using 'e' the FreeBSD editor, and follow the steps in the online manual. Edit your kernel.config file, to produe your new, lean, mean, super-narrowly-minded kernel, and recompile. Follow the steps in the manual to switch your bootloader to point at the new kernel, and, making sure you have taken all the necessary steps to ensure the next bit goes moothly, reboot. Now you can begin thinking about downloading and installing extra software like a desktop, etc.

FreeBSD ins't the prettiest softweare in the world, to install, but it is fairly straightforwad (mostly because it is even more conservative than Debian ;)).

So, in summary: it all depends how much, resurrecting this old laptop means, to you, and how much of a geeky sense of personal achievement, you will optain, when KDE finally loads on your new/old super-lean custom-built, saved-from-the-skip, ' Womble' computer.

I recommend FreeBSD, simply because it was what I used, the first time I did it, and what I've used ever since, in these situations. Others may have other OSes that they have had good mileage with.

---

### Post by RedSquirrel on 2007-05-25
DeLi Linux might be worth a try. 

[http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/)

---

### Post by floke on 2007-05-25
You could try the Xubuntu alternative installer (non-Live CD).

---

### Post by reclusivemonkey on 2007-05-25
Without a GUI, it will run just fine.

I've run Slackware on many a machine without X, and it never got anywhere near using up 32 megs of RAM.

---

### Post by RedSquirrel on 2007-05-25
> **Steve.K said:**
> You could try the Xubuntu alternative installer (non-Live CD).


On 32 MB of RAM? The Xubuntu website suggests 64 MB is the minimum and strongly recommend 128 or more...

---

### Post by mdg on 2007-05-27
Codyr,
I have an old IBM Thinkpad, 166 Mhz with 2 Gig HD and 64 MB (I upgraded from 32 mb).  Before I added those 32 mb of ram, I was able to run Damn Small Linux pretty well - Firefox was really slow so I got Opera.   It works really wonderfully with console programs like Elmo for e-mail, and elinks for text browsing.  This was with a frugal install so I could use the newer programs.  In DSL 3.1 or higher you can add programs that have a ".unc" or ".uci" extension.  These are programs that are made into an image file and given that extension.  Then to use the program, you "mount" the file system (just like .iso").  These program get by on a lot less ram.  You won't be able to use something like OpenOffice, but you might be able to pull off Abiword.  Firefox is a bit hefty, but you could try Opera or seamonkey.  Dillo browser is very fast if you want a GUI environment, but you won't be able to check webmail and such with it.  I am able to listen to CDs and webradio, view images, send e-mail in Syphleed.  Depending on what you want - more flash or more function, you should be able to find a nice combination that works on this old laptop.

There are lots of good tutorials on how to get DSL on your harddrive.  I would highly recommend setting up a swap partition that is two times RAM (i.e., in your case 64 MB).  Oh, you can tell how much ram is being used as a program called torso runs by default giving you info about ram, swap and harddrive space.  You will really learn a lot about Linux by starting with DamnSmallLinux.

By the way, you probably have PCMCIA slots - you can buy a compact flash card adapter for that slot so you can save files, pictures, emails, etc to it.  You can also get another compact flash adapter that plugs into a USB port on a newer computer so you can transfer files, etc. between the two.

Hope this helps, and happy linux computing!  :)

---

### Post by regomodo on 2007-05-31
> **codyr said:**
>  so i tried DSL, and that requires 64 mb of ram...

No it doesn't. I know as i've just been playing with DSL and DSL-N on my ancient lappy

@ Idle

DSL uses ~20MB of RAM
DSL-N uses ~18MB or RAM

---

