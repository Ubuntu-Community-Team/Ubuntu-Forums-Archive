---
title: "Download For X Error Message"
date: 2005-09-06
forum: General Help
---

### Post by Unit #134679 on 2005-09-06
When I try to run D4X, it runs but right when it opens, it terminates. I ran it in terminal and received this error message within the terminal:

(d4x:8045): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
Segmentation fault

---

### Post by arnieboy on 2005-09-06
[QUOTE=Unit #134679]When I try to run D4X, it runs but right when it opens, it terminates. I ran it in terminal and received this error message within the terminal:

(d4x:8045): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:8045): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
Segmentation fault[/QUOTE]


do a:
```
sudo apt-get install gtk2-engines-smooth

```and try again

---

### Post by Unit #134679 on 2005-09-06
mark@xxxxxxx:~$ sudo apt-get install gtk2-engines-smooth
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-smooth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by arnieboy on 2005-09-06
[QUOTE=Unit #134679]mark@xxxxxxx:~$ sudo apt-get install gtk2-engines-smooth
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-smooth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems[/QUOTE]
your /etc/apt/sources.list is screwed up. 
make it look like the following:
[http://ubuntuguide.org#repositories](http://ubuntuguide.org#repositories)

---

### Post by Unit #134679 on 2005-09-06
Upon correction:

mark@xxxxxx:~$ sudo apt-get install gtk2-engines-smooth
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-smooth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by arnieboy on 2005-09-06
[QUOTE=Unit #134679]Upon correction:

mark@xxxxxx:~$ sudo apt-get install gtk2-engines-smooth
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-smooth is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems[/QUOTE]

u want to do the following:
```
sudo apt-get remove gtk2-engines-smooth
sudo apt-get update
sudo apt-get install gtk2-engines-smooth
```
in exactly the order that I have mentioned.

---

### Post by Unit #134679 on 2005-09-06
Upon removing GTK-Engines-Smooth:

mark@xxxxxxx:~$ sudo apt-get remove gtk-engines-smooth
Reading package lists... Done
Building dependency tree... Done
Package gtk-engines-smooth is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by arnieboy on 2005-09-06
[QUOTE=Unit #134679]Upon removing GTK-Engines-Smooth:

mark@xxxxxxx:~$ sudo apt-get remove gtk-engines-smooth
Reading package lists... Done
Building dependency tree... Done
Package gtk-engines-smooth is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems[/QUOTE]

gtk2-engines-smooth (not gtk-engines-smooth) I corrected my typo within 10 secs of posting the reply. sorry abt that though

---

### Post by Unit #134679 on 2005-09-06
mark@xxxxxx:~$ sudo apt-get remove gtk2-engines-smooth
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gtk2-engines-smooth
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 266kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 67223 files and directories currently installed.)
Removing gtk2-engines-smooth ...
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


I even continued with your instructions for the hell of it too, and D4X did the same thing

---

### Post by arnieboy on 2005-09-06
ok do this:
change your gnome theme to the "human" theme and try running d4x again.

---

### Post by Unit #134679 on 2005-09-06
I cant get to Themes cause I'm having another problem I'm trying to get solved. I cant see the Preferences and Administration menus...they show up blank

---

### Post by arnieboy on 2005-09-06
[QUOTE=Unit #134679]I cant get to Themes cause I'm having another problem I'm trying to get solved. I cant see the Preferences and Administration menus...they show up blank[/QUOTE]
run from terminal:
```
gnome-theme-manager
```

---

### Post by Unit #134679 on 2005-09-06
There we go. Thanks. Why doesnt it work with certain themes I have?

---

### Post by arnieboy on 2005-09-06
cuz some of them have gtk2 related bugs

---

### Post by Unit #134679 on 2005-09-06
Ah, thanks for the help arnieboy :)

---

