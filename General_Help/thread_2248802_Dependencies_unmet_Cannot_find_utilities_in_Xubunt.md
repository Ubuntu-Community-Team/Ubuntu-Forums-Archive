---
title: "Dependencies unmet? Cannot find utilities in Xubuntu 14.04..."
date: 2014-10-17
forum: General Help
---

### Post by Mike_Walsh on 2014-10-17
Morning, all.

Now, then; following a completely successful installation of Kubuntu 14.04 to a SanDisk CruzerBlade flashdrive a fortnight ago, I've just done the exact same thing with Xubuntu 14.04 to another CruzerBlade. 

(I like the CruzerBlades; they're small, low profile, and seem to work very well with Linux...)

After restarting, updating, and configuring, I started installing my usual extras and other things. GParted & Disks are not included as standard with Xubuntu, so in they went...

...only to discover I couldn't find them in the main (Whisker) menu. 

I've removed them from the USC (which insists they're both installed); I've installed them via the terminal.....still no joy. So I removed them (via terminal), installed Synaptic, and installed them THAT way. 

I can start them both via the terminal:

```
sudo gparted
```

and:

```
sudo disks
```

without any problem; but I would PREFER to start them via the menu. Has anybody out there got any ideas as to why they're not showing up? I had a similar installation on my external HDD a few months back, and I had NO problems with getting them to show up in the menu on that occasion.  The ONLY difference with this install is that I've also installed the XFCE 'Screenlets' package so I could have a nice big analogue clock on my desktop, as well as a calendar; could this package have installed or removed any dependencies that might conflict with what the other two require? :confused:

Any advice would be appreciated.

Regards,

Mike.

---

### Post by vasa1 on 2014-10-17
I don't have either program but one hint may lie in the program's .desktop file. Is there a line starting with something like OnlyShowIn followed by a specific DE (Unity/GNOME/etc)?

---

### Post by ibjsb4 on 2014-10-17
I do not run Whisker, but found a similar answer.
> Check individual launchers /.desktop files for parameters like "OnlyShowIn" and "NoDisplay" to hide or un-hide applications.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=+add+edit+apps+Whisker+menu&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=+add+edit+apps+Whisker+menu&sa=Search&cof=FORID:9)

---

### Post by Dennis N on 2014-10-17
**GParted and Disks in Xubuntu 14.04**

On my Xubuntu 14.04 GParted appears in the Whisker menu under **Settings > System**, and Disks (gnome-disk-utility) appears under **Settings > Hardware**

---

### Post by Mike_Walsh on 2014-10-19
> **Dennis N said:**
> **GParted and Disks in Xubuntu 14.04**

On my Xubuntu 14.04 GParted appears in the Whisker menu under **Settings > System**, and Disks (gnome-disk-utility) appears under **Settings > Hardware**

Dennis to the rescue again..!

Oh, you are SO right, mate. I found them in the Settings menu myself last night, when I was looking for something else entirely; always the way.

I knew they had to be SOMEWHERE not too far away, since the USC insisted they WERE installed. It just never occurred to me to look there!

I know what threw me out. I have the 'xubuntu-desktop' package installed on my Ubuntu setup.....NOT just the 'xfce-desktop' package. When I installed it, I was after just the extra desktop, but got the wrong package, by mistake.....and it was easier to just leave it as was, rather than uninstall, and re-install again. So, I've got the WHOLE thing; and when I'm running the 'xfce-session' from login, if I look in the main menu, I've got all the software showing from Ubuntu as well as the Xubuntu stuff. It's like I've combined TWO OSs in one.....which I suppose I HAVE done, if you think about it..!

That's why I expected to see it show up in the Whisker menu.

Actually, having installed Conky in a short-lived fit of enthusiasm (didn't last long; I LIKE tweaking, but there ARE limits.....THAT is complicated!), at log-in I now have a choice of:-

-Gnome (Compiz)
-Gnome (Metacity)
-Ubuntu
-Xfce
-Xubuntu session

A bigger choice than I originally envisaged; because Conky installs the Gnome packages; well, it must do, 'cos they weren't there BEFORE installing it, and they WERE there immediately afterwards.....*sigh* I'm NOT messing with it ANY more; it works as it is; I'm leaving THAT install well alone from now on!!!

We 'live & learn', don't we? ;)

Will mark this as 'Solved'!

Regards,

Mike.

---

