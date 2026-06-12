---
title: "Install packages without Internet connection"
date: 2007-09-16
forum: General Help
---

### Post by pixeltarian on 2007-09-16
how do I do the "sudo apt-get install libgtk2.0-dev g++"with no internet connection? I downloaded the .deb, but it says it's missing package: 

libgtk2.0-0_2

when I try to install "libgtk2.0-0_2.10.6-0ubuntu3.1_i386.deb" it tells me a newer version is already installed. 

any help? 

I'm running widows on the same machine so I can download packages and install them in ubuntu. 

I'm running feisty fawn 7.04
athlon xp 2800
1GB or ram
blah blah blah ask if you need any more info... 

thanks so much, 

~ [p]ix

---

### Post by Bachstelze on 2007-09-16
Please paste the exact error message you get when you try to install your libgtk2.0-dev package.

---

### Post by pixeltarian on 2007-09-16
> **HymnToLife said:**
> Please paste the exact error message you get when you try to install your libgtk2.0-dev package.

./configure.sh --launcher=external

Using helper_launcher.sh as launcher proxy, you may need or want to tune this script.
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Please install (or upgrade to) GTK+ 2.6.0, at least.

====================================================

when I try to install libgtk2.0-dev I get: 
Error: Dependency is not satisfiable: libgtk2.0-0

when I try to install the package "libgtk2.0-0_2.10.6-0ubuntu3.1_i386.deb" 
(which is the dependancy that it's talking about, right?) 
I get the message: 
Error: A later version is already installed



any ideas? I'm excited to get ubuntu up and running. it's the 3rd distro I've tried and it looks really great.

thanks so much,

- pix

---

### Post by Bachstelze on 2007-09-16
> **HymnToLife said:**
> Please paste the exact error message you get when you try to install your libgtk2.0**-dev** package.

You should read more carefully...

---

### Post by pixeltarian on 2007-09-16
> **HymnToLife said:**
> You should read more carefully...

Dependency is not satisfiable: libgtk2.0-0

is that not what you're looking for?

I just added the other info to be thorough.

---

### Post by Bachstelze on 2007-09-16
Here's what an exact error message would look like :

```
root@Ana:~# dpkg -i libgtk2.0-dev_2.11.6-1ubuntu4_i386.deb
Selecting previously deselected package libgtk2.0-dev.
(Reading database ... 87523 files and directories currently installed.)
Unpacking libgtk2.0-dev (from libgtk2.0-dev_2.11.6-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libglib2.0-dev (>= 2.12.0); however:
  Package libglib2.0-dev is not installed.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not installed.
 libgtk2.0-dev depends on libatk1.0-dev (>= 1.6.1-2); however:
  Package libatk1.0-dev is not installed.
 libgtk2.0-dev depends on libcairo2-dev; however:
  Package libcairo2-dev is not installed.
dpkg: error processing libgtk2.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk2.0-dev

```

Not exactly what you posted...

---

### Post by pixeltarian on 2007-09-16
> **HymnToLife said:**
> Here's what an exact error message would look like :

```
root@Ana:~# dpkg -i libgtk2.0-dev_2.11.6-1ubuntu4_i386.deb
Selecting previously deselected package libgtk2.0-dev.
(Reading database ... 87523 files and directories currently installed.)
Unpacking libgtk2.0-dev (from libgtk2.0-dev_2.11.6-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libglib2.0-dev (>= 2.12.0); however:
  Package libglib2.0-dev is not installed.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not installed.
 libgtk2.0-dev depends on libatk1.0-dev (>= 1.6.1-2); however:
  Package libatk1.0-dev is not installed.
 libgtk2.0-dev depends on libcairo2-dev; however:
  Package libcairo2-dev is not installed.
dpkg: error processing libgtk2.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk2.0-dev

```

Not exactly what you posted...

my apologies. I am new at this. I'm guessing that means installing from the command line instead of the package manager. right?

---

### Post by Bachstelze on 2007-09-16
Oh, you were installing graphically ? Must have missed that... Anyway, try to install it from the command line (sudo dpkg -i file.deb) so we can see what's going on.

---

### Post by pixeltarian on 2007-09-16
> **HymnToLife said:**
> Oh, you were installing graphically ? Must have missed that... Anyway, try to install it from the command line (sudo dpkg -i file.deb) so we can see what's going on.

ah yes, here you go: 

Selecting previously deselected package libgtk2.0-dev.
(Reading database ... 87911 files and directories currently installed.)
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.11.6-1ubuntu4_i386.deb) ...
dpkg: dependency problems prevent configuration of libgtk2.0-dev:
 libgtk2.0-dev depends on libgtk2.0-0 (= 2.11.6-1ubuntu4); however:
  Version of libgtk2.0-0 on system is 2.10.11-0ubuntu3.
 libgtk2.0-dev depends on libglib2.0-dev (>= 2.12.0); however:
  Package libglib2.0-dev is not installed.
 libgtk2.0-dev depends on libpango1.0-dev (>= 1.10.0-2); however:
  Package libpango1.0-dev is not installed.
 libgtk2.0-dev depends on libatk1.0-dev (>= 1.6.1-2); however:
  Package libatk1.0-dev is not installed.
 libgtk2.0-dev depends on libcairo2-dev; however:
  Package libcairo2-dev is not installed.
 libgtk2.0-dev depends on libx11-dev (>= 2:1.0.0-6); however:
  Package libx11-dev is not installed.
 libgtk2.0-dev depends on libxext-dev; however:
  Package libxext-dev is not installed.
 libgtk2.0-dev depends on libxinerama-dev; however:
  Package libxinerama-dev is not installed.
 libgtk2.0-dev depends on libxi-dev; however:
  Package libxi-dev is not installed.
 libgtk2.0-dev depends on libxrandr-dev; however:
  Package libxrandr-dev is not installed.
 libgtk2.0-dev depends on libxcursor-dev; however:
  Package libxcursor-dev is not installed.
 libgtk2.0-dev depends on libxfixes-dev; however:
  Package libxfixes-dev is not installed.
 libgtk2.0-dev depends on libxcomposite-dev; however:
  Package libxcomposite-dev is not installed.
 libgtk2.0-dev depends on libxdamage-dev; however:
  Package libxdamage-dev is not installed.
