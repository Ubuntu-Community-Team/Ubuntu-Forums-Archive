---
title: "[SOLVED] Add/Remove trouble in Xubuntu"
date: 2007-02-12
forum: General Help
---

### Post by Zeotronic on 2007-02-12
I just installed Xubuntu (6.10) yesterday and despite its lack of support for my modem, got it online today with the use of my brother's computer (Windows XP improperly installed over Windows 95 in a 10 year old Dell Latitude) through a network connection. Now, when I try to use Add/Remove in the 'Other' section of the Xfce menu it will function properly until I try to install something, in which case it will give me the error :
> E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I'm not entirely sure what this means or how to deal with it. If its of any relation, the particular things I am trying to install are the Blender 3D Modeller and the Inkscape Vector Illustrator, though I doubt that they have any connection with this problem.
I know that I could just get either of these programs from their respective websites however, my experiance with Xubuntu thus far has suggested to me 2 things.
1: Anything I intend to get I must compile.
2: I am not good at compiling.
So, if anyone could help me with fixing the Add/Remove Application or some very helpful pointers on compiling...

Also, this seems to effect a few other components that seem to deal with downloading from the internet as well, namely system based applications, not like Firefox and such.

---

### Post by SeanTater on 2007-02-12
Are you familiar with apt?

You may not need to compile anything at all..

Try this in a terminal:```
apt-get update && apt-get install
```
It should first update your packages, then try to fix them if there any broken ones.

While you're at it, read [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by Maestro23 on 2007-02-12
Have you tried getting programs from the Repositories via Synaptic or apt-get?  You also might have to enable extra repositories.

GUI: Synatpic
Command line: apt-get

You don't have to install everything from source.

Extra Reps: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

How to Install Software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
                                  [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Just some links to help you.  Good luck.

---

### Post by Zeotronic on 2007-02-12
SeanTater's code didn't seem to work for me, and if the icon beside Add/Remove means anything I was using Synaptic. If I'm not mistaken apt-get is for Debian isn't it? I know that Ubuntu and the like were created from Debian but I'm fairly sure that they arn't entirely compatible... But I would rather like to get Synaptic to work rather than downloading something of which I know absolutely nothing about.

---

### Post by Maestro23 on 2007-02-12
> **Zeotronic said:**
> SeanTater's code didn't seem to work for me, and if the icon beside Add/Remove means anything I was using Synaptic. If I'm not mistaken apt-get is for Debian isn't it? I know that Ubuntu and the like were created from Debian but I'm fairly sure that they arn't entirely compatible...But I would rather like to get Synaptic to work rather than downloading something of which I know absolutely nothing about.


If you read the Install links I gave you, you will see that apt-get and aptitude are both used in Ubuntu.

---

### Post by Zeotronic on 2007-02-12
Ok, so I tried using Aptitude, which I do have apparently. Anyways when I tried using Aptitude to get Inkscape, I got this error:
> E: I wasn't able to locate file for the conexant package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

If I'm not mistaken this error is very similar to the one I got with Synaptic... they both seem to mention a Conexant package. Though I recall some mention of it in my fiddlings with Xubuntu's support of my modem, I'm not quite sure what its talking about.

---

