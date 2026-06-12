---
title: "&quot;type apt-get install apt-get&quot;????"
date: 2007-04-05
forum: General Help
---

### Post by phoenixfirebird on 2007-04-05
I recently developed a serious problem.  Apparently I some how deleted the program apt-get, or at least what's what I was told during one boot-up.  I was then given the instructions (I'm sure its just some automatic script that does it) to use apt-get to get the program ap-get.  

Of course, when I tried...it didn't work.  So...how do I reinstall apt-get?

---

### Post by Shmifty on 2007-04-05
Synaptic?

---

### Post by GuitarRocker2562 on 2007-04-05
is apt-get the same as aptitude, if not

"sudo aptitude install apt-get"

---

### Post by strabes on 2007-04-06
aptitude and apt-get are two different ways of installing packages. I prefer the former since it seems to handle dependencies and upgrades better. what guitarrocker2562 said should work.

---

### Post by phoenixfirebird on 2007-04-06
"Couldn't find any package matching "apt-get".  However, the following
packages contain "apt-get" in their description:
  newbiedoc gnome-apt xen-headers-2.6.19-4-generic 
  xen-headers-2.6.19-4-server adept-updater libcmdparse2-ruby1.8 aptitude 
  xen-headers-2.6.19-4 cron-apt debarchiver apt jablicator libcmdparse-ruby 
  posixtestsuite r-base libcmdparse2-ruby apt-build debdelta grep-dctrl 
  aptoncd auto-apt apt-move 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used."

aptitude worked, but it couldn't seem to find anything to download.  I guess I'll find out if I really have a problem next time I try and use apt-get.  Thanks for the help.

---

### Post by pppetter on 2007-04-06
lol. this was interesting! (Sorry for the laugh, but it's really strange). You should be fine using aptitude instead of apt-get. 

However, the package is named apt, and not apt-get, and it's listed in your previus post. 

> sudo aptitude install apt

should do the trick.

And heres some info on the APT package: [http://packages.ubuntu.com/edgy/base/apt](http://packages.ubuntu.com/edgy/base/apt)

---