dpkg: error processing libgtk2.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtk2.0-dev

looks like quite a few things need to be installed. should I just search for all of these packages and install them individually? I can't access the internet in ubuntu yet. 

my only fear is that these dependencies will have even more dependencies. 

thanks for the help, in spite of my newbie-ness

---

### Post by Bachstelze on 2007-09-16
@pixeltarian > You downloaded the Gutsy version (2.11.6). You must download the Feisty one (2.10.11). You also need the relevant versions of all listed -dev packages - they're libraries so there shouldn't be any additional dependency.

---

### Post by pixeltarian on 2007-09-17
> **HymnToLife said:**
> @pixeltarian > You downloaded the Gutsy version (2.11.6). You must download the Feisty one (2.10.11). You also need the relevant versions of all listed -dev packages - they're libraries so there shouldn't be any additional dependency.

*sigh*
they all seem to have dependencies. here's a couple examples: 

sudo dpkg -i /home/jeffrey/Desktop/pkgs/libatk1.0-dev_1.18.0-0ubuntu1_i386.deb
(Reading database ... 88586 files and directories currently installed.)
Preparing to replace libatk1.0-dev 1.18.0-0ubuntu1 (using .../libatk1.0-dev_1.18.0-0ubuntu1_i386.deb) ...
Unpacking replacement libatk1.0-dev ...
dpkg: dependency problems prevent configuration of libatk1.0-dev:
 libatk1.0-dev depends on libglib2.0-dev (>= 2.4.1-2); however:
  Package libglib2.0-dev is not installed.
