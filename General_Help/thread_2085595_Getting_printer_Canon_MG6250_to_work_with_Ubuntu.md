---
title: "Getting printer Canon MG6250 to work with Ubuntu?"
date: 2012-11-18
forum: General Help
---

### Post by MagnusL on 2012-11-18
Hi!

I bought the nice Canon Pixma MG6250, that prints photos nicely - from Windows. I now have installed it (network printer, ethernet cable) in my Ubuntu 12.10 workstation as well, but when I try to print a high resolution picture here, it is sent to the Printer (the Printer dialog shows it being processes, and the printer shows there is something going on) but then it just disappears, nothing gets printed. 

The driver is CUPS+Gutenprint v5.2.9. 

Any suggestions on what to do, check, try?

Magnus Larsson

---

### Post by pdc on 2012-11-18
I suggest you consider installing the printer driver that Canon supplies for the MG6200 series.......in some countries called the printer is termed the 6250, in others..6270......

go here

[http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html)

and you will be downloading the [COLOR="SeaGreen"]MG6200 series IJ Printer Driver Ver. 3.60 for Linux (debian Packagearchive)[/COLOR]

ubuntu uses debian packages so this comes down as [COLOR="SeaGreen"]cnijfilter-mg6200series-3.60-1-deb.tar.gz[/COLOR]

as you click to initiate download, your system should offer to open with archive manager........let it.....open the debian package and you should see an [COLOR="Magenta"]install.sh[/COLOR] file .........if you click on this, it should open a terminal and interact with you....and install the printer

(*the install.sh script will detect if you have 32bit or 64bit ubuntu*)

**[COLOR="Blue"]FOR THE SCANNER[/COLOR]**

..download [http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html)

install the same way

.......run by copy and paste into a terminal

> [COLOR="Red"]scangearmp
[/COLOR]
.....after that, create a launcher and google on how to do this

please post back as needed for clarifications.....

---

### Post by offgridguy on 2012-11-18
> **MagnusL said:**
> Hi!

I bought the nice Canon Pixma MG6250, that prints photos nicely - from Windows. I now have installed it (network printer, ethernet cable) in my Ubuntu 12.10 workstation as well, but when I try to print a high resolution picture here, it is sent to the Printer (the Printer dialog shows it being processes, and the printer shows there is something going on) but then it just disappears, nothing gets printed. 

The driver is CUPS+Gutenprint v5.2.9. 

Any suggestions on what to do, check, try?

Magnus Larsson
There have been a lot of threads recently involving canon printers, you might try a search, using"canon printer"  there may already be something that helps you. :)

---

### Post by MagnusL on 2012-11-19
Hi!

I tried downloading the Canon drivers, through the links you sent. Un-tarred with no problems, then tried sudo ./install.sh, and the get error "The package management system cannot be identified". 

So I manually installed the deb package, then installed the printer using this new driver as PPD. But it does not even print the test page. 

So, I tried the Michael Gruz PPA: 
[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

Installed the cnijfilter-gs6200system (after uninstalling the Canon driver), and installed the printer again. Now I get a test page printed, but photos still dies - no error msgs, just nothing printed. 

ANy help on this?

Magnus

---

### Post by pdc on 2012-11-20
can I suggest we start from the beginning again ..

if you delete ALL existing 6200 drivers ............

and let's use the terminal and if I give you commands to copy and paste:

......

..assuming you have the file [COLOR="Green"]cnijfilter-mg6200series-3.60-1-deb.tar.gz[/COLOR] in your Downloads directory: if you do not have a directory already created from this tar.gz file, if you issue the command

> [COLOR="Red"]cd Downloads[/COLOR] and then 

> [COLOR="Red"]tar -zxvf cnijfilter-mg6200series-3.60-1-deb.tar.gz[/COLOR]

.....that should create a directory called cnijfilter-mg6200series-3.60-1-deb and we next

> [COLOR="Red"]cd cnijfilter-mg6200series-3.60-1-deb[/COLOR]

then we 

> [COLOR="Red"]cd packages[/COLOR]

then we need to install the [COLOR="Blue"]COMMON PACKAGE[/COLOR] first

> [COLOR="Red"]sudo dpkg -i cnijfilter-common_3.60-1_amd64.deb[/COLOR]

..........assuming you have 64bit...........

then we install the [COLOR="Blue"]6200 PACKAGE[/COLOR]

> [COLOR="Red"]sudo dpkg -i cnijfilter-mg6200series_3.60-1_amd64.deb[/COLOR]

.......and it should all work...................... :)

---

### Post by MagnusL on 2012-11-24
Hi!

I've been away a few days, therefore not been able to tinker with this. 

Yes, that is precisely the way I installed them, when the install.sh did not succeed (I am quite familiar with both apt and dpkg). So I did it again. But I am not sure what you mean with "it all should work". So I have installed the *drivers*, but then I need to install the *printer*, right? 

When I try to do that (either in Gnome or KDE printer config), the Canon is *not* discovered, but another network printer is. So I choose manually, lpd printer, set it up at the correct ip-address, as lpd://192.168.1.17/PASSTHRU. 

THen I choose drivers, and now there are the one I installed, MG6200 series Ver 3.60 (en). Two identical entries, even. I choose one of them, and go on. But no test page is printed. However, on another computer, a test page is printed with the printer set up as lpd://192.168.1.17/PASSTHRU

So, what do I do now? Did I do something wrong in the installation?

Magnus

---

### Post by pdc on 2012-11-24
my working assumption on printer installation is that folks connect their printer via a USB cable to a standalone computer .

.........please describe your setup so we can understand it ...

..great that you are familiar with apt and dpkg ...very helpful ...

you have bought a great printer.....very enthusiastically reviewed 

[http://www.expertreviews.co.uk/printers/1287226/canon-pixma-mg6250](http://www.expertreviews.co.uk/printers/1287226/canon-pixma-mg6250)

[http://www.pcpro.co.uk/reviews/printers/372037/canon-pixma-mg6250](http://www.pcpro.co.uk/reviews/printers/372037/canon-pixma-mg6250)

---

