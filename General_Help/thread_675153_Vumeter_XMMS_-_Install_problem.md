---
title: "Vumeter XMMS - Install problem"
date: 2008-01-22
forum: General Help
---

### Post by dan0z on 2008-01-22
Hi,

I seem to struggling to install the vumeter plugin for XMMS. I have downloaded the source but am getting an error while trying to compile (see below). I am also getting the same error while trying to install XMMS 1.2.11. Any help would be much appreciated.

```

checking for GLIB - version >= 1.2.10... yes
checking for xmms-config... no
checking for XMMS - version >= 1.2.9... no
*** The xmms-config script installed by XMMS could not be found.
*** If XMMS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XMMS_CONFIG environment variable to the
*** full path to xmms-config.
configure: error: *** XMMS >= 1.2.9 not installed - please install first ***
```

I currently have version 1.2.10 installed.

Thanks

Dan

---

### Post by saurabh kakkar on 2008-03-11
> **dan0z said:**
> Hi,

I seem to struggling to install the vumeter plugin for XMMS. I have downloaded the source but am getting an error while trying to compile (see below). 

```

checking for GLIB - version >= 1.2.10... yes
checking for xmms-config... no
checking for XMMS - version >= 1.2.9... no
*** The xmms-config script installed by XMMS could not be found.
*** If XMMS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XMMS_CONFIG environment variable to the
*** full path to xmms-config.
configure: error: *** XMMS >= 1.2.9 not installed - please install first ***
```

I currently have version 1.2.10 installed.

Thanks

Dan

I m also getting the same error in installing vumeter plugin for my XMMS 1.2.10 Can anyone plz help me I want to install this skin on my xmms [http://www.gnome-look.org/content/show.php?content=41102&forumpage=2](http://www.gnome-look.org/content/show.php?content=41102&forumpage=2) 
plz help

---

### Post by martinx73 on 2008-03-31
Ubuntu 7.10 25 Marzo 2008

install with synaptic
xmms
xmms-dev
gcc
gcc-4.2
gawk
libgdk-pixbuf-dev
libglib1.2-dev

download the  plugin
[http://vumeterplugin.sourceforge.net/download.php](http://vumeterplugin.sourceforge.net/download.php)

decompress
move to decompress folder

with a  terminal
sudo ./configure
sudo make
sudo make install
sudo mkdir /usr/share/xmms/VU_Meter_skins
sudo cp -R skins/* /usr/share/xmms/VU_Meter_skins

load xmms
press Control+v
enable the  plugin
click in configure
go to  skins
selecti skin

PD
sorry, my english is very basic

---

