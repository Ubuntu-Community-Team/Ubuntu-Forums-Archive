---
title: "How do i know what I have installed?!"
date: 2004-11-07
forum: General Help
---

### Post by andy_sp1ke on 2004-11-07
How do I get a list of what packages are installed on my system to help with finding what needs to be installed to make programs work? I'm becoming a little confused about what i have and dont have! Will things i install through the terminal appear in the syntaptic package manager?

Cheers

Andy

---

### Post by im_ka on 2004-11-07
[QUOTE=andy_sp1ke]How do I get a list of what packages are installed on my system to help with finding what needs to be installed to make programs work? I'm becoming a little confused about what i have and dont have! Will things i install through the terminal appear in the syntaptic package manager?

Cheers

Andy[/QUOTE]

yes they will. synaptic runs those commands you'd type in the background.

```
man apt-get
``` for some cool commands :)

---

### Post by p!=f on 2004-11-07
[QUOTE=andy_sp1ke]How do I get a list of what packages are installed on my system to help with finding what needs to be installed to make programs work?
[/QUOTE]

This is where dependencies take place. If you install any program using apt, it will automagically resolve all dependencies and download/install appropriate libraries and other programs.
```

apt-cache depends gaim

```
This will show you a list of packages which will be installed with gaim.

Do you have any programs which refuse to run?

* Using Synaptic:
Sort by status and you can immediately see what's installed, what's not, what can be upgraded, what's broken, ...

* Using command line:
To get a full list of installed packages:
```

dpkg -l

```

To get a full list of packages with other status then ii (correctly installed):
```

dpkg -l | grep -v ^ii

```
pi means "partially installed" so it's wise to reinstall the package
rc means "removed but configuration files still present"
To remove the package Gaim but don't delete its configuration:
```

sudo apt-get remove gaim

```
To remove the package Gaim completely:
```

sudo apt-get --purge remove gaim

```
See dpkg/apt-get documentation for more informations.

[QUOTE=andy_sp1ke]
Will things i install through the terminal appear in the syntaptic package manager?
[/QUOTE]
Sure.

---

### Post by WW on 2004-11-07
I'm still learning about dpkg, apt-get, and other package management commands, but as far as I can tell, this command should do what you want:

```
dpkg -l
```

You can also use Synaptic.  Just click on the "S" (the column header of the first column in the display of the packages).   The green squares indicate installed packages.


*Ha! Looks like p!=f got there before me, and with a much more thorough answer.*

---

### Post by jdong on 2004-11-07
[QUOTE=andy_sp1ke] Will things i install through the terminal appear in the syntaptic package manager?

Cheers

Andy[/QUOTE]

Remember that Synaptic is a *frontend* to apt. All synaptic really does is issue the above mentioned commands in the background and format the results graphically.

---

### Post by andy_sp1ke on 2004-11-07
ok thats excellent, am looking through at whats installed etc. THe problem i am having is with BitTorrent Client which i installed through synaptic and Azuerus which should work because its Java based but when i click on the icon nothing happens, also LimeWire is in a .bin file and I cant remember what to do with it!!

Andy

---

### Post by p!=f on 2004-11-07
[QUOTE=andy_sp1ke]ok thats excellent, am looking through at whats installed etc. THe problem i am having is with BitTorrent Client which i installed through synaptic and Azuerus which should work because its Java based but when i click on the icon nothing happens, also LimeWire is in a .bin file and I cant remember what to do with it!!

Andy[/QUOTE]

* Not enough informations detected * ;)

1) APT won't take care about the software which was not installed as a **Debian** package.
2) Where's Java installed? Is Java working? Can you run other Java applications?
3) Where's Azureus installed? Did you edit its startup script?
```

 * 17:51:15 * pef @ agonicus *
[~] > head -5 /opt/apps/azureus/azureus
#!/bin/bash

######## CONFIGURE ########
JAVA_PROGRAM_DIR="/usr/bin/"             # use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
PROGRAM_DIR="/opt/apps/azureus/"      # use full path to Azureus bin dir

```
Setting up JAVA_PROGRAM_DIR is essential.

4) What do you get when you try to run Azureus from the command line?

---

### Post by andy_sp1ke on 2004-11-07
Ok i dont think Java is installed actually. I saw that Ubuntu doesnt come with it installed and looking at the list from dpkg -l i cant see Java listed as being installed. Am looking at the lib.... files to see if there is a libjava (or similar). I have downloaded Java but it comes as a bin file and having a few problems there. Going to read through what was written above with the example of gaim to see if i can work it out!

When i lauch azureus nothing happens, thats for both the program file and from the terminal.

i shall supply more infomation as i work on it ! 

andy

---

### Post by arjaybe on 2004-11-07
[QUOTE=andy_sp1ke]Ok i dont think Java is installed actually. I saw that Ubuntu doesnt come with it installed and looking at the list from dpkg -l i cant see Java listed as being installed. . .

andy[/QUOTE]

From my MEPIS partition, which does install with Java, here is the Java line from /etc/apt/sources.list:

# java
deb [ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian](ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian) unstable main non-free

(Watch that doesn't get word-wrapped.)

If you add this to your /etc/apt/sources.list and apt-get update, you should be able to find Java to install.  (All pertinent disclaimers go here.)

Once you do that you're no longer running an official Ubuntu, though.

---

### Post by arjaybe on 2004-11-07
Okay, the part that got cut out of the url at /dev . . .down:

/devel/lang/java/blackdown.org/

---

### Post by andy_sp1ke on 2004-11-07
What do you mean i would no longer be running an offical ubuntu? Am i right in thinking Ubuntu doesnt normally have Java, which means you need to install it when you come across something that uses it? which is what I can do from the infomation you gave me? What other difference does it make and why does ubuntu not support it?

cheers

andy

---

