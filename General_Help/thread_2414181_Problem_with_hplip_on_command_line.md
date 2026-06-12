---
title: "Problem with hplip on command line"
date: 2019-03-06
forum: General Help
---

### Post by JimLS on 2019-03-06
Wanting to install hplip on a Ubuntu 14.04 box (I know, it's old, but it has other things on it that will take some effort to move and it IS supported for another month or so...) so I can run hp-clean periodically (once a week?) to keep the little used inkjet from drying out.  I have an OfficeJet4655 which appears to install as 4650.

sudo apt-get install python-qt4
sudo apt-get install hplip

hp-setup  (did not find inkjet)
hp-doctor   (seems to have found inkjet - selected only multifunction devices to skip laser printer)
hp-setup  (now it worked)

Need to test from command line so I can run this from cron.  So 

lpstat -a  to get printer names

lpr -P OfficeJet_4650 /usr/share/cups/data/default-testpage.pdf     works and prints test page

Not quite clear on how to format hp-clean command line...

hp-makeuri 192.168.15.180 
returns:  error:  Device not found

I can ping that address successfully.

Haven't been able to get hp-clean to run trying various command line variations.

I suppose I could just go with the lpr command but would like to get hp-clean and other related programs working.

---

### Post by dave157 on 2019-03-06
Why do you need to install hplip its already installed?

---

### Post by JimLS on 2019-03-07
Yes, it's installed now but not working.  The commands I listed are the ones I ran to install and test.

---

### Post by dave157 on 2019-03-08
I did a search on Linuxprinting.org and this is what it has for the  HP 4650. 

[http://www.openprinting.org/printer/HP/HP-OfficeJet_4650](http://www.openprinting.org/printer/HP/HP-OfficeJet_4650)

This can be outdated my HP Envy 5530 is not on there but works normally.

---

### Post by dave157 on 2019-03-08
This is the supported printer list for HP ubuntu.

[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

I looked as nd it does not list your printer officejet 4655.

---

### Post by ajgreeny on 2019-03-08
It says it is fully supported on the info that I see at that site linked to by dave157:
```
HP OfficeJet 4655 All-in-one Printer 	3.15.9 	No 	Full 	Color 	Yes 	Yes 	USB, Network 	 
```
I do not remember the hplip version for 14.04 but if, as I suspect, it is earlier than the 3.15.9 mentioned above, you will possibly need to update hplip manually.

Instructions for doing so are here at [https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)
It takes a while and possibly needs a few dependencies to be installed but that is all done automatically when you execute the hplip-*version*.run in terminal as shown.

---

### Post by JimLS on 2019-03-09
hplip is 3.17.4

hp-doctor updates the version I think and has been run before the OP.

---

### Post by JimLS on 2019-03-10
hp-doctor gives some errors that indicate all is not right...

At the start is give error:

error: This distro (i.e ubuntu  14.04) is either deprecated or not yet supported.
The diagnosis is limited on unsupported platforms. Do you want to continue?(y=yes*, n=no):

When continue is selected it reports a recent version:

HPLIP-Version: HPLIP 3.17.4
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  14.04 version



Later:

OfficeJet_4650
--------------
Type: Printer
Device URI: hp:/net/OfficeJet_4650_series?ip=192.168.15.180
PPD: /etc/cups/ppd/OfficeJet_4650.ppd
PPD Description: HP Officejet 4650 Series, hpcups 3.17.4                                                                                                       Printer status: printer OfficeJet_4650 is idle.  enabled since Sun 03 Mar 2019 08:22:35 AM CST
error: Unsupported model: OfficeJet_4650_series
error: Communication status: Failed

And some additional errors.  Tried running it with and without gui with similar results.  Not sure why it reports it is depreciated.  And 4650 should be supported.

---

### Post by brian_p on 2019-03-11
Your OfficeJet 4655 installs as a 4650 because it belongs to the OfficeJet 4650 Series. For what you want to do stop fussing with hp-clean and read the device's manual. Cleaning can be done from the control panel display; look in the Tools section.

---

