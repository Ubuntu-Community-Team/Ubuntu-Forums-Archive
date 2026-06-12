---
title: "Linux help for old upgraded machine project...slow!"
date: 2007-09-05
forum: General Help
---

### Post by crzyakta on 2007-09-05
Ok here is the problem...

Trying to install Xubuntu 7.04 on an older Packard Bell Machine, that is vastly upgraded, just for fun/learning

The machine:

Packard Bell PB600 motherboard (VLSI Wildcat chipset), has 3 busmastered PCI slots and 3 ISA slots
120MHz Pentium 1 (80MHz x 1.5)
128MB EDO RAM (at 80MHz)
SB Live! PCI
CMD 0649 ATA100 PCI card
40GB 7200 RPM WD hard drive (on ATA100 card, primary master)
DVD Burner (on ATA 100 card, secondary master)
Netgear EA201 ISA NIC
Onboard Cirrus 5430 PCI video (I replated it with a Voodoo3 PCI and a Cirrus 5449 PCI, but both cards show the dreaded unable to load V_Bios...because apparently onboard doesnt disable completely)

PCI bus is running at half FSB (80MHz / 2 = 40MHz)...this is an old Socket 5, that I hacked to run the higher/faster FSB (PLL trick)

I am new to the linux realm...and it took long enough to get this machine working (runs Win98 SE on dual boot very well)...but Xubuntu is SLOW SLOW SLOW!

I have disabled ACPI (acpi=off in grub) because my comp doesnt do ACPI, also tried the 'IRQPOLL' trag with it, but that didnt make a difference...it takes like 4-6 minutes to load, and when it starts, it is SLOW!!!

video, hard drive is barely responding apparently...2D blit drawing etc is VERY slow, like no acceleration, it feels like the CPU L1 cache is off and that the video is in software mode...all my searching says that the Cirrus 5430 PCI is supported in linux...but it doesnt feel like it at all...anyone know a way I can save the boot logs etc and maybe show you guys to get a tip on what the heck is goin on during boot that is making it so slow (is this dmesg etc)?  perhaps the CPU L1 is getting shut, or the IRQs are gettin screwed up making all PCI tasks slow (ie video, ide controller)

PS onboard IDE is disabled (the buggy CMD 640x), but upon boot up, linux sees it during the command line boot

thank you, any help is appreciated greatly...I would love to get this started, its been bugging me and put off at times for months!

---

### Post by SOULRiDER on 2007-09-05
I dont know if its a good idea to run Ubuntu in there. I would suggest other distros like Puppy or DeLi but maybe others like Arch will be just as good.

---

### Post by Kowalski_GT-R on 2007-09-05
hi crzyakta,


you are trying the same experiments as me :)

Xubuntu alternate on a P166 with 64Mbs is almost unusable, even if you install from the command line and try to keep it lean, with the bare minimum.

I'm afraid Xubuntu (XFCE desktop environment) is not as light as you (and I) expected.

Check out what I've been sayng tonight with kerry_s:

