---
title: "Lubuntu - removing Abiword etc?"
date: 2013-03-07
forum: General Help
---

### Post by 2CV67 on 2013-03-07
After upgrading Lubuntu to 12.10 I suddenly found my LibO .odt files were being opened by Abiword instead of previously-set LibO Writer.
I reset the default application to LibO Writer & that works OK for now.

But I thought I had removed Abiword some years back, so was surprised to find it there again.
I was even more surprised when I tried to remove it in SynApt and was told I must also remove Lubuntu-Desktop!

Some Googling showed this was an old concern & advice generally seemed to be to just go ahead removing it & everything would be OK, not actually removing my Lubuntu Desktop, just lubuntu-desktop...
Many discussions point to the Wiki item here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

Disconcertingly, that wiki says "The lubuntu-desktop would just need adding back in for the update from 10.04 to 10.10, after that it can be safely removed again."

Does that mean I have to remember to reinstall lubuntu-desktop before every upgrade?
Or is lubuntu-desktop & Abiword automatically included in every upgrade & I need to remember to remove them again after every upgrade?
Or is it simpler to just leave Abiword lying idle?
Or what?

Seems like a mess, so far...

Thanks for all advice!

---

### Post by Rex Bouwense on 2013-03-07
After installing Libe Office Writer and Calc, I uninstalled Abiword and Gnumeric.  It is no big deal since they do not take a lot of space but I just removed them.  I had tried to operate with Abiword but I found that I needed a few things that it was not capable of doing so I just installed Libre Office.  I'll put up with the larger foot print.  Abiword is a default install.  Your choice if you un-install or leave it.

---

### Post by cortman on 2013-03-07
Just uninstall Abiword with

```
sudo apt-get purge abiword
```

if it tries to uninstall lubuntu-desktop as well, run

```
sudo apt-mark manual lubuntu-desktop
```

then uninstall.

---

### Post by Rex Bouwense on 2013-03-07
> **cortman said:**
> Just uninstall Abiword with

```
sudo apt-get purge abiword
```

if it tries to uninstall lubuntu-desktop as well, run

```
sudo apt-mark manual lubuntu-desktop
```

then uninstall.

Houston, we may have a problem.  Is that last code necessary, because I never have done that.  I hope that I haven't screwed up my stuff.  It does seem to be working at max efficiency.  I was under the impression that when the computer spit out that little blurb about having to uninstall the lubuntu-desktop, it was a bug because it really didn't do it.  Is that wrong?

---

### Post by lykeion on 2013-03-07
> **Rex Bouwense said:**
> Houston, we may have a problem.  Is that last code necessary, because I never have done that.  I hope that I haven't screwed up my stuff.  It does seem to be working at max efficiency.  I was under the impression that when the computer spit out that little blurb about having to uninstall the lubuntu-desktop, it was a bug because it really didn't do it.  Is that wrong?

lubuntu-desktop is a meta package. It does not itself contains anything to install, it only declares some dependant packages (like lxterminal, leafpad, etc) and recommended packages (like abiword). apt-mark manual is used to mark a package as being manually installed, which will prevent the package from being automatically removed if no other packages depend on it.

---

### Post by Rex Bouwense on 2013-03-07
Thank you.

---

### Post by vasa1 on 2013-03-07
> **cortman said:**
> ...
if it tries to uninstall lubuntu-desktop as well, run

```
sudo apt-mark manual lubuntu-desktop
```

then uninstall.

That's really useful. Why don't you update [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop) with that information?

---

### Post by cortman on 2013-03-07
> **lykeion said:**
> lubuntu-desktop is a meta package. It does not itself contains anything to install, it only declares some dependant packages (like lxterminal, leafpad, etc) and recommended packages (like abiword). apt-mark manual is used to mark a package as being manually installed, which will prevent the package from being automatically removed if no other packages depend on it.

Thanks for explaining that.

