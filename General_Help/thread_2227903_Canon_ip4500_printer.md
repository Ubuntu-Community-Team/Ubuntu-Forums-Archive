---
title: "Canon ip4500 printer"
date: 2014-06-04
forum: General Help
---

### Post by fairbrother89 on 2014-06-04
hi again guys,
i have bought a secondhand canon ip4500 printer. i am running ubuntu 12.04.
i have downloaded the debian driver from the canon website.
this opened "archive manager" into which appear 5 files.
do i need to extract the data from these files and if so can you please instruct me how to do this.
do i just highlight each file on the list and click *extract* from the top of archive manager.
thanks.

---

### Post by Bucky Ball on 2014-06-04
*Thread moved to **General Help**.*

If you hit the extract icon it may extract everything, or highlight them all and extract.

---

### Post by oldrocker99 on 2014-06-04
For a .deb file, try this:

```
sudo dpkg -i nameoffile.deb
```

If it gives a dependency error, then type

```
sudo apt-get -f install
```

This will install all necessary dependencies, an then finally install the driver.

Good luck!

---

### Post by deadflowr on 2014-06-04
> i have downloaded the debian driver from the canon website.
this opened "archive manager" into which appear 5 files.

Can you list the name of the five files?
Most likely one of those is a file called install.sh, maybe?
Please confirm...

---

### Post by fairbrother89 on 2014-06-04
cnijfilter-common
cnijfilter-common tar.tar
cnijfilter-4500 series
faq.pd.tar.tar
guide 4500 series-pd

these are the 5 files.

---

### Post by dragonfly41 on 2014-06-04
Is this guide enough? It worked on my Ubuntu 12.04 32bit.

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

---

### Post by pdc on 2014-06-04
so fairbrother;

this printer was first released in 2007; and back then; when ubuntu was at 7.04 systems were 32bit; if you have a 32bit system installed on 14.04 it should be good;

I had a look at the Canon ip4500 debian package [http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP4500.aspx?DLtcmuri=tcm:14-738157&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP4500.aspx?DLtcmuri=tcm:14-738157&page=1&type=download) 

and a snapshot below;

if one were installing it, the common package is installed first, then the ip4500

let us know what you are using and post back

---

