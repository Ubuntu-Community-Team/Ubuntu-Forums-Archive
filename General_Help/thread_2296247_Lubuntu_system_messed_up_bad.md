---
title: "Lubuntu system messed up bad"
date: 2015-09-24
forum: General Help
---

### Post by KayeNg on 2015-09-24
Hi guys.  I installed a certain desktop environment in my Lubuntu (to use along with LXDE).  It didn't go over well, so I uninstalled it, then ran the autoremove command.  Afterwards, GDebi Package Installer wasn't working, so I removed it, then installed it via terminal.  Still not working.  Same with Synaptic.  It's a long story and I can't remember all the details.  Now gksu is gone too. Have a look below:

```
kaye@kaye-laptop:~$ gksu pcmanfm
The program 'gksu' is currently not installed. You can install it by typing:
sudo apt-get install gksu
kaye@kaye-laptop:~$ sudo apt-get install gksu
[sudo] password for kaye: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gksu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
kaye@kaye-laptop:~$ gksu pcmanfm
The program 'gksu' is currently not installed. You can install it by typing:
sudo apt-get install gksu
kaye@kaye-laptop:~$
```

It's never-ending as you can see.  Should I just reinstall the operating system?

P.S. the Fn + up, down, left, right arrow to adjust screen brightness and sound isn't working anymore.

---

### Post by sudodus on 2015-09-24
> **KayeNg said:**
> ...
It's never-ending as you can see.  Should I just reinstall the operating system?
...

Yes, I think so. It is probably the easiest and fastest way to get a working system :-)

---

### Post by ajgreeny on 2015-09-24
If you open synaptic and look in the status bar at the bottom does it show any errors or broken packages?

I think that before you reinstall, you should check the status of all your packages, so it is worth trying ```
sudo apt-get install -f
``` and ```
sudo dpkg-configure -a
``` just in case there are some unconfigured or broken packages.

---

### Post by KayeNg on 2015-09-25
hi guys

Update:

Gdebi ALREADY WORKING thru terminal as well as clicking it in Menu.

Gksu ALREADY WORKING; had to uninstall it thru synaptic, then install it thru synaptic again.

To:  ajgreeny

Clicking status in Synaptic does not show any broken packages.  Not sure what you mean by "unconfigured" ?

what does this do?  

sudo apt-get install -f

and this?

sudo dpkg-configure -a

Problems (for now):

Synaptic will open thru terminal by typing gksu synaptic , but if I click it in Menu, nothing happens.  Any solution?

