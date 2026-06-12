---
title: "xserver fails"
date: 2007-12-01
forum: General Help
---

### Post by oeolycus on 2007-12-01
I started by installing the Ubuntu minimal CD and then following [this guide]("http://www.psychocats.net/ubuntu/minimal"). Everything was functioning perfectly until (I think) I installed xfonts-artwiz through synaptic. Upon the next reboot, I met with an error screen after GDM failed to start. It read:

> Failed to start the X server [...] Would you like to view the X server output to diagnose the problem.

Inside of that I can't really tell what's going on, but these errors stand out:

```
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from the list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from the list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from the list!
Fatal server error:
could not open default cursor font 'cursor'
```

I tried reinstall, remove, and install (after a purge), but none seems to fix the problem. When reinstalling, I see this error:

```
warning: /usr/lib/X11/fonts/100dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/100dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
```

Then later, after "Updating catefory cid.."
```

warning: /etc/X11/fonts/X11R7/Type 1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /etc/X11/fonts/X11R7/Type 1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

```

The tail end of the output after "startx" reads:
```
 XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
```

Any help will be greatly appreciated. **NB: all errors have been hand-typed by me so there may be typos.**

---

### Post by PmDematagoda on 2007-12-01
Could you post the specifications of you PC.

---

### Post by p_quarles on 2007-12-01
This is just a guess, but you might want to try running this command (from aysiu's tutorial) again:
```
sudo dpkg-reconfigure xserver-xorg
```
It may be that xorg wasn't configured correctly after installing the fonts.

I'm hoping that this will work, since I just installed that same package, and haven't restarted since :)

---

### Post by oeolycus on 2007-12-01
sudo dpkg-reconfigure xserver-xorg is functional. I've reentered all of the same settings as I had before. The problem doesn't seem to be that simple. It seems that several font files or directories were overwritten and I'm not sure how to recover them. My initial thought was reinstalling and reconfiguring xorgwould set it all right, but it hasn't.

As for specs:

[Compal CL-50]("http://www.laptopkb.com/index.php/Compal_CL50") (powerpro laptop)
1 gig ram
80 gig 7200 rpm Seagate HD

EDIT: As a sidenote, how do you include error output in a file with the command ">"?

---

### Post by p_quarles on 2007-12-01
> **oeolycus said:**
> EDIT: As a sidenote, how do you include error output in a file with the command ">"?
Never tried it, but I believe you could accomplish that with something like this. Boot to the command line, and:
```
startx > startx_output
```"startx_output" would be the name of the file. 

As for the main problem: It's difficult for me to say what the problem is, since I've never encountered it. If it's a bad package, then I will very likely encounter the next time I restart. If it happens to me, here's what I *would *do: look through the various configuration files in /etc/X11 and attempt to compare the font paths they're looking for with the font paths that really exist on the system. I would probably be cursing at the screen a lot while doing this. If I found what looked like the problem, I would fix the config file, and hope for the best. 

I'm not in a hurry to find out, but I'll definitely let you know. In any case, if font paths really were broken by installing that package, don't hesitate to file a bug report at Launchpad. Font packages should not break the X server.

EDIT: Just looked at the link for your system, and noticed it's got an ATI video card. Those things are notorious X crashers. Have you tried reinstalling the driver?

EDIT 2: Okay, I got curious and went ahead and restarted X. It didn't crash, but it did cause some serious resolution problems, This was fixed by restarting the computer itself, since that reloads some resolution patches that I have to use for my video card. This suggests to me that the problem is, in fact, with the ATI video card. If I were you, I would try uninstalling the fonts:
```
sudo apt-get remove --auto-remove xfonts-artwiz
```
I say this because I'm now seeing what this package does: it creates some nice graphical effects with things like menus and tooltips. But, my graphics card (Intel) has an open source driver that handles things like that. The ATI cards don't handle advanced Linux graphics as easily.

---

### Post by oeolycus on 2007-12-02
Thanks pquarles for your help. I've tried sudo startx > output_file, but it comes out blank.

I will give it another shot tomorrow looking through the X11 files. The Radeon Mobility 9000 is one of the worst graphics cards ever produced. Its support has been almost nil, but ironically, I've had better luck using it in Ubuntu than WindowsXP. I run most of my old games (Fallout, etc.) through Wine and Ubuntu--Windows doesn't remember how to do the things it used to.

How would I go about reinstalling that specific driver? Thanks again.

---

### Post by p_quarles on 2007-12-02
> **oeolycus said:**
> Thanks pquarles for your help. I've tried sudo startx > output_file, but it comes out blank.

I will give it another shot tomorrow looking through the X11 files. The Radeon Mobility 9000 is one of the worst graphics cards ever produced. Its support has been almost nil, but ironically, I've had better luck using it in Ubuntu than WindowsXP. I run most of my old games (Fallout, etc.) through Wine and Ubuntu--Windows doesn't remember how to do the things it used to.

How would I go about reinstalling that specific driver? Thanks again.
Note the edit I made to my last message -- I started that before I saw your reply.

Two things, though:
Don't run "startx" with "sudo." It doesn't need it, and running X as root is a security risk. Sorry that command didn't work, though. 

To reinstall the driver, I think this will work (keep in mind, though, that I've never used an ATI card, so am not an expert on this):
```
sudo apt-get --reinstall install xserver-xorg-video-ati xorg-driver-fglrx
```

---