### Post by fairbrother89 on 2014-06-04
thanks dragonfly.
so according to your link;

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
```

followed by

```
sudo apt-get install cnijfilter-ip4500series
```

should do the trick,

---

### Post by fairbrother89 on 2014-06-04
yes pdc. thats what i have in archive manager at the moment.
i am using 32 bit 12.04.

---

### Post by pdc on 2014-06-04
well it should all turn out the same in the end: great that you have 32bit;

if you open the folder (or directory as some call it) where the packages are:

if you right-click, can you select to install the packages? 

COMMON first

ip4500 next.........................that should be all you need to create a printer driver and see if your second-hand printer actually works!!

---

### Post by deadflowr on 2014-06-04
+1 to 32-bit, much easier in this instance
> if you right-click, can you select to install the packages? 
If you simply double click on .deb files, it'll open the software center for installation.
Of course it's the software center so it takes a while to load.
But yes, install the common first, then the other one.

---

### Post by fairbrother89 on 2014-06-05
right click gives;
open
open with
extract.

i think its the extract i wasnt sure about. as i've often read to extract before installing. maybe i'll just doublr click each one in turn. if this oopens software centre i hope it will be straightforward from then on what to do.

yes i hope the printer works ! if sure fires up ok. no blinking lights etc.:)

---

### Post by marksmarks on 2014-06-05
--- I too have a Pixma ip4500.  When I first installed it on 32 bit Ubuntu (12.04) it automatically installed (if I remember correctly) with the CUPS driver (600 dpi).  So to make things simple you may want to try that route first.


I then installed the Canon drivers (2,400 dpi)
The Canon drivers include the maintenance utility (clean heads, clean paper paths, auto power off, align head, etc.).

--- If you are interested in refilling the ink tanks, troubleshooting, cleaning the print head, .... take a look at [www.printerknowledge.com](www.printerknowledge.com), Canon Inkjet printers Forum(s).  


--- You can also perform a ** Print Nozzle Check Pattern / Self Test **from the iP4500 without using your computer.
  
(That may be useful if you want to return the printer as not working before the return period ends.  I bought one on EBay and the seller gave me a 14 day return option.)

[http://kbsupport.cusa.canon.com/system/selfservice.controller?CONFIGURATION=1011&PARTITION_ID=1&TIMEZONE_OFFSET=&CMD=PRINT_ARTICLE&ARTICLE_ID=16341](http://kbsupport.cusa.canon.com/system/selfservice.controller?CONFIGURATION=1011&PARTITION_ID=1&TIMEZONE_OFFSET=&CMD=PRINT_ARTICLE&ARTICLE_ID=16341)


--- Because you are using 12.04 you will not need to manually install Libtiff4.  However the other steps from my install experience will apply to you.   
I posted it at; [http://ubuntuforums.org/showthread.php?t=2220935](http://ubuntuforums.org/showthread.php?t=2220935)

(Ubuntu 12.04, 32 bit automatically installed libtiff4 for me.) 


Later,... :-)

---

### Post by fairbrother89 on 2014-06-06
a fabulous and generous reply markmarks for which i thank you. :P
i can report that i've just performed the standalone nozzlecheck and all is well. :KS

i 've been looking for one of this series of printers for a while as i had an ip4300 which was very easy to refil. unfortunately the printhead burnt out due to overuse.

maybe i'll just plug it in and let the cups thing load. could be all i need really. so long as if that doesnt work, it wont interfere with the specific canon drivers. but it sounds from your experience that everything is running smoothly. 

cheers !!

---

### Post by marksmarks on 2014-06-06
Well, &#8230;
  I *never actually used *the CUPS ip4500 driver.  I just happened to notice that it was installed after I first connected the ip4500 to my Ubuntu box, and started to install the Canon drivers.

---

### Post by fairbrother89 on 2014-06-07
just my luck...what now. terminal apt get instal 
libcupsys2 ????

```
Selecting previously unselected package cnijfilter-common.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 1156434 files and directories currently installed.)
Unpacking cnijfilter-common (from .../cnijfilter-common_2.80-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common
```

---

### Post by dragonfly41 on 2014-06-07
If you search around you'll find that this dependency error is due to a renaming of libcupsys2 to libcups2

[http://ubuntuforums.org/archive/index.php/t-1427098.html](http://ubuntuforums.org/archive/index.php/t-1427098.html)

---

### Post by marksmarks on 2014-06-07
Hummm,&#8230;

  I didn&#8217;t get that error when installing on Ubuntu 12.04 (32 bit).   

 Was this in Synaptic and from the Canon-trunk PPA (in my thread)?  Or from the drivers you downloaded directly from Canon?



 -- For Ubuntu 12.04, 12.10, 13.04, 13.10, 14.04;  [https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)


PS: Woops, I just reread your post and noticed, "terminal apt get install". 

 I can't say what is on your system after all you have tried... However, if you have not already, would it help to try Synaptic and the trunk PPA?  (I'm just saying, for what it's worth,... is that combo worked for me on 12.04.

---

### Post by fairbrother89 on 2014-06-07
direct from canon. :confused:

---

### Post by marksmarks on 2014-06-07
I checked my 12.04 box, Synaptic history.

I have, **libcups2 1.5.3-0ubuntu8.3**, installed.
It was updated on 5/26/14, 4/27/14, &#8230; 

I have,** cnijfilter-common 3.90~precise1**, installed on 3/7/14.
(It has not been updated, still is the current version.)  
It's depends are; [I]libc6 (>=2.7), libcupsys2|libcups2, libpopt0 (<=1.14), Zenity
[/I]

---