Fn key + up and down arrow to adjust laptop screen brightness still not working; any solutions?   (Fn key plus left and right arrow buttons to adjust sound is working; only the brightness isn't working)

Thanks!

---

### Post by ajgreeny on 2015-09-25
> **KayeNg said:**
> Not sure what you mean by "unconfigured" ?

what does this do?  

sudo apt-get install -f

and this?

sudo dpkg-configure -a
**sudo apt-get install -f** is a command that should fix any broken packages.
**sudo dpkg-configure -a** is another command that will continue to configure any unconfigured packages if, for example, your computer is shutdown accidentally or crashes whilst carrying out some package installations, leaving them part installed but unconfigured and therefore "broken".

---

### Post by KayeNg on 2015-09-26
I'm getting this:

> kaye@kaye-laptop:~$ sudo dpkg-configure -a
sudo: dpkg-configure: command not found
kaye@kaye-laptop:~$

I'm using Lubuntu

---

### Post by KayeNg on 2015-09-26
I've partially found out the problem.  My system doesn't have this directory anymore:
> /sys/class/backlight/acpi_video0

Instead it has this
> /sys/class/backlight/samsung

Right now if I want to adjust screen brightness, I have to get inside  /sys/class/backlight/samsung  and edit "brightness" (without the quotation marks).

The Fn+up or down shortcut key is gone.  How do I get it back please?

---

### Post by Bashing-om on 2015-09-26
KayeNg; Hello;

A very small typo, that has great repercussions;
Happens to the best of us under the best of conditions. - typing hundreds of commands at a stretch, human error can and does creep in -
Correct ajgreeny's command to be:
```

sudo dpkg --configure -a

```
where there is a space ( as the separateor ) between 'dpkg' and the operative '--configure'. Note this operative requires 2 dashes .

Once executed, we see where we go from there.

What can I say, the command line is exact ->
[INDENT][INDENT]say what you mean, and mean what you say[/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-09-26
Whoops!  Sorry about that.  Not thinking as straight as I should have been.

---

### Post by KayeNg on 2015-09-27
> kaye@kaye-laptop:~$ sudo dpkg --configure -a
[sudo] password for kaye: 
kaye@kaye-laptop:~$

Rebooted. Fn key + up or down arrow button to adjust brightness still not working.
Temporary solution:
> sudo ln -s /sys/class/backlight/samsung/ /home/kaye/Desktop/

Regarding the synaptic issue, turns out that (probably) because of the installation of another desktop environment (which I have now uninstalled), and the subsequent un-installing and installing of synaptic, there appears to be a synaptic icon in:

 > /home/kaye/.local/share/applications

which is a desktop configuration file named > synaptic-kde.desktop  

I opened said desktop configuration file in leafpad and saw this:

> OnlyShowIn=KDE;

I put a # in front of it like this:
> #OnlyShowIn=KDE

and now it's visible in Menu-->System Tools, but when I click it, a pop up window says:

Starting "Synaptic Package Manager" without administrative privileges...........You will not be able to apply any changes, but you can still export the marked changes or create a download script for them."

That's not normal right? So right now, if I want to use synaptic, I open terminal and type gksu synaptic.  That way, I don't get the pop up window.

I would like these two issues (synaptic and backlight) to return to their original state, if it's possible. If not, nevermind.

Thank you

By the way, there's another synaptic desktop configuration file in 
> /usr/share/applications

which has these lines
> Exec=synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;System;
X-KDE-SubstituteUID=true
OnlyShowIn=KDE;

Don't really know if I should mess with it?

---

### Post by KayeNg on 2015-09-27
By the way, there's another synaptic desktop configuration file in 
> /usr/share/applications

which has these lines
> Exec=synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;System;
X-KDE-SubstituteUID=true
OnlyShowIn=KDE;

Don't really know if I should mess with it?

---

### Post by ajgreeny on 2015-09-27
That kde version of the synaptic.desktop file will open synaptic but you will not actually be able to use it to install or remove packages as it uses the line **Exec=synaptic** instead of **Exec=synaptic-pkexec** the latter of which opens synaptic as root.

Do you have a synaptic.desktop file in /usr/share/applications as you should with the **Exec=synaptic-pkexec** line?  Let's see the output of ```
ls /usr/share/applications | grep synaptic
```

For some reason that synaptic-kde.desktop file appears in my OS and always has, though I always add a few KDE applications to my OS even though I now run XFCE and used to run Gnome 2; perhaps that is where the file comes from.

---

### Post by KayeNg on 2015-09-27
Yes ajgreeny, it's there.  Here's what I did now for a fresh start:

Uninstall synaptic thru terminal with the remove command.  Re-installed it thru the same.  Immediately after installing, two identical synaptic desktop configuration files (synaptic icons) appear in 

/usr/share/applications

but the codes are a bit different.  One is:

> [Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=synaptic-pkexec
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

and the second one is:
> 
Exec=synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;System;
X-KDE-SubstituteUID=true
OnlyShowIn=KDE;

Surprisingly, the one with Exec=synaptic (the second one) is the one that can be opened.  The first does nothing when I click it.  It may also be the one residing in Menu-->System Tools because when I click it there, nothing happens too (which maybe correct because if I right-click it and click properties, the COMMAND is synaptic-pkexec.

Any thoughts?  This is on a Lubuntu, by the way.

---

### Post by ajgreeny on 2015-09-27
Check to see if both files are executable.  I am not even certain if they need to be for them to work as launchers but I think it might be so.

---

### Post by vasa1 on 2015-09-27
> 2.  I recently installed another desktop environment in my Lubuntu, which
proved to be buggy, so I uninstalled it.  **I wonder if _it_** has anything to do
with Fn key not working?This is from the [lubuntu users mailing list]("https://lists.ubuntu.com/archives/lubuntu-users/2015-September/009996.html"). Why didn't the poster mention what "_it_" was?

---

### Post by KayeNg on 2015-09-28
vasa1, it's the Enlightenment desktop.

ajgreeny, if by executable you mean it will open synaptic if I double click them, the answer is that one does nothing, the other one opens synaptic, but with a message like this:

Starting "Synaptic Package Manager" without administrative  privileges...........You will not be able to apply any changes, but you  can still export the marked changes or create a download script for  them."

Anyway, it's alright, I can live with it. No biggie.

---

### Post by timotheus3 on 2016-01-14
ps, i heard that using aptitude solves many similar problems because it keeps track of dependencies better, so installing/uninstalling desktop environments should be easier then with apt-get or synaptic

---

