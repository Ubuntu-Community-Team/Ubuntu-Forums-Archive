---
title: "Installing Banshee 0.11.3"
date: 2006-12-21
forum: General Help
---

### Post by RippyMan on 2006-12-21
Hi All,

I would like to install the newest version of Banshee in Ubuntu Edgy. Currently I have version 0.11.1, the version in the repository, but I would like to upgrade to version 0.11.3. I have attempted to install it from source following the directions on the Banshee Project's website ([http://banshee-project.org/Banshee_Source]("http://banshee-project.org/Banshee_Source")), but have had no success. I keep get the following error: 

```
make: *** No targets specified and no makefile found. Stop.
```

I still get this even after installing the gnome-devel package. Installing programs from source is very aggravating to me. Never once have I been successful. It would be very helpful to me if one of you all could tell either how to bypass compiling it from source altogether or find a solution to this issue. The former would be preferable, but either way would work. Thanks in advance for your help.

RippyMan

---

### Post by bruenig on 2006-12-22
Do you have build-essential installed? That is necessary.
```
sudo apt-get install build-essential
```
Also, explain the process you used to get to the point where you used make.

---

### Post by RippyMan on 2006-12-22
bruenig,

Thanks for your reply. Yes I did install build-essential. It seems to have no effect. Here is the exact code I typed in terminal. The first thing I did was to download the package from the Banshee project's website and place it in my home folder.

```

username@computer:~$ tar zxvf banshee-0.11.3.tar.gz
username@computer:~$ cd banshee-0.11.3
username@computer:~$ ./configure --prefix=/usr
username@computer:~$ make

```

Before doing that I did these steps:

```

username@computer:~$ sudo apt-get build-dep banshee
username@computer:~$ sudo apt-get install libmono-sqlite2.0-cil libmono-cairo2.0-cil libglib2.0-dev libtool subversion autoconf automake1.9
username@computer:~$ sudo update-alternatives --set automake /usr/bin/automake-1.9
username@computer:~$ sudo ldconfig

```

I appreciate your help. I would like to figure this out so I can wean myself of iTunes, and consequently, another thing I have to use Windows for. My guess is that this whole problem has something to do with the fact that the directions are for Dapper and I am attempting to do it in Edgy. 

RippyMan

---

### Post by bruenig on 2006-12-22
Did it configure properly?
You must be missing some dependencies or something and the configure is not actually running all the way through therefore leaving no makefile.

---

### Post by RippyMan on 2006-12-22
Okay, I actually got it working, but on a different computer. The computer I installed it on successfully had a clean install of Edgy, while the one I wanted to install it on had an installation that has been polluted a little more. It doesn't completely solve my problem, but at least I got it working. I following the directions on this website: [http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html]("http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html"). The only thing I did slightly different was to install the package **libmono-system-runtime2.0-cil** before doing Step 5. The whole process was really time consuming, but it is now working. I will admit that I wasn't overly impressed with this new version. It didn't really distinguish itself over version 0.11.1. The main reason why I wanted to install the newest version was to be able to do playlists on my 4th Gen iPod. I am still not able to do this in Banshee. Oh well, at least I was able to try it. For now I must remain with iTunes, unfortunately :( . Oh and by the way, I did not need to install build-essential or gnome-devel on the computer I was successful on. It worked fine without both of these. Thank you bruenig for your help.

RippyMan

---

