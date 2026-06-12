---
title: "HP PSC 1410 support for Linux"
date: 2005-09-16
forum: General Help
---

### Post by Digitallysick on 2005-09-16
ive been looking forever for this and it works!!! try it!!

"Well, this one drove me a bit crazy. The information on HP's website and
support forums as of today is non-existant and I've read different stories on
forums about using the PSC 1310 drivers, but nothing really works. The printer
always ignores the print jobs while the printing server (CUPS) thinks they have
all been printed out successfully.

After jumping back and forth between HP's HPOJ and HPLIP drivers, I finally got
it to work. All you need is the following packages: HPOJ, HPIJS and the PPD for
the PSC 1400 series. Here is how to install it on a Debian box:

apt-get install hpoj hpijs

(this is going to ask you to probe for parallel and usb devices, answer Y to
USB and your printer will be detected as "1400 series")

As far as the PPD, it is available here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400)
(click on Download PPD)

Now you need to place that file in the right directory. In my case (as root):

cp HP-PSC_1400-hpijs.ppd /usr/share/cups/model


and restart cups (as root):

/etc/init.d/cupsys restart


Now, open the CUPS web configuration with your favorite web browser:
[http://localhost:631](http://localhost:631)

Click on "Printers", then "Add Printer" and enter a name for it (you can skip
location and description). If you are lucky, you will have your PSC detected as
shown below:



Then select HP as the printer family:



If you have installed your PPD correctly, you should have your PSC 1400 series
as an option:


Now complete the installation and print your test page. You will note that it
takes FOREVER to print a single page, which I will investigate next. For now, I
have accomplished my mission : ) "

---

### Post by Sbooob on 2008-01-28
Hello,

If you want to install your HP PSC 1410 printer, you can also visit this page :
[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
On ubuntu 6.06, all run very well.

---

### Post by fragos on 2008-01-28
Using System-> Administration-> Printing easily finds this printer with the default Ubuntu install.  You'll also find the HP Toolkit very useful.  It even provides ink levels.

---

