---
title: "Problem with Canon LBP7010 laser printer"
date: 2013-04-14
forum: General Help
---

### Post by leifwi on 2013-04-14
Installation seem to go OK, but printing a test page results in an error message saying "Unable to send data to printer".

sudo lsusb give the following output when printer is connected:

Apr 14 17:42:14 linux kernel: [ 5746.848153] usb 1-2: new high-speed USB device number 4 using ehci_hcd
Apr 14 17:42:14 linux kernel: [ 5746.976161] usb 1-2: device descriptor read/64, error -71
Apr 14 17:42:15 linux kernel: [ 5747.160161] hub 1-0:1.0: unable to enumerate USB device on port 2
Apr 14 17:42:15 linux kernel: [ 5747.504145] usb 4-2: new full-speed USB device number 2 using ohci_hcd
Apr 14 17:42:15 linux kernel: [ 5747.644090] usb 4-2: device descriptor read/64, error -62
Apr 14 17:42:15 linux kernel: [ 5747.888159] usb 4-2: device descriptor read/64, error -62
Apr 14 17:42:15 linux kernel: [ 5748.128134] usb 4-2: new full-speed USB device number 3 using ohci_hcd
Apr 14 17:42:16 linux kernel: [ 5748.268729] usb 4-2: device descriptor read/64, error -62
Apr 14 17:42:16 linux kernel: [ 5748.512129] usb 4-2: device descriptor read/64, error -62
Apr 14 17:42:16 linux kernel: [ 5748.752153] usb 4-2: new full-speed USB device number 4 using ohci_hcd
Apr 14 17:42:17 linux kernel: [ 5749.160149] usb 4-2: device not accepting address 4, error -62
Apr 14 17:42:17 linux kernel: [ 5749.296126] usb 4-2: new full-speed USB device number 5 using ohci_hcd
Apr 14 17:42:17 linux kernel: [ 5749.704146] usb 4-2: device not accepting address 5, error -62
Apr 14 17:42:17 linux kernel: [ 5749.704178] hub 4-0:1.0: unable to enumerate USB device on port 2

Any suggestion what to do?

---

### Post by pdc on 2013-04-14
I think most folks would perceive you as being a bit light on the details.............

> Installation seem to go OK

.........tell us more..................

I would infer you are using Ubuntu !! :P        32bit or 64bit? version 12.10 ?

from here

