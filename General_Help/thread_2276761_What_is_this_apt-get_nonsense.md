---
title: "What is this apt-get nonsense?"
date: 2015-05-04
forum: General Help
---

### Post by Richard_M._Utter on 2015-05-04
This is a first. Usually I solve my own problems. I've been running Ubuntu for several years, but the following error messages, written in an English-like language, left me baffled. 

```

rmu@ThermalCity1:~/SW/Source/efl-1.13.2$ sudo apt-get install libgles2-mesa
[sudo] password for rmu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcheese-gtk23 : Depends: libclutter-1.0-0 (>= 1.13.2) but it is not going to be installed
                   Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
rmu@ThermalCity1:~/SW/Source/efl-1.13.2$ 

```

Can someone smarter than me explain exactly what is being said here? I should point out that I'm running 14.04 LTS, and that the "cheese" application was uninstalled long ago. Thank you.

---

### Post by Vladlenin5000 on 2015-05-04
Hi and welcome.

You have broken packages / dependencies issues.
What are you trying to do/install? Something to do with Intel graphics drivers?!?... What exactly and for what purpose? That might give a clue about what's happening now and solutions may follow.

---

### Post by mc4man on 2015-05-04
This may shed some light - 
```
apt-cache policy libgles2-mesa-lts-utopic libgles2-mesa
```

---

### Post by Keith_Helms on 2015-05-05
It looks like somebody moved your cheese. ;)

---

### Post by Richard_M._Utter on 2015-05-06
Thanks to those who replied, and a small apology for a somewhat tardy response.

Yesterday morning, I poked around a little further, and concluded that apt-get had erred when it apparently uninstalled "libcheese" after I requested that the "cheese" application be uninstalled. I still have no idea why my attempt to install the "libgles2-mesa" package triggered the odd error messages. I had installed at least a dozen other packages before the error messages appeared.

mc4man, I suspect your note was intended to hint that "libgles2-mesa" is part of the stock Ubuntu setup. It would be a kindness on the part of the "apt-get" developers to hint that a package is already in place. Something along the lines of "Hey, it's already installed!" would get the job done.

Finally, I'll add a paragraph aimed at people building software who have wasted too much time repeating the following sequence over and over again.

1. "./configure"
2. Watch the script crash because file "XXX" is missing.
3. Waste far too much time Locating and installing the package containing "XXX".
4. Start over at step 1.

Replace step 3 with what follows.

"apt-file search XXX | more"

Copy the name of the package at the beginning of the "apt-file" output line. If there are multiple lines, you may have to do a little research to select the appropriate package.

"sudo apt-get install <package-name>"

You must install "apt-file", then run "apt-file update", before this will work correctly.

In my case, I quickly concluded that what I lacked was not the libraries the application required, but the include files need to actually employ the libraries. So my "apt-file" command line changed slightly, and the output looked like this.

```
rmu@ThermalCity1:~$ apt-file search gl3.h | grep include | more
libgles2-mesa-dev: /usr/include/GLES3/gl3.h
libgles2-mesa-dev-lts-utopic: /usr/include/GLES3/gl3.h
rmu@ThermalCity1:~$ sudo apt-get install libgles2-mesa
```

---

### Post by mc4man on 2015-05-06
I think you're over complicating this. 
If you are on the orig 14.04 or 14.04.1 image then libgles2-mesa is installed. If on the 14.04.2 image install then  libgles2-mesa-lts-utopic is installed. Each has it's own -dev package. Attempting to install one when using the other is going to cause issue similar to what you saw.
apt-cache policy would have showed you which you have..

---

