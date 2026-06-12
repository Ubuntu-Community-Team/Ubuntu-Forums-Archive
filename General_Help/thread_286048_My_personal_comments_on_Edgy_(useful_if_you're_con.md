---
title: "My personal comments on Edgy (useful if you're considering upgrading)"
date: 2006-10-27
forum: General Help
---

### Post by jamyskis on 2006-10-27
I was pleasantly surprised by Edgy. I'd been hearing all kinds of problems with it and even Canonical themselves were warning that if it is stability you're after, then you're better off with Dapper. Reviews seemed to be positive though and a new release of Ubuntu is always tempting. :mrgreen:

First, the upsides that really caught my eye:-

* The boot-up sequence just has to be seen to be believed. The new Ubuntu boot logo looks amazing, although you won't have much time to see it - Upstart (the new bootloader) has reduced startup time considerably. I do miss the rundown on what exactly is being loaded a bit, but it's not a major complaint.

* The new version of GNOME is a major improvement in terms of speed. Just run Evolution and call up your mail and you'll notice the difference.

* The new system of Add/Remove programs looks great and it is much easier to find the programs you're looking for, if you're a beginner. There is one catch though - see below.

* Firefox 2 rocks. OK, the default method of opening a new tab for a new window does take some getting used to, but you can change it back easily enough if you really want to, and if you take the time to learn working this way, it soon becomes better than working with individual windows.

* More of an advantage to Dapper than Edgy, but the process of upgrading using gksudo update-manager -c was one of the most professional and seamless things I have ever seen in a Linux distro.

As usual, there are some niggly points:-

* Briquolo and BZFlag seem to have lost their icons, and BZFlag was completely wiped from the menu. I had to manually enter the entries again, albeit without the nice icons. This led me to the second problem...

* ...the menu entry for Alacarte has also magically disappeared. The program is still there, so this is a minor point again, but I was used to working that way. True, you can click on the menu and select Edit Menus, but it took some unnecessary getting used to.

* Somewhat more seriously, easy access to Synaptic has completely disappeared off the map. The menu entry for directly accessing Synaptic (as opposed to clicking on the Advanced button) which seems to randomly reappear and disappear between releases is not present in Edgy, and there is no more Advanced button in the basic Package Manager. Some users may not be well versed enough to use the command line, but that is not to say that Synaptic is too difficult for them too.

* Anjuta 2 is still far too early to be included in a distro. True, Edgy is intended to be bleeding edge, but it breaks compatibility with Anjuta 1, which was a very stable and reliable IDE.

---

### Post by MattW on 2006-10-27
I've still got a Synaptic icon in System->Administration just like in Dapper before I upgraded.

I had to check though, I'm a bit of a command-line person when it comes to software installation. In any case, the upgrade didn't remove mine.

---

### Post by dpurple77 on 2006-10-27
Quick complaint... I just finished off a clean install and although everything went well as always, i really really hate not having the boot up and halt messages desplayed to me. It reminded me of windows xp in the worst possible way. I dont really care about the scrolling bar. It doesn't really do me any good. But i do care if everything goes the way it is supposed to or not. If anyone knows of a way to bring back the messages i would really appreciate the tip.

---

### Post by galileon on 2006-10-27
open a terminal,

sudo gedit /boot/grub/menu.lst

look for something like this:

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot


get rid of the 'splash'.....(thats the splash screen) if you want to see the kernel loading, remove the 'quiet' as well

---

### Post by PriceChild on 2006-10-27
Alacarte is still there... System>Preferences>Menu Layout

---

### Post by fragos on 2006-10-28
Also right click "Applications" and "Edit Menus" is an option.

---

### Post by jamyskis on 2006-10-28
I found the menu editor under System/Preferences - quite a change and not one I would have thought of. Oh well...

As far as Anjuta 2 is concerned, I'm really steamed about this - it is extremely unstable and regularly crashes on me just by importing a project or editing a text file. Worse, the dependencies for Anjuta 1 have been tweaked around so much that it is now impossible to install it from the Dapper packages. I've been forced to download the source for Anjuta 1 and install it from source which took a lot of time and effort :-(

Also, Screem seems to have taken a plunge in the stability department, as that randomly crashes on me too. Not only that, it seems to no longer recognise directories when working from an FTP directory, which is extremely annoying because I have a number of HTML files and images located in directories (so that it doesn't get too disorganised).

And there seems to be a problem with the window close signal in the GNOME libraries, as many programs don't react to the close icon or button when you open certain windows within the program, e.g. the About window. This has hit AisleRiot, Screem among others.

I'm wondering if Edgy is a bit too bleeding edge - I don't think it should have ever made it as a stable release.

---

### Post by Choad on 2006-10-28
My thoughts on Xubuntu are positive too

pro

- Applications menu has been cleaned up alot
- Some bugs in dapper are nowhere to be found here
- New software manager works beautifully
- Thunar now has trash support
- Better default background, theme and login screen
- faster boot process

con

- boot screen is ugly as sin, and doesnt tell you whats happening
- thunar was hidden away in "system" - hardly user friendly. had to make a launcher for that in the panel
- the top and bottom panels start off at a wierd size. too big to be useful
- firefox has a font rendering problem on the menus that needs sub-pixel hinting to sort
- changing sub-pixel hinting causes a bug in XFCE that needs a config file to have a line added
- firefox doesnt go back when u hit backspace, needs about:config mods
- gxine sucks (but so did the old one) VLC is much better!
- certain add-ons to the panel stretch it out stupidly

but hey, it kicks *** generally

also, general linux gripe - no support for my SiS graphics chip, so rendering anything maxes out my processor. firefox scrolls horribly. its a mirical VLC only uses about 40% of my cpu when fullscreen, as every other player can't even keep up the framerate

---

### Post by bleearg on 2006-10-28
Has anyone tested the wireless support?  Most specifically with EAP/TLS using certificates for authorization.  Never was able to get this to work on Dapper.

---

### Post by David A Knight on 2006-10-30
> **jamyskis said:**
> 
And there seems to be a problem with the window close signal in the GNOME libraries, as many programs don't react to the close icon or button when you open certain windows within the program, e.g. the About window. This has hit AisleRiot, Screem among others.

I'm wondering if Edgy is a bit too bleeding edge - I don't think it should have ever made it as a stable release.

In the case of screem it is because it hasn't really had much development over the past year, so hasn't kept track of any changes with GNOME.  I've not seen the about window problem in anything but screem for that matter.

---

