---
title: "Should Ubuntu run fast on my system?"
date: 2007-10-21
forum: General Help
---

### Post by Sabretooth on 2007-10-21
Thought I'd ask it, after a long while. I've been using Ubuntu as a dual-boot with XP for about 3-4 months now and I'm loving it. It's rather slow, however. I mean, it boots faster than XP and all that - its smooth, but rather sluggish in opening windows etc. Using Firefox is painful, with slight delays in opening pages, shifting tabs etc.

XP on the other hand, is a little slow (startup takes a few weeks, lol) but it runs very smoothly. Here are my system specs:

Intel Pentium III 1.2 GHz
nVidia GeForce FX  5200 w/ 128 MB RAM (drivers installed)
512 MB RAM
10 GB Ubuntu drive w/ 80 GB XP Drive (both at 5200 RPM, I think, not sure)

I'm using Gutsy right now, with Compiz Fusion (which runs much faster and stabler than previous builds!) having many effects on, but not overloaded. But I've found this sluggishness in Feisty as well.

---

### Post by PmDematagoda on 2007-10-21
It should run faster, but I believe 10Gb may not be enough for Ubuntu if you are using it extensively.

---

### Post by MegaSvensk on 2007-10-21
How does it work without the desktop effects enabled?

Also, you might want to try using Xubuntu (sudo apt-get xubuntu-desktop.) Xfce uses a lot less resources than Gnome. Although the regular Ubuntu really shouldn't run that slow on your machine. Maybe someone with more knowledge of this stuff will reply and help you get it running smoothly.

---

### Post by PmDematagoda on 2007-10-21
How much swap space have you given Ubuntu?

---

### Post by kellemes on 2007-10-21
Well, all those nice Compiz-effects XP doesn't offer :popcorn:
You don't have a bleeding-edge rig so I guess you have to ditch some effects sooner or later..
Like one of the previous posters I can also point to other windowmanagers, have you tried e17? Pretty damn cool!

---

### Post by dcstar on 2007-10-21
> **Sabretooth said:**
> Thought I'd ask it, after a long while. I've been using Ubuntu as a dual-boot with XP for about 3-4 months now and I'm loving it. It's rather slow, however. I mean, it boots faster than XP and all that - its smooth, but rather sluggish in opening windows etc. Using Firefox is painful, with slight delays in opening pages, shifting tabs etc.

XP on the other hand, is a little slow (startup takes a few weeks, lol) but it runs very smoothly. Here are my system specs:

Intel Pentium III 1.2 GHz
nVidia GeForce FX  5200 w/ 128 MB RAM (drivers installed)
512 MB RAM
10 GB Ubuntu drive w/ 80 GB XP Drive (both at 5200 RPM, I think, not sure)

I'm using Gutsy right now, with Compiz Fusion (which runs much faster and stabler than previous builds!) having many effects on, but not overloaded. But I've found this sluggishness in Feisty as well.

Another 512MB of RAM would help, but that could be quite expensive these days for a PIII motherboard - and the CPU will still struggle to handle the load.

That hardware is really (really) old, you cannot really expect it to handle the current GUI demands of any O/S.

---

### Post by LanDan on 2007-10-21
just a guess,

but try to look up the models for those 2 disks and search google for some benchmarks, don't underestimate disk speed cause it might make a huge difference

p.s.
if you ask a question like this people will always recomend you a different desktop environment ;)
personally i always go with Xubuntu, especially on specs with yours

---

### Post by PreviousN on 2007-10-21
I know that idealists will blast me for this..but the disk size makes a huge difference. Think of it this way: 

Data is packed tighter on the 80 gig drive. Thus, even though its the same rotational velocity, it will be able to read and write a lot faster due to the fact that it can sling around more bits faster. It has to. It is the same physical dimensions. 

Lastly, a 10 gig drive is likely OLDER compared to an 80. Even though they may rotate the same speed, the drive head may move slower and it may be less efficient. 

Sure, windows managers help...but why don't you just go out to a junk shop or plead with your local nerds for a spare hard drive.

---

### Post by Sabretooth on 2007-10-21
Like I've said, Ubuntu runs sluggishly even without Compiz, so Compiz doesn't make too much of a difference. I'm not sure about the swap space, though. How do you view/change it?

Yeah, I know I need a new rig and all but Dad ain't giving me one. :( Keeps telling me to wait, although I've waited a good year and a half. I'm going to start a rebellion one day. :p

Nah, I'm cool right now with the Desktop Environment. Its not unusuably slow, just sort of disappointingly slow. I just wanted to know if I should expect sluggishness on my system with those specs or whether it should be running perfectly...

---

### Post by PmDematagoda on 2007-10-21
You can find the amount of swap space in System Monitor>Resources.

---

### Post by Sabretooth on 2007-10-21
Okay, I have 462.8 to Swap. Right now I'm running Firefox, Exaile, Pidgin and System Monitor (Compiz-Fusion on) and it shows me:

42% Memory Used
0 % Swap Used
CPU is fluctuating anywhere from 10% to 100% in a rhythm (its almost like a cardiograph! :p )
My 10 gig drive is 28% full, 80 gig drive is 79% full.

---

### Post by PmDematagoda on 2007-10-21
Very strange that the CPU should be fluctuating like that, that could be the main reason, could you post what processes take up the most power?

---

### Post by LanDan on 2007-10-21
lol ;)

probably the "system monitor" is taking up the most resources ;)

---

### Post by Sabretooth on 2007-10-21
Okay, Memory-wise, here are top guns:

firefox-bin: 44 MB
python: 23.1 MB
compiz.real: 18.1 MB
pidgin: 9.4 MB
gnome-panel: 9.1 MB
nautilus: 8.1 MB
emerald: 6.0 MB

The rest are are below 4 MB

Here's CPU-wise:

Okay, because of the fluctuations, its difficult to point down things. System monitor is taking up 10-15% mostly.

python: around 9%
firefox: 4-14%
compiz.real: 0-5%

All the rest are at 0%, but things are wildly jumping up and down in the top 10. I'll get a screenshot of the "Resources" tab if anyone wants?

---

### Post by PmDematagoda on 2007-10-21
Yes, it would be better to have a screenshot of your system monitor.

---

### Post by LanDan on 2007-10-21
system monitor always gives a twisted view on CPU usage, try the top command in a terminal for a cleaner picture.

my opinion,
1st probably your hard disk is your bottleneck, upgrading that one would give you the best performance boost

2nd using something lighter then Gnome could leave some extra RAM for your applications like Firefox, making them snappier  when using or starting up for the second time.

---

### Post by Sabretooth on 2007-10-21
Okay, here are the screenshots. I'll try top meanwhile.

Top:

Things are fluctuating a bit in Top as well. Python is eating around 9% of CPU, Xorg is jumping from 0 to 2 to 20, firefox is roughly around 11% and the rest are generally below 3%.

---