dpkg: error processing libatk1.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libatk1.0-dev
===============================================
sudo dpkg -i /home/jeffrey/Desktop/pkgs/libcairo2-dev_1.4.2-0ubuntu1_i386.deb
Selecting previously deselected package libcairo2-dev.
(Reading database ... 88586 files and directories currently installed.)
Unpacking libcairo2-dev (from .../libcairo2-dev_1.4.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libfontconfig1-dev; however:
  Package libfontconfig1-dev is not installed.
 libcairo2-dev depends on libfreetype6-dev (>= 2.1.10); however:
  Package libfreetype6-dev is not installed.
 libcairo2-dev depends on libxrender-dev (>= 0.6.0); however:
  Package libxrender-dev is not installed.
 libcairo2-dev depends on libpng12-dev; however:
  Package libpng12-dev is not installed.
 libcairo2-dev depends on libsm-dev; however:
  Package libsm-dev is not installed.
dpkg: error processing libcairo2-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairo2-dev
===================================================
sudo dpkg -i /home/jeffrey/Desktop/pkgs/libglib2.0-dev_2.12.11-0ubuntu1_i386.deb
Selecting previously deselected package libglib2.0-dev.
(Reading database ... 88615 files and directories currently installed.)
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.11-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libglib2.0-dev:
 libglib2.0-dev depends on libc6-dev | libc-dev; however:
  Package libc6-dev is not installed.
  Package libc-dev is not installed.
dpkg: error processing libglib2.0-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglib2.0-dev
==================================================



any thoughts/suggestions ?

---

### Post by Bachstelze on 2007-09-17
Well, there's nothing you can do but download and install them all manually... You can also download a DVD from [here](http://www.ubuntu.com/getubuntu/downloadmirrors), which will have all those packages on it so you can install them with apt-get.

---

### Post by pixeltarian on 2007-09-17
> **HymnToLife said:**
> Well, there's nothing you can do but download and install them all manually... You can also download a DVD from [here](http://www.ubuntu.com/getubuntu/downloadmirrors), which will have all those packages on it so you can install them with apt-get.

i actually have a disk. but I think it tries to download things instead of look at the disk. 

when I try to add cdrom0 as a source, it gets to the point where it says "unmounting CD" and just sits there. 

I'll tinker around a bit. thanks for all the help. 

is there a way I can tell the installer to only look at the cdrom when getting files? 

goodness thanks for all the help. I really, truly appreciate it.

---

### Post by Bachstelze on 2007-09-17
I don't think the packages you need are on the CD, you'll have to get the DVD. Anyway, to add a disc to the repos list, do a *sudo apt-cdrom add*.

By the way, if you download the DVD ISO, you don't need to burn it. When you're asked to insert the disc, do this instead :

```
sudo mount -o loop file.iso /cdrom
```

---

### Post by pixeltarian on 2007-09-17
> **HymnToLife said:**
> I don't think the packages you need are on the CD, you'll have to get the DVD. Anyway, to add a disc to the repos list, do a *sudo apt-cdrom add*.

By the way, if you download the DVD ISO, you don't need to burn it. When you're asked to insert the disc, do this instead :

```
sudo mount -o loop file.iso /cdrom
```

thanks, I'll give that a try. it's downloading now. 

this seems like it has to work. thanks for taking the time to help me out. especially when I've (or rather, we've) added two pages to this thread just from this little problem. 

take care, 

~ Jeffrey James.

---

### Post by Bachstelze on 2007-09-17
> **pixeltarian said:**
> especially when I've (or rather, we've) added two pages to this thread just from this little problem. 

Yes, and which had very little to do with the subject of the thread :p I've moved those posts to a new thread.

---

### Post by pixeltarian on 2007-09-20
good idea. it all worked by the way.  ubuntu is running like a dream now... thanks a lot!

---