[http://www.canon.co.uk/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP7010C.aspx?type=download&page=1](http://www.canon.co.uk/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP7010C.aspx?type=download&page=1)

Canon Europe would seem to feel the CAPT driver is the one for you; I have an LBP printer and I see the 7018K.ppd also covers your 7010C printer .........I enclose a snapshot of the ppd

........so I sense we are heading towards guiding you on how to the install the CAPT driver.........if you have a 32bit system, life will be simpler .....................(much simpler)

but if we hear from you first?

---

### Post by leifwi on 2013-04-15
My system is the 12.04 32 bit version. I have installed the Canon CAPT driver. 
localhost:631/printers show my printer as:
 "LBP7010C-7018C (Processing, Accepting Jobs, Shared)". 
Description:	Canon LBP7010C/7018C
Location:	linux
Driver:	Canon LBP7010C/7018C CAPT (UK) (color, 2-sided printing)
Connection:	usb://Canon/LBP7010C/7018C?serial=0000A2BA6JsS
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided

When I try to print a test page the state is changed to "Sending data to printer." but nothing happens.
The printer is working fine with Windows XP on the same PC.

After installation the error log show following errors:
E [15/Apr/2013:10:21:29 +0300] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [15/Apr/2013:10:26:17 +0300] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [15/Apr/2013:11:05:30 +0300] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-Gray..' already exists
W [15/Apr/2013:11:05:30 +0300] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'LBP7010C-7018C-RGB..' already exists
W [15/Apr/2013:11:05:30 +0300] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-LBP7010C-7018C' already exists

---

### Post by pdc on 2013-04-15
thanks; 

when you say you installed the Capt driver;

I find this guide

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

the best: it is in french so if you use google translate or somesuch

in my setup, the connection is described as ccp://localhost:59787 .........as shown in the attached thumbnail

as described also here

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

eg for you it would be

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP7010C -m CNCUPSLBP7018CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

---

### Post by leifwi on 2013-04-15
Did not work:
wikberg@linux:~$ sudo /usr/sbin/lpadmin -p LBP7010C -m CNCUPSLBP7018CAPTK.ppd -v ccp://localhost:59787 -E
[sudo] password for wikberg: 
lpadmin: Unable to copy PPD file.

---

### Post by leifwi on 2013-04-15
There was an error in the file name, so now the copy command is OK but the printer is still not working.
On the cups page a new printer has appeared:
Description:	LBP7010C
Location:	
Driver:	Canon LBP7010C/7018C CAPT (UK) (color, 2-sided printing)
Connection:	ccp://localhost:59787
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided

Printing a test show status as completed, but nothing actually happens.

After rebooting, printing a test page now results in status "Can't connect to CCPD: Connection refused"

---

### Post by pdc on 2013-04-15
You tell us your problems; and I guess you are asking for comment and/or assistance;

You don't tell us what you have done and that makes it all harder;

I would have started with the latest version of the CAPT driver: 2.5 that you can get from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

then the french sivella guide has the details 

.... please tell us if your system is a standard type; ie standalone computer with printer connected by USB cable;

so the command

> sudo / usr / sbin / ccpdadmin-p LBP7010C-o / dev/usb/lp0

should have given a reply

eg

> Usage: 
   ccpdadmin [-p Printer-name-o Printer-dev-path]
   ccpdadmin [x-Remove-Printer-name]

  CUPS_ConfigPath = / etc / cups /
  LOG Path = None
  UI Port = 59787

  Entry Num: Spooler: Backend: FIFO path: Device Path: Status 
  -------------------------------------------------- --------------------------
      [0]: LBP7010C: ccp: / / localhost: 59787: / dev/usb/lp0: New! 

then sivella says to do

> sudo Service ccpd start

and then check with 

> sudo Service ccpd status 

I am a great believer in 1         2         3         4            5                6          7                8        9 ........you get the picture?

If you read Sivella tutorial again, he talks about /etc/ccpd.conf            and I enclose a snapshot of mine and my LBP is hooked to lp1 as I have 2 printers but you can check what yours says...........

---

### Post by leifwi on 2013-04-16
I am using the 2.50 version CAPT driver. My system is stand alone, printer connected with usb cable.

I have done the installation according to the instructions above and the documentation in the CAPT driver package.

sudo / usr / sbin / ccpdadmin-p LBP7010C-o / dev/usb/lp0  command gives the answer that it cannot find the command.

---

### Post by pdc on 2013-04-16
thanks;

so the command you quote 

> sudo / usr / sbin / ccpdadmin-p LBP7010C-o / dev/usb/lp0  is to install the ccpd printer daemon

............before that...................

one needs to have restarted CUPS after installing the printer drivers with the command that Canon recommend of

> [COLOR="#FF0000"]sudo /etc/init.d/cups restart[/COLOR]

and then Register the printer (PPD) with the print spooler.

> [COLOR="#FF0000"]/usr/sbin/lpadmin -p LBP7010C -m CNCUPSLBP7018CCAPTK.ppd -v ccp://localhost:59787 &#8211;E[/COLOR]

and then to install the printer daemon Canon say

> /usr/sbin/ccpdadmin -p [Printer Name] -o [Printer Device Path]

which should look like 

> sudo /usr/sbin/ccpdadmin -p LBP7010C -o /dev/usb/lp0

whereas if I understand you correctly you wrote

> sudo / usr / sbin / ccpdadmin-p LBP7010C-o / dev/usb/lp0

.........I realise now that the Sivella documentation has crucial spaces in the wrong spots...............you have spaces where you should have none.........and are lacking spaces where there should be spaces!

If I suggest you start again: delete your entry with 

> [COLOR="#FF0000"]/usr/sbin/ccpdadmin -x LBP7010C[/COLOR]

then register the printer with the spooler and then second command as I suggest above to register the ccpd print daemon

ie 

> [COLOR="#FF0000"]/usr/sbin/lpadmin -p LBP7010C -m CNCUPSLBP7018CCAPTK.ppd -v ccp://localhost:59787 &#8211;E[/COLOR]

then 

> [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -p LBP7010C -o /dev/usb/lp0[/COLOR]

then

> [COLOR="#FF0000"]sudo /etc/init.d/ccpd start[/COLOR]  to start the ccpd daemon

and 

> [COLOR="#FF0000"]captstatusui -P LBP7010C[/COLOR] ...........it should give you an OK........if so, try to print something....................

---

### Post by leifwi on 2013-04-16
Some progress, I managed to print a test page, but after that the status monitor shows that there is a 
communication error and ask to check if cable is connected and power on.

I think I had done all the things you suggested in your previous answer, but something must have gone wrong. Also now I had to change the localhost to 
59787 as suggested earlier.

So now there is only the communication error. I already tested with another cable and another usb port on my PC.
That did not help. Turning off and on the power, the status monitor shows that the printer is initializing, but after that
the communication error message returns.

---

### Post by pdc on 2013-04-16
Sivella suggests you check with 

>  [COLOR="#FF0000"]sudo service status ccpd[/COLOR]

he says you should see something like 

> Canon Printer Daemon for CUPS: ccpd: 8956 8954 

he says: If you only see one number at the end of the line

> [COLOR="#FF0000"]gksudo gedit /etc/ccpd.conf[/COLOR] ............so you open the file ccpd.conf that is in the /etc/ directory.............and can change it as your are sudo.......

add

> <Printer LBP7010C>
 DevicePath / dev/usb/lp0
</ Printer>

see his wiki to check your grammar is good: you need three lines of text............

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

then 

> [COLOR="#FF0000"]sudo service restart ccpd[/COLOR]

then 

> [COLOR="#FF0000"]sudo service status ccpd[/COLOR]

you should see something like Canon Printer Daemon for CUPS: ccpd: 8956 8954

any joy?

then try

> [COLOR="#FF0000"]captstatusui -P LBP7010C[/COLOR]

my apologies for getting the localhost number wrong: well spotted by you to correct it .......I have since edited my last post.............

---

### Post by leifwi on 2013-04-16
I probably solved the communication problem. I some time ago installed the printconf package
and that automatically installed another instance of the same printer, so I had two printers
competing for the same usb interface.
 
Thank you for your valuable help.

---

### Post by pdc on 2013-04-16
sounds very promising

so let us know in a day or two if all is good;

I never thought to ask if you had printconf installed.........never heard of it !!

---

### Post by leifwi on 2013-04-16
I rebooted my PC -> same problem again. Printer not working, cups page shows state as "Can't connect to CCPD: Connection refused".

It is working again after I run theese commands agaig:
sudo /usr/sbin/lpadmin -p LBP7010C -m CNCUPSLBP7018CCAPTK.ppd -v ccp://localhost:59787 -E
sudo /usr/sbin/ccpdadmin -p LBP7010C -o /dev/usb/lp0
sudo /etc/init.d/ccpd start

Is there a way to automatically run for example the "/etc/init.d/ccpd start" command at start-up if that is what is needed?

---

### Post by pdc on 2013-04-16
> [COLOR="#EE82EE"]Is there a way to automatically run for example the "/etc/init.d/ccpd start" command at start-up if that is what is needed?[/COLOR] 

Yes indeed; sorry if I didn't specify it earlier

from here

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

if you translate it into your favourite language

go down to section 2.3 called "Automate the detection of the printer"

and the commands are

> [COLOR="#FF0000"]gksudo gedit /etc/udev/rules.d/85-canon-capt.rules[/COLOR]...............if gedit is your text editor.........it may be [COLOR="#0000FF"]pluma[/COLOR].................

to open the file where the command is to be vested; and having opened it with the right to change it (sudo), paste in 

> KERNEL == "lp *", SUBSYSTEM == "usb", ACTION == "add", ATTRS {idVendor} == "04a9", RUN + = "/ etc / init.d / ccpd start"
KERNEL == "lp *", SUBSYSTEM == "usb", ACTION == "remove", RUN + = "/ etc / init.d / ccpd stop"

........two separate lines.............[COLOR="#0000FF"]SAVE[/COLOR].............[COLOR="#0000FF"]CLOSE[/COLOR]...........

them from Sivella's documentation you need to edit  /lib/udev/rules.d/70-printers.rules

........so........

> gksudo gedit  /lib/udev/rules.d/70-printers.rules and add what Sivella recommends

let us know how it goes; my LBP works very well each time I turn it on; it is auto-detected and prints almost immediately

---

### Post by leifwi on 2013-04-17
I added the 85-canon-capt file. Should the {idVendor} be replaced by something else?
The 70-printers.rules already exists exactly as in the french tutorial.

The printer started to work after I added the ccpd-restart.conf file.

Anyway one problem still exist. After reboot another printer is added:

"LBP7010C-7018C (Processing, Accepting Jobs, Shared)".
Description: Canon LBP7010C/7018C
Location: linux
Driver: Canon LBP7010C/7018C CAPT (UK) (color, 2-sided printing)
Connection: usb://Canon/LBP7010C/7018C?serial=0000A2BA6JsS
Defaults: job-sheets=none, none media=iso_a4_210x297mm sides=one-sided]

I am not sure if having this extra printer is a problem or not. I guess if I try to use it there will be a conflict on the usb port?

---

