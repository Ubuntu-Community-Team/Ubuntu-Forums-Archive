---
title: "Method to show installed proprietary software on system?"
date: 2015-07-04
forum: General Help
---

### Post by Rytron on 2015-07-04
Hi UF.

Is there a way to show what proprietary software is installed? It would be handy if Synaptic had a column for this to sort by.

Thanks.

---

### Post by Keith_Helms on 2015-07-04
What do you consider proprietary?  For example, is an Nvidia driver that has been tested and loaded into the repositories by the Ubuntu team proprietary?

---

### Post by deadflowr on 2015-07-05
> **Keith_Helms said:**
> What do you consider proprietary?  For example, is an Nvidia driver that has been tested and loaded into the repositories by the Ubuntu team proprietary?
Yes that is proprietary.
The Ubuntu devs only test and build a package around the driver so that it installs without problems on Ubuntu, but they do not have access to the source code.

Synaptic does have a column, sort of, for this it's the Origin section. There should be a section within that for Restricted.
I think multiverse contains closed source software as well...
I don't know if there is a way to toggle it to show only those packages that are installed though.
(Actually when you click on the restricted repo, go to the main package listing window and toggle the Installed Version item list)

---

### Post by Keith_Helms on 2015-07-05
> **deadflowr said:**
> Yes that is proprietary.
The Ubuntu devs only test and build a package around the driver so that it installs without problems on Ubuntu, but they do not have access to the source code.

Synaptic does have a column, sort of, for this it's the Origin section. There should be a section within that for Restricted.
I think multiverse contains closed source software as well...
I don't know if there is a way to toggle it to show only those packages that are installed though.
(Actually when you click on the restricted repo, go to the main package listing window and toggle the Installed Version item list)

Yes, I considered that proprietary too.  I was just trying to uncover what he considers proprietary and, as a followup, what could be searched on or queried to list those items.

Some purists might state that any software that isn't GPLed is proprietary! ;)

---

### Post by Irihapeti on 2015-07-05
You could install vrms (sudo apt-get install vrms), which will give you a listing of non-free software when run in a terminal.

On my system, it shows:

```
flashplugin-installer               Adobe Flash Player plugin installer
pepperflashplugin-nonfree           Pepper Flash Player - browser plugin
ttf-mscorefonts-installer           Installer for Microsoft TrueType core fonts
virtualbox-4.3                      Oracle VM VirtualBox

  4 contrib packages, 0.2% of 1749 installed packages.
```

I'm not sure of the definition of non-free, though it's likely to be fairly strict, given that:

```

       This program began as an attempt to create a "virtual Richard M. Stall&#8208;
       man" for Debian GNU/Linux.  Thus the choice of name.
```

---

### Post by Rytron on 2015-07-05
> **Irihapeti said:**
> You could install vrms...

Thank you Irihapeti - that's ideal. Here's an abridged listing of my terminal output.

```
Non-free packages installed on PC_XYZ

adobe-flash-properties-gtk          GTK+ control panel for Adobe Flash Player plugin
adobe-flashplugin                   Adobe Flash Player plugin
assaultcube-data                    data files and documentation for AssaultCube
caja-dropbox                        Dropbox integration for Caja
doom-wad-shareware                  Shareware game files for the 3D game Doom

Non-free packages with status other than installed on PC_XYZ

nvidia-libopencl1-331               ( dei)  NVIDIA OpenCL Driver and ICD Loader library

Contrib packages installed on PC_XYZ

assaultcube                         realistic first-person-shooter
jdownloader                         Transitional package for jdownloader-installer
jdownloader-installer               download manager for one-click hosting sites
nvidia-settings                     Tool for configuring the NVIDIA graphics driver
pepperflashplugin-nonfree           Pepper Flash Player - browser plugin

Contrib packages with status other than installed on PC_XYZ

flashplugin-installer               ( dei)  Adobe Flash Player plugin installer

26 non-free packages, 0.9% of 2978 installed packages.
20 contrib packages, 0.7% of 2978 installed packages.
```

