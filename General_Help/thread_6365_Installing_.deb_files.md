---
title: "Installing .deb files?"
date: 2004-11-27
forum: General Help
---

### Post by Gibbz on 2004-11-27
Ive got a few .deb files and i cannot figure out how to install them? cxan anyone point me in the right direction?

---

### Post by jdong on 2004-11-27
**dpkg --install file.deb**

--or--

**dpkg -i file.deb**.


For complete guide for the dpkg command:

**man dpkg**

Save for when you're bored!

---

### Post by Gibbz on 2004-11-27
so i cant just double click on them? or something like that?

---

### Post by jdong on 2004-11-27
[QUOTE=Gibbz]so i cant just double click on them? or something like that?[/QUOTE]

Unfortunately they aren't that easy yet... You must install via console. But it's really nothing to be afraid of. Issue one command, dpkg will install and then return you back to a prompt, at which time you're free to close the terminal.

---

### Post by az on 2004-11-28
Debs are not like rpms.

Debian has on organised packaging system.  You will not bugger up your system by using stable repositories of packages.  You can (will) screw up your system by installing individual deb files.

If you want to install them one at a time, without using apt (advanced package tool) or synaptic (which uses apt) - it is assumed you know what you are doing.  That is why no one complains about not having a gui for dpkg.  There is too much tinkering involved with it.

Apt, on the other hand is a different story...

---

### Post by uggeli on 2004-11-28
Edit: got problems fixed, but still want to ask following:

What command should I use when installing invidual deb file?

I have used command: sudo dpkg -i filename.deb

and got my system screwed up twice. Is there easy way to use apt-get to install allso invidual deb files so it installs all packages which are nececcearly? Or is there some commands for dpkg that dpkg doesn't install file if there is not already all files needed?

---

### Post by Marauder1 on 2004-11-28
Find a repository where the program
can be found and then use Synaptic.
Synaptic takes care of all the dependency
problems.

---

### Post by az on 2004-11-28
dpkg -i file
apt-get -f install 

that pulls in all undsatisfied dependancies or removes the offending package(s)

If your dpkg fails, the package can be unpacked but not configured.  That really can bugger your computer up.

---

### Post by uggeli on 2004-11-29
thanks for answers, now it's much easier to install debs when I know what commands to use to not screw my system. Don't have to 'scare' anymore.. :)

---

### Post by PFC.Spengler on 2005-08-30
[QUOTE=azz]

That is why no one complains about not having a gui for dpkg.  There is too much tinkering involved with it.

[/QUOTE]

I'm wondering if it is still the case, a year later, that dpkg is without a frontend.  I, for one, am complaining, and I'm going to look into writing a kde frontend for dpkg, it doesn't seem like a particularily indepth project.

---

### Post by Ricapar on 2005-08-31
I don't see that much of a danger in using dpkg to install .debs. There are many things that I've had to use .debs that I've downloaded, mainly because they weren't in the repositories, or the ones in the repositories were outdated. 

There are also programs that you won't find in there either, commercial ones specificly, such as Cedega and Limewire to name two.

Of course apt-get/aptitude/Synaptic should be used when possible, but saying that using dpkg to install debs in general will screw up your system is a bit untrue.

---

### Post by manqueller on 2007-04-15
> **jdong said:**
> **dpkg --install file.deb**

--or--

**dpkg -i file.deb**.


For complete guide for the dpkg command:

**man dpkg**

Save for when you're bored!

Thanks for the help.  I just installed Alien because I thought I needed that to get AVG anti-virus, but then when I went to download the anti-virus software I found that they now have it available as a .deb and your thread helped out.  I got it installed now.  Thanks!

---

### Post by Stoneface on 2008-07-22
Well now you can install .debs using a gui. Gdeb is installed and does the work for you. It even checks if any dependencies are missing!

---

