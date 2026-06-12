---
title: "Nothing will apt install because of &quot;virtual packages&quot;"
date: 2007-07-25
forum: General Help
---

### Post by Donshyoku on 2007-07-25
I keep getting similar errors with each program I try to install through apt or a standalone deb that needs to satisfy a dependency.  Just for brevity's sake, I'll post an example.  It is the same problem with every app save for the names of the files needing to be fetched.

```
drew@drewbuntu64:~$ sudo aptitude install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  mplayer 
The following NEW packages will be automatically installed:
  libdvdread3 libfaac0 libggi-target-x libggi2 libgii1 libgii1-target-x 
  liblame0 libmp4v2-0 libpulse0 libxvidcore4 mplayer-skins 
The following NEW packages will be installed:
  libdvdread3 libfaac0 libggi-target-x libggi2 libgii1 libgii1-target-x 
  liblame0 libmp4v2-0 libpulse0 libxvidcore4 mplayer-skins 
0 packages upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 5903kB of archives. After unpacking 15.9MB will be used.
The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.0-1) which is a virtual package.
           Depends: libmad0 (>= 0.15.1b) which is a virtual package.
           Depends: libmpcdec3 which is a virtual package.
           Depends: libxvmc1 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
mplayer [Not Installed]

```

Substitute "mplayer" and "libmad0, etc" with your choice.  It says the apted package is broken, that it needs to satisfy virtual packages, and that it will not install the initial app a solution.  

Any ideas?

---

### Post by Donshyoku on 2007-07-25
Now apt will not find or install any packages, even ones that I know are in the repositories.  This is a clean install as of 6 oclock tonight and something is already wrong with it!  All I have done is dist-upgrade, install nvidia binary, and a reorganize my sources.list into something a little less messy and more coherent.  But I am 110% that it is functional and correct as a file, I always modify my organization in apt sources with all my Debian-based distros.  Should I reinstall?  Would it just be easier than troubleshooting this?

---

### Post by Donshyoku on 2007-07-26
I reinstalled the OS completely and right out of the box, I am getting the same thing again.  Not sure why this is happening out of the box unless something is wrong with an update in which case I would suspect more people reporting a similar issue.  If it helps, I am running x86_64 when this problem is occurring and I haven't DLed x86 to try it.

---

### Post by rbmorse on 2007-07-26
Please post the content of your 

/etc/apt/sources.list

file.  Sounds like a potential repository problem.

---

### Post by Donshyoku on 2007-07-28
I actually figured it out.  I don't know what I did wrong, but my sources were messed.  I had to restore the defaults by removing everything from the file and then readding repos through Synaptic.  It is odd that it happened this time as I always modify my source list in this format on Debian installs.  But, hey, at least it works now!

---

### Post by rbmorse on 2007-07-28
Cool beans

---

