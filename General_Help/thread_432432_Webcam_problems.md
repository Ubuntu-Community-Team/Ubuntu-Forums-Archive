---
title: "Webcam problems"
date: 2007-05-04
forum: General Help
---

### Post by Chang An on 2007-05-04
Hi,
I have been trying to find a suitable driver for my built in webcam on my HP dv6000 laptop.  Easycam 1 and 2 could not find the drivers.  I also installed camstream which did nothing.  This is the read out from the terminal.

Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd 

any help would be great.  Thanks

---

### Post by Kristopher on 2007-05-04
I have the same problem and the same Laptop. 

Anyone?

I could be wrong but I dont think there are Linux drivers for this......yet!

---

### Post by eXact on 2007-05-06
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2)

Think that will help...

---

### Post by Mr_Starscream on 2007-05-06
I dunno if this will work, but if the drivers for windows are in an inf format and there are sys as well, try install and using the ndiswrapper.

---

### Post by fragos on 2007-05-06
Check out [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) his driver works with hundreds of different webcams.  He lists those supported at the site.  Even if your's isn't listed it may still be supported based on the chipset used.

---

### Post by Chang An on 2007-05-09
Thanks for the link eXact.  It lead me to this page, which looks very promising. 

[http://www.arakhne.org/spip.php?article51]("http://www.arakhne.org/spip.php?article51")

I understand how to add sources to the repositories but what is the deal with having  the choice between source and binaries? Also what is the deal with adding the GPG public key into your apt key list?  This page gives you more detail about which webcams are supported.

[http://www.arakhne.org/spip.php?rubrique31]("http://www.arakhne.org/spip.php?rubrique31")

---

### Post by Sabrage on 2007-05-09
> **fragos said:**
> Check out [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) his driver works with hundreds of different webcams.  He lists those supported at the site.  Even if your's isn't listed it may still be supported based on the chipset used.

I went to the site and installed gspcav1-20070508.tar.gz and spcagui20060127.tar.gz with synaptic. But how do I start spcagui? Can't find it in any menus....

---

### Post by fragos on 2007-05-10
When you ran gspca_build to install driver the system was setup to load the driver.

---

### Post by Sabrage on 2007-05-10
I just downloaded the packages and unpacked them and installed them with Synaptic... Do I need to run the gspca_build? :confused:

---

### Post by fragos on 2007-05-10
Synaptics installs .DEB packages from repositories in its data base.  gspca is a tar ball of source code which sysnaptic can't install.    I recommend you download the tarball from the referenced site.  gspca-source, an older version, is available in Synaptic package but whats installed that way is still only source and must be compiled.  You must extract the tar ball into the directory it chooses.  Open a terminal window and cd to the directory where it was extracted.  Then "sudo ./gspca_build".  The driver will be compiled and installed.  If that process fails it wwill be bcause you're missing the Ubuntu development packages.

---

### Post by Chang An on 2007-05-11
Im still trying to figure out how to add these two lines to my apt keylist

$> gpg --keyserver [www.keyserver.net](www.keyserver.net) --recv-keys 0xBA62BC7E
$> gpg --export -a 0xBA62BC7E | sudo apt-key add -

any know how to do that?
[http://www.arakhne.org/spip.php?article51](http://www.arakhne.org/spip.php?article51)

---

### Post by Chang An on 2007-05-12
Anyone?

---

### Post by fragos on 2007-05-12
I recommend you use the Gnome interface instead of the command line.  Assuming you're running Ubuntu, goto the upper left hand corner of the screen and select System-> Administration-> Software Sources.  Use the tabs to add what you require.  That said I recommend that you seek packages from the Ubuntu repositories because going elsewhere as you are now.  To find specific packages use the search function in Synaptic.  The end result will be a more stable system.

---

### Post by Chang An on 2007-05-26
I gave up. :( Maybe by Gutsy Ubuntu will be more friendly towards webcams.

---

### Post by whistl3r on 2007-09-29
Did you try: [http://lsb.blogdns.net/ry5u870](http://lsb.blogdns.net/ry5u870)

---

