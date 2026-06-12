---
title: "where can I find the following kde libraries"
date: 2008-05-06
forum: General Help
---

### Post by linuxed on 2008-05-06
I just installed kdelibs, kdelibs-data, and kdelibs4c2a.  But I seem to be missing the following libraries.  Where can I find them or how can I install them?  Thanks.
```

	libkio.so.4 => not found
	libkdeui.so.4 => not found
	libkdesu.so.4 => not found
	libkwalletclient.so.1 => not found
	libkdecore.so.4 => not found
	libDCOP.so.4 => not found
	libkdefx.so.4 => not found
	libqt-mt.so.3 => not found
	libfam.so.0 => not found

```

---

### Post by hariprs on 2008-05-06
How did you install it? From Gnome? Using Synaptic Package Manager?

---

### Post by linuxed on 2008-05-07
sudo apt-get install kdelibs

---

### Post by linuxed on 2008-05-07
Well, apparently all of these libraries are in fact installed since they are included in the following packages which I just installed.
```

libqt3-mt
  libqt-mt.so.3
libgamin0
  libfam.so.0
kdelibs4c2a
  libkio.so.4
  libkdeui.so.4
  libkdesu.so.4
  libkwalletclient.so.1
  libkdecore.so.4
  libDCOP.so.4
  libkdefx.so.4

```
But anytime I run a program that requires those files it tells me they can't be found.  So I'm assuming that means they just weren't correctly registered during the installation.  Any idea how to fix this?

---

### Post by Monicker on 2008-05-07
Try

```
sudo ldconfig
```

---

### Post by roderick on 2008-05-07
Did synaptic happen to crash or report any error during installation? This sounds suspiciously like a "half-configured" install problem as ldconfig is usually run as part of the post install step.

Try dropping to a console and running:

```

sudo apt-get update
sudo apt-get upgrade

```

See if you get any warnings about half-configured or any other error.

If you do, read my blog posts here (part I and part II): 
[http://roderick-greening.blogspot.com/search/label/apt](http://roderick-greening.blogspot.com/search/label/apt)

Hope this helps.

Note: It is aimed at Kubuntu, but you can substitute Adept with Synaptic, konsole with gnome-terminal.

---

### Post by linuxed on 2008-05-07
Roderick and monicker thanks for your suggestions.  As it turns out the problem was actually related to the 32-bit libraries.  When I installed kdelibs it only installed the 64-bit versions of the libraries.  The program I was trying to run required the 32-bit libraries so it kept alerting me that they were not found when I knew that they had been installed, they just weren't installed in the /usr/lib32 folder.  So for anyone else who runs into this problem here's how you can fix it.

1. Download the i386 versions of the files you are missing.  In my case it required the following 3 packages.

libgamin0_0.1.8-2_i386.deb
libqt3-mt_3.3.7-4etch1_i386.deb
kdelibs4c2a_3.5.5a.dfsg.1-8etch1_i386.deb

2. Run file-roller as root so you can extract the files to /usr/lib32

gksudo file-roller

3. Open each package and select the files to extract.
4. Extract the files to /usr/lib32
5. Run program. Be happy.

List of files that I extracted to /usr/lib32:

libfam.so.0
libfam.so.0.0.0
libqt-mt.so.3
libqt-mt.so.3.3
libqt-mt.so.3.3.7
libDCOP.so.4
libDCOP.so.4.2.0
libkdecore.so.4
libkdecore.so.4.2.0
libkdefx.so.4
libkdefx.so.4.2.0
libkdesu.so.4
libkdesu.so.4.2.0
libkdeui.so.4
libkdeui.so.4.2.0
libkio.so.4
libkio.so.4.2.0
libkwalletclient.so.1
libkwalletclient.so.1.0.1

---

