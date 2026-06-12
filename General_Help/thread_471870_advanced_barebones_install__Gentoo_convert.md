---
title: "advanced barebones install?  Gentoo convert"
date: 2007-06-12
forum: General Help
---

### Post by gnychis on 2007-06-12
Hey all,

I am thinking of converting from Gentoo to Ubuntu.  Gentoo's "build from scratch" methodology is starting to take its toll on me after 3 years, and I can't stand watching things build any longer.  Furthermore, one of my 4 machines is an old 800mhz laptop, that simply can't handle it anymore.

The thing is, I don't want to be tied down and restricted.  I don't know how much flexibility and control Ubuntu gives.  For example, when I install the system, I want a completely clean slate, with no Gnome, no Nautilus, no KDE... etc

I want to run FVWM with no desktop manager, and be able to install what I want.  Basically I'm not looking for click point install, and I end up in a Gnome desktop which is *great* for first time users, but not what I'm looking for.  When installing Gentoo, you start bare bones and emerge exactly what you want.  This is what i want.

Also, I want the package manager to be able to keep track of updates on everything *but* the kernel.  I like to build my own kernels.

I'd greatly appreciate any feedback.

Thanks!
George

---

### Post by Rui Pais on 2007-06-12
hi,
[here]("http://psychocats.net/ubuntu/minimal#barebones") is a nice suggestion for a minimal.

from that point you can install what you want.

---

### Post by notwen on 2007-06-12
Do a server install and apt-get install to your hearts desire. =]  I did this briefly when I setup a general file/web server and didn't want all the pre-loaded things.  I installed flux box and various other lightweight things when i did have need of a GUI.  Since you're a former Gentoo user, I'm sure you shouldn't have too many issues doing a bare bones install.  If you run into any bumps along the way post back. Good luck. =]

---

### Post by gnychis on 2007-06-12
awesome!  exactly what i was looking for, thanks!

I'm going to give this approach a shot on the 800mhz machine, see how it works out, then migrate the rest of my machines if i like it :)

will post back, i should be okay manually installing packages and figuring out what i nedd

---

### Post by digilink on 2007-06-13
Welcome to the world of Ubuntu ;) 

I switched from Gentoo in January of '05 on a trial basis and I just never went back! Gentoo is by every right a fine distribution, but I was tired of dealing with broken ebuilds, circular dependencies and other headaches. While I thought building everything from source with compiler optimizations was really cool, in the end I spent more time building software and fixing things than I did using it. 

Good luck with Ubuntu and let us know how you make out.....

---

### Post by Rui Pais on 2007-06-13
Btw,
just a tip (always nice for Gentoo newcomers).
One of the most different aspect from Gentoo is the boot process. 
Gentoo make things easier if one wants a light system. Ubuntu goes for everything one may need approach :(

An excellent app is sysv-rc-conf. 
That will easily allow to turn on/off from any level any service available. You can tweak a lot under Ubuntu too :)

---

### Post by moore.bryan on 2007-06-13
[I]not to toot my own horn, but...
[http://ubuntuforums.org/showthread.php?t=396390&highlight=openuntu](http://ubuntuforums.org/showthread.php?t=396390&highlight=openuntu)
[/I]

---

### Post by gnychis on 2007-06-14
just wanted to holler back

so i installed ubuntu the server way on my laptop, and i LOVE it ... it's exactly what i was hoping for, and everything works with far less pain than in Gentoo

for example, I was ready to go through the alsa pain, when I realized, oh... my sound already works

I plugged my x60s in to the docking station I had been trying to get to work for the past year in Gentoo, and oh... it magically works.  I literally have not had cd/dvd access on this machine because of that until now.

i went to install xorg and fvwm-crystal because its my prefered setup... and yeah, it took about 1 day less without compiling

if i said i was happy, it would be an understatement... i am truly loving this

---

### Post by Nythain on 2007-06-14
you dont have to use the server disc... the alternate install cd gives the option to install command line system only... from there you can edit your /etc/apt/sources.list and install whatever you want from the repos... granted the server disc will do effectively the same thing, but just figured id throw out my plug for the alternate iso

---

### Post by Rui Pais on 2007-06-14
> **Nythain said:**
> you dont have to use the server disc... the alternate install cd gives the option to install command line system only... from there you can edit your /etc/apt/sources.list and install whatever you want from the repos... granted the server disc will do effectively the same thing, but just figured id throw out my plug for the alternate iso

The problem is that with old boxes most of the time people have old hardware too.
Some cdwriters, old ones of course, have limitations of size of ISOs they can save. 
Mine, the bigger size it saves is ~680M :(

The alternate CD is one of the biggest (had too much things on it that one will never need...)
Besides that if the point is get a light DE why download an iso with a huge gnome inside?

feisty desktop iso = 692M 
feisty alternate iso = 696M 
feisty server iso = 492M
feisty mini iso = 8.4M (he, he, no calories)

The advantage of mini.iso (netboot install) is that is the same thing that alternate but you only download what you need. 
It has the same kernel, not the server one, offers the same choices for LAMP and DNS, but the alternate cd choices too for x/k/ubuntu (or any other one user wish)

---

### Post by shae on 2007-06-14
Do not worry about custom kernels in ubuntu.  When you install one, it is considered to be user-installed software and does not confilct with the ubuntu repository kernels.  After you are finished testing that the kernel is stable, you can remove the kernel installed by ubuntu and it's supporting files without a single problem.  Good luck with your install.  May I suggest installing gnome-core if you are interested in using gnome.  It installs the barebones of gnome for your pleasure.

//ot: what is your favorite patchset for the kernel?

---