[http://ubuntuforums.org/showthread.php?t=543802]("http://ubuntuforums.org/showthread.php?t=543802")


might be of help....

ciao

---

### Post by crzyakta on 2007-09-05
Hey Soulrider,

Its actually Xubuntu (alternate install)

hey Kowalski,

Glad to see a old hardware hobbyist...how slow is your PC?  because this is ridiculously slow, like how Windows XP Pro might run (maybe slower)...I am thinking of putting a AMD K6-3 @480 MHz in there (with a Powerleap adapter)...but need to see that it gets decent speed...I honestly think something incorrect is happening....anyway I can check, and maybe post the log on here?

Thanks!

---

### Post by K.Mandla on 2007-09-05
> **crzyakta said:**
> Trying to install Xubuntu 7.04 on an older Packard Bell Machine, that is vastly upgraded, just for fun/learning ...
Unfortunately, Xubuntu is going to be very slow on that machine. It's a common misconception that Xubuntu is much lighter than Ubuntu or Kubuntu -- it's lighter, but not by much. Even the developers don't call it a lightweight distro any more.

Try Damn Small Linux if you can, or Puppy Linux. Both of those are exceptional distros for ultra-lightweight machines like yours.

You might also look into DeLi Linux, or perhaps even a minimal Ubuntu or Debian installation. I tried that once about a year ago, with a 120Mhz machine, and the results were mixed. 

[http://ubuntuforums.org/showthread.php?t=259901](http://ubuntuforums.org/showthread.php?t=259901)
[http://ubuntuforums.org/showthread.php?t=294292](http://ubuntuforums.org/showthread.php?t=294292)

It can be done, though. ;)

---

### Post by Kowalski_GT-R on 2007-09-05
I'm sure other experts can examine your log to check for something unusual.

Xubuntu alternate on my 166 (now 233MMX) was really, I mean, really, slow: so, same experience here.

If Win98SE ran well, than the circle tightens....

try an Ubuntu server installation, and build it up from there.......
.....

...


..


.then let me know how it goes:biggrin:

i'm really interested in the results, as I will have little spare time until next week...

ciao,

Andre

p.s. I think Damn Small Linux or Puppy Linux (or Fluxbox) can sort you out with little fuss....but that's another story: I'm also fairly new to Linux and want to learn too...

---

### Post by Kowalski_GT-R on 2007-09-05
oh,

you might also want to read this:

[http://ubuntuforums.org/showthread.php?t=478237&highlight=crappy+old]("http://ubuntuforums.org/showthread.php?t=478237&highlight=crappy+old")


lots of like-minded people, this forum is great :cool:

ciao

---

### Post by crzyakta on 2007-09-06
awesome link!  19 pages of machines...not much trouble shooting, but its good to see how slow systems fair...still have to go through the rest of it

one thing caught my eye, some1 running ubuntu server and i think fluxbox over it...is fluxbox the same thing as xfce?

also how do I take a snapshot (or save it where I can retrieve it) of my boot log?

thanks!

---

### Post by Warren Watts on 2007-09-06
Wolvix Cub or Arch Linux are two other lightweight alternatives as well...

I have Wolvix Cub installed on a 256MB 700MHz system and it runs considerable faster and smoother than Ubuntu on the same box.  

In fact, I am considering wiping the Ubuntu partition completely and switching the box over completely to Wolvix.  The only thing stopping me is the fact that Wolvix is Slackware based, and adding/removing packages isn't nearly as painless as it is with Apt in Ubuntu...

---

### Post by crzyakta on 2007-09-06
Isnt Xubuntu alot faster than Ubuntu though?

---

### Post by crzyakta on 2007-09-07
bump

---

### Post by Pumm4 on 2007-09-07
> **crzyakta said:**
> Isnt Xubuntu alot faster than Ubuntu though?
Yes it is, but I would skip the word "alot" though [IMG]http://www.mysmiley.net/imgs/smile/winking/winking0050.gif[/IMG]

---

### Post by raul_ on 2007-09-07
You should take a look at this thread, and at some of the (working) solutions posted there for old computers

[http://ubuntuforums.org/showthread.php?t=478237]("http://ubuntuforums.org/showthread.php?t=478237")

---

### Post by crzyakta on 2007-09-13
How do I take a snapshot of the boot log so I can post it up here?

Thanks

---

### Post by Stan_1936 on 2007-09-13
Just use a camera.

---

### Post by crzyakta on 2007-09-15
Ok, where do I locate the boot log then?

---

### Post by RedSquirrel on 2007-09-15
The boot log can be saved to a text file by running this on the command line:

```
 dmesg > dmesg.txt
```

Then you can just paste the contents of the text file here.

Have you tried some of the other suggestions for that old machine? Xubuntu is too heavy for that hardware.

Here are some links for the minimal install of Ubuntu, but even that might be too much:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