> **vasa1 said:**
> That's really useful. Why don't you update [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop) with that information?

Thanks; I'll do that- never thought to check if it was there.
That command works for any large meta-package; e.g., xubuntu-desktop, ubuntu-desktop, gnome-core, etc.

---

### Post by 2CV67 on 2013-03-08
I am struggling to follow the ideas here, but I see you wasted no time in updating the wiki - thanks!

Still not clear for me though.
Following the new wiki, I STARTED (was that wrong?) by running ```
sudo apt-mark manual lubuntu-desktop
``` even though I avoid command line wherever possible (see signature).

What I got was:
```
chris@Acer-desk:~$ sudo apt-mark manual lubuntu-desktop
[sudo] password for chris: 
lubuntu-desktop was already set to be manually installed.
chris@Acer-desk:~$ 
```

Should I have removed Abiword (& lubuntu-desktop) first, THEN run sudo apt-mark manual lubuntu-desktop?

What will happen at future upgrades?
Do I get Abiword back again every time?

---

### Post by vasa1 on 2013-03-08
> **2CV67 said:**
> I am struggling to follow the ideas here...

What I got was:
```
... 
lubuntu-desktop was already set to be manually installed.
...
```

...
You've opened an interesting can of worms! After reading the response you got, I ran ```
sudo apt-mark showauto
``` and ```
sudo apt-mark showmanual
```. The lists don't make sense to me. Things I've never fiddled with, very basic software, are showing in the "showmanual" list.

I must clarify that I don't upgrade or even preserve /home. I do a clean install for each Ubuntu release. And this time, when I clean installed Lubuntu 12.10, I promptly removed Abiword and games and lost lubuntu-desktop as a result. Come 13.04, and I'll install afresh and remove what I don't want but I'll try to remember to run the apt-mark show commands to see what a new install looks like.

---

### Post by mastablasta on 2013-03-08
> **2CV67 said:**
> Still not clear for me though.<BR><BR><BR>I saw a good explanation on forums not long ago. anyway....let's try like this: there is a Lubutnu Desktop (the LXDE) and lubuntu-desktop package. the package tells the system what stuff should be installed to have lubuntu desktop "user experience" as ment by developers of the distribution. <BR><BR>now if you remove abiword from it it won't be the same "user experience" as developers had in mind. so you don't need the lubuntu desktop package anymore. since it is the one telling to the OS that Abiword ought to be be installed.<BR><BR>another way is if oyu had installed for example server or minimal ubutnu where all you would get in the end is a command line. then you could have just installed lxde package. this would give you the LXDE desktop, but not the look and feel of lubuntu . it also wouldn't install abiword and other packages. but you could add them all yourself one by one or all together. or you could simply use a metapackage lubuntu desktop which would search for them and install them all.<BR><BR>> <BR>What will happen at future upgrades?<BR>Do I get Abiword back again every time?<BR><BR>i believe so, yet. but i am not sure. and you would also keep additionally installed aplications that were not installed via PPA. i decided to go with fresh install since it's strangely faster.


edit: forgot to mention.... YOu can do the mark command in synaptic i believe. you can lock packages and such.

---

### Post by cortman on 2013-03-08
For me the reason I mark metapackages as manually installed is so that it doesn't remove the metapackage, then realize that all the dependencies are still there but are now "unneeded" since the package that depended on them is gone.
Marking it manually prevents catastrophes from happening when you run "apt-get autoremove".
I know some distros set some packages to manually installed to prevent this, Crunchbang does for some packages (I'm forgetting which ones now). That could be why some of your packages (@vasa1 @2VC67) are already set to manually installed.

---

### Post by vasa1 on 2013-04-08
@cortman, if you have the time, please take a look at [Uninstall empathy without affecting dependencies]("http://askubuntu.com/q/278500/25656"). OP was trying to remove Empathy without bringing down the house. I suggested the use of marking stuff "manual" but it didn't work.

---