What does it mean by "Contrib packages"?

---

### Post by Irihapeti on 2015-07-05
> **Rytron said:**
> ....What does it mean by "Contrib packages"?

According to the vrms man page:

```
       The  packages in the contrib tree are themselves free software but have
       some dependency on non-free software for their use that make them  wor&#8208;
       thy of reporting so that their use can also be consciously considered.
```

Incidentally, if you're running things in Wine, they don't seem to be included. 

I want to point out here that I'm not a free software hard-liner, and I run this little program occasionally for entertainment as much as anything else. :)

---

### Post by Rytron on 2015-07-05
> **deadflowr said:**
> Yes that is proprietary.
The Ubuntu devs only test and build a package around the driver so that it installs without problems on Ubuntu, but they do not have access to the source code.

Synaptic does have a column, sort of, for this it's the Origin section. There should be a section within that for Restricted.
I think multiverse contains closed source software as well...
I don't know if there is a way to toggle it to show only those packages that are installed though.
(Actually when you click on the restricted repo, go to the main package listing window and toggle the Installed Version item list)

Ah yes, there are a few restricted entries, non-free, and as you said - also in Multiverse.

---

### Post by Rytron on 2015-07-05
> **Irihapeti said:**
> According to the vrms man page:

```
       The  packages in the contrib tree are themselves free software but have
       some dependency on non-free software for their use that make them  wor&#8208;
       thy of reporting so that their use can also be consciously considered.
```

Incidentally, if you're running things in Wine, they don't seem to be included. 

I want to point out here that I'm not a free software hard-liner, and I run this little program occasionally for entertainment as much as anything else. :)

You have been most helpful. I like to opt for non-proprietary software where possible. Unfortunately sometimes there maybe no non-free alternative.

---

### Post by vasa1 on 2015-07-05
> **Irihapeti said:**
> You could install vrms (sudo apt-get install vrms), which will give you a listing of non-free software when run in a terminal.
...
Neat!```
12:58 AM ~ $ vrms
        Non-free packages installed on vasa1-Inspiron-1545

oracle-java8-installer              Oracle Java(TM) Development Kit (JDK) 8

         Contrib packages installed on vasa1-Inspiron-1545

b43-fwcutter                        utility for extracting Broadcom 43xx firmware
firmware-b43-installer              firmware installer for the b43 driver

  1 non-free packages, 0.1% of 1434 installed packages.
  2 contrib packages, 0.1% of 1434 installed packages.
12:58 AM ~ $ 

```

---

### Post by Rytron on 2015-07-05
> **vasa1 said:**
> Neat!```
12:58 AM ~ $ vrms
        Non-free packages installed on vasa1-Inspiron-1545

oracle-java8-installer              Oracle Java(TM) Development Kit (JDK) 8

         Contrib packages installed on vasa1-Inspiron-1545

b43-fwcutter                        utility for extracting Broadcom 43xx firmware
firmware-b43-installer              firmware installer for the b43 driver

  1 non-free packages, 0.1% of 1434 installed packages.
  2 contrib packages, 0.1% of 1434 installed packages.
12:58 AM ~ $ 

```

Hi vasa1.

That's a damn fine system you've got there.

---

### Post by Rytron on 2015-07-12
Alas, it seems vrms also does not show proprietary deb installs like Chrome.

Nor PPAs are accounted for?

---

### Post by Bucky Ball on 2015-07-12
What fun!

```
 Non-free packages installed on TrustMini

libfaac0                            AAC audio encoder (library)
skype                               client for Skype VOIP and instant messaging service
skype-bin                           client for Skype VOIP and instant messaging service -
unrar                               Unarchiver for .rar files (non-free version)

              Contrib packages installed on TrustMini

flashplugin-installer               Adobe Flash Player plugin installer
ttf-mscorefonts-installer           Installer for Microsoft TrueType core fonts

  4 non-free packages, 0.2% of 2229 installed packages.
  2 contrib packages, 0.1% of 2229 installed packages.
```

