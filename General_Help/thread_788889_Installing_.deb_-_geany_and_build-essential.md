---
title: "Installing .deb - geany and build-essential"
date: 2008-05-10
forum: General Help
---

### Post by zakiya on 2008-05-10
Hi, I am having trouble connecting to internet with ubuntu (gutsy), so cannot use synaptic package manager to install the packages I want. In the meantime I want to install build-essential and geany manually, so how do I do that?

I have used a windows pc to download the .deb packages of geany and build-essential onto a usb stick, so how do I then install these in ubuntu?

I have already tried just double clicking on the geany .deb, and it seemed to install ok (added to menu etc.) but just seg faults when I try to start it. Is there other package/s that I need first to install these .debs? Or should I try the .tar versions instead?

Thanks :)

---

### Post by MaindotC on 2008-05-10
Geany has these dependencies:

```

Depends: libatk1.0-0 (>= 1.13.2), libc6 (>= 2.5-5), libcairo2 (>= 1.4.0), libfontconfig1 (>= 2.4.0), 
libgcc1 (>= 1:4.2-20070516), libglib2.0-0 (>= 2.13.4), libgtk2.0-0 (>= 2.11.2), libpango1.0-0 (>= 1.17.2), 
libstdc++6 (>= 4.2-20070516), libx11-6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), 
libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1

```

Can you use the locate command and see if you have these packages installed?  I looked at geany from the get-deb site but I can't tell if it includes the dependencies.

---

### Post by zakiya on 2008-05-10
Thanks, slocate finds all the packages but some seem to be out of date, others do not have a version number listed so I can't tell. I think I really need to get the internet working first, as the package manager really seems the easiest way.

---

### Post by Glaxed on 2008-05-10
If you still have your install CD, edit your source.list to make it your primary source.
Then, update your system against the CD defaults and install Geany from there.

Failing that, get geany source on windows and compile it on your Linux box.
Good luck

btw: Geany is my FAVORITE editor. nothing really is better for the 'money' (or in this case CPU)

---

### Post by zakiya on 2008-05-11
I can't update my system as I can't connect to the internet in ubuntu (yet). All I have installed is what comes on the official gutsy live cd, so will those packages be sufficient to compile and install the geany source? 
Thanks.

---

### Post by mc4man on 2008-05-11
> so will those packages be sufficient to compile and install the geany source?  In all likelihood not. You could add ```
autoconf automake1.7 autotools-dev intltool m4
``` and possibly an additional dev or two. You'd have to try a build and see, if it fails you'd need something else

---

### Post by zakiya on 2008-05-11
No can't build as some are missing, getting a bit complicated for a complete novice :P

---

### Post by zvacet on 2008-05-11
Like **Glaxed** said make your CD one of repositoriy.That way you can install buid-essential from CD.For other package try [nonetdebs]("http://nonetdebs.homeip.net/").

---

### Post by zakiya on 2008-05-11
I have succesfully connected to another network (not at home) so am now able to update/install using the package manager. And yes, I already had an uptodate version of build-essential installed from the cd. 

I have freshly installed geany. Why is it that the terminal command geany causes a seg fault yet sudo geany works, and clicking on the geany entry in Applications->Programming does nothing?

Thanks.

---

### Post by Glaxed on 2008-05-11
What does 'gksudo geany' do?

---

### Post by zakiya on 2008-05-12
> **Glaxed said:**
> What does 'gksudo geany' do?

Same as sudo geany as far as I can tell. I initially installed geany by compiling the source code, but made a mistake, the README said to "become root" and I (being newbie) changed to root directory and did make install. So maybe that has left me with a broken install and that is causing the problem? How can I find and remove it?

thanks :)

---

### Post by zakiya on 2008-05-12
Apologies, gksudo opens geany but from the current directory, not root (like sudo geany).

---

### Post by mc4man on 2008-05-12
normally it should open from app menu or from terminal with just geany, no sudo , gksudo


edit;> How can I find and remove it?

If you haven't deleted your build folder and you wish to uninstall (now or later) cd to your build folder and run sudo make uninstall
In this case your fortunate that there is an uninstall rule in the make file so the command will work.

---

