---
title: "Don't know how to set up my brother printer"
date: 2014-11-26
forum: General Help
---

### Post by whedding on 2014-11-26
I am suppose to enter a command and I don't know if it is sudo or  what. I know this is a very basic question and I am a newbe which means I don't understand anything it wants me to do.  I have 1404 Ubuntu LT.The instructions say:


[LIST]
[*]Install LPR driver.The install process may take some time. Please wait until it is complete. [B]
Command  :  dpkg -i --force-all  (lpr-drivername)[/B]
[*]Check if the LPR driver is installed.[B]
Command  :  dpkg -l  |  grep  Brother[/B]
[/LIST]
and then:

[LIST]
[*]Confirm/Configure a file according to your connection.
[LIST]
[*]Check the configuration filename for your distribution.
[B]Example:
openSUSE, Ubuntu, Debian : /etc/printcap
Redhat, fedora, Mandriva : /etc/printcap.local [/B]
[*]Edit the file according to your connection.
_**For USB Connection (Default)**_
Check if the parameter of ":lp" is ":lp=/dev/usb/lp0"
_**For Network Connection**_
replace ":lp" line to the following 2 lines
:rm=(ip address of your printer)\
:rp=lp\
_**For Parallel Connection**_
replace ":lp" line to the following line
:lp=/dev/lp0\
[*]Restart the print system. [B]
Command  (for  lpr):  /etc/init.d/lpr  restart
Command  (for  lprng)  :  /etc/init.d/lprng  restart [/B]
[/LIST]
[/LIST]

---

### Post by carl4926 on 2014-11-26
You have connected the printer
Gone to 'Printers'
And it's not been added automatically?

So do you have the lpr driver file?

---

### Post by plucky on 2014-11-27
What is the Model # of your printer?

---

