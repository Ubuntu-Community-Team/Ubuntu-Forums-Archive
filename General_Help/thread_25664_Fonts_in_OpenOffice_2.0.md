---
title: "Fonts in OpenOffice 2.0"
date: 2005-04-10
forum: General Help
---

### Post by sethmahoney on 2005-04-10
I'm currently using OpenOffice 2.0 with Hoary.  I've enabled all the fancy supersmooth fonts, and it looks pretty good, except in OpenOffice, where the fonts are all chunky, both in the documents and in the menus.  Any idea what's going on?  I've got a screenshot attached, hopefully.

---

### Post by humanity_to_others on 2005-04-10
Extra fonts can help:
[http://ubuntuguide.org/#extrafonts](http://ubuntuguide.org/#extrafonts)
```
sudo apt-get install msttcorefonts
```
[IMG]http://xs404.xs.to/pics/05151/font.png[/IMG]

---

### Post by sethmahoney on 2005-04-10
Thanks, but I already have the msttcorefonts package installed.  I can use Arial, for example, but it looks just as chunky as anything else.

---

### Post by sethmahoney on 2005-04-10
Fixed the problem.  If anyone else has this issue, shut down OpenOffice and run

sudo fc-cache -v

When you start it back up, everything should look fine.

---

### Post by rosslaird on 2005-04-11
Thanks for the fix!
I had given up on OO2 because of this weird problem (I figured it would get fixed in a later update).

---

### Post by rosslaird on 2005-04-11
Update:

The fix only works (for me) during the current OO session. If I restart OO2, or restart X, or reboot, OO2 reverts to ugliness...

---

### Post by kevin1 on 2005-05-06
I am finding OpenOffice 2.0 unusable under Hoary due to corrupt font display.
(The Windows version works fine!  :? ).

I am not sure whether downloading new fonts will fix the problem, but thought I would give it a try.

Unfortunately, 'sudo apt-get install msttcorefonts' results in:

Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

I do have 'universe' enabled in /etc/apt/sources.

I'd be grateful for any advice on fixing this.

Thanks,

Kevin

---

### Post by 8oluf7 on 2005-05-06
*I do have 'universe' enabled in /etc/apt/sources.*

Synaptic failed to find msttcorefonts for me until I enabled the Multiverse repositories.

Now can somebody please explain  how to get and install these fonts - remembering I'm new to all of this, especially the command line stuff. I want to use the fonts with a DTP package (Scribus) as well as OO. All of the information I have found so far via the Scribus website expects me to be using an RPM-based distro and KDE.  ](*,)

Mike G.

---

### Post by kevin1 on 2005-05-07
Thanks for the tip about 'multiverse'  8oluf7.

To spell it out for anyone else who is struggling with this, I added:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

... to my /etc/apt/sources.list.

I then clicked the 'Reload' button in Synaptic, followed by a search for 'msttcorefonts'.
I then marked it for installation and clicked apply.

The fonts were then installed.

However, this did not fix my problem, nor did 'sudo fc-cache -v'.  ](*,)

Kevin

---

### Post by 8oluf7 on 2005-05-07
Thanks Kevin1.

When I restarted my machine today I found the additional fonts were available in both the OO (1.1.3) and Scribus font lists. So that's one problem solved. :)

---

### Post by apox on 2005-05-08
I've noticed that I get the same 'clunky font' behavior _every other_ time I start OpenOffice2. It does not occur with OpenOffice1. Very odd...

--Mark

---

### Post by l.tambiah on 2005-05-09
Unless your testing the software for bugs you really should avoid using Openoffice 2.0 for mission crtical tasks. II have not used the beta version yet and will wait till the stable version has been released before i dig in. 

Anyway in regards to Openoffice i have had what i would describe as clunky blurred fonts with in the application. As a test i installed AbiWord (which is great!!!!), and my fonts where clean and sharp as i would expect. I now figured this is an Openoffice issue. 

Before i explain the Openoffice solution that worked for me i will take you through my set up in the Font preferences of Gnome. The Gnome preferences can be found by going to System>Preferences>Fonts. 

First instal Microsoft True type fonts, which can be downloaded and added to your system using apt-get. 

I then used Arial 11 as my Application font, desktop font, and window title font. The terminal font was set with courier new. I set the Font rendering to Mono Chrome. The resolution was set to 72 dots per inch and smoothing is set to none. Hinting can be set to full. The subpixel default value of RGB is fine. For me this produced clean sharp fonts similiar to windows. 

As we selected Smoothing "None" and not "Greyscale" there is no antialiasing being applied to the fonts (which is what i want, applying antialiasing can distort fonts, although it improves images). 

In OpenOffice go to the menu Tools>Options. You will now see a dialogue box now click OpenOffice.org and select view. Look for the option "Screen font antialiasing" and uncheck it and click ok.

You should now see clear fonts when you type. Hope this helps..........

---

### Post by sethmahoney on 2005-05-09
[QUOTE=apox]I've noticed that I get the same 'clunky font' behavior _every other_ time I start OpenOffice2. It does not occur with OpenOffice1. Very odd...

--Mark[/QUOTE]
 Yeah, I've discovered that myself.  The problem isn't that the fonts are ugly every time, but that they're ugly every other time I start OpenOffice.  However, if I close the program when I get ugly fonts and open it up again (a pain, but whatever), I get nice, clean fonts again.

---

### Post by dunnerz on 2006-05-31
Try:

Tools->options->View

uncheck  Use system font for user interface

(i have the anti-alaysising options checked)

:D

---