---

### Post by Rytron on 2015-07-19
A slow but steady improvement. :-)

5-July-2015

```
26 non-free packages, 0.9% of 2978 installed packages.
20 contrib packages, 0.7% of 2978 installed packages.
```

19-July-2015

```
18 non-free packages, 0.6% of 2997 installed packages.
17 contrib packages, 0.6% of 2997 installed packages.
```

---

### Post by Rytron on 2015-07-27
I also have Chrome (just for times when I need flash since I uninstalled it from Firefox and Chromium). As mentioned before, .deb and ppas don't show up in vrms.

               ```
Non-free packages installed on XYZ_PC

faac                                AAC audio encoder (frontend)
libcg                               Nvidia Cg core runtime library
libcggl                             Nvidia Cg Opengl runtime library
libcuda1-331                        NVIDIA CUDA runtime library
libfaac0                            AAC audio encoder (library)
libfdk-aac0                         Fraunhofer FDK AAC Codec Library - runtime files
mame                                Multiple Arcade Machine Emulator (MAME)
mess-data                           Data files for the Multi Emulator Super System (MESS)
nvidia-331                          NVIDIA binary driver - version 331.113
nvidia-331-uvm                      NVIDIA Unified Memory kernel module
nvidia-opencl-icd-331               NVIDIA OpenCL ICD
oracle-java8-installer              Oracle Java(TM) Development Kit (JDK) 8
spectrum-roms                       ZX Spectrum ROMs

...

  15 non-free packages, 0.5% of 2990 installed packages.
  17 contrib packages, 0.6% of 2990 installed packages.
```

---

### Post by vasa1 on 2015-07-27
> **Rytron said:**
> I also have Chrome (just for times when I need flash since I uninstalled it from Firefox and Chromium). As mentioned before, .deb and ppas don't show up in vrms.
```

...
oracle-java8-installer              Oracle Java(TM) Development Kit (JDK) 8
....
```
I have the same entry and I got that after installing [this webupd8 ppa]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"). So software installed via a ppa seems to show up in vrms? But then I can't explain Google Chrome's absence. (I too have Google Chrome installed.)

---

### Post by mystics on 2015-07-27
Well, vrms helped me locate a couple lingering packages I thought had been purged long ago. So both neat and helpful. Nice.

And, just for fun, here's my output after getting rid of those two pesky packages:

```

mystics@XMac:~$ vrms

                Contrib packages installed on XMac

ttf-mscorefonts-installer           Installer for Microsoft TrueType core fonts
winetricks                          Microsoft Windows Compatibility Layer (winetricks)

  2 contrib packages, 0.1% of 2412 installed packages.
mystics@XMac:~$ 


```

---

### Post by Rytron on 2015-07-28
> **vasa1 said:**
> I have the same entry and I got that after installing [this webupd8 ppa]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"). So software installed via a ppa seems to show up in vrms? But then I can't explain Google Chrome's absence. (I too have Google Chrome installed.)

Just curious -- what would happen if I got rid of 'oracle-java8-installer'?

-----

Hi vasa1. VRMS does not seem to pick up deb files (e.g. chrome.deb, etc.) nor ppas -- it's a pity but maybe a future version will.

---

### Post by Rytron on 2015-07-28
> **mystics said:**
> Well, vrms helped me locate a couple lingering packages I thought had been purged long ago. So both neat and helpful. Nice.

And, just for fun, here's my output after getting rid of those two pesky packages:

```

mystics@XMac:~$ vrms

                Contrib packages installed on XMac

ttf-mscorefonts-installer           Installer for Microsoft TrueType core fonts
winetricks                          Microsoft Windows Compatibility Layer (winetricks)

  2 contrib packages, 0.1% of 2412 installed packages.
mystics@XMac:~$ 


```

Hi mystics.

Thats a tidy system you have.

---

