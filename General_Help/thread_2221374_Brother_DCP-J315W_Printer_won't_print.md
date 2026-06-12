---
title: "Brother DCP-J315W Printer won't print"
date: 2014-05-01
forum: General Help
---

### Post by guilherme6 on 2014-05-01
I have followed these steps to install the printer correctly:

[http://askubuntu.com/questions/260621/installing-brother-dcp-j315w](http://askubuntu.com/questions/260621/installing-brother-dcp-j315w)

It seems that the printer is configured correctly, though when I try to print anything it says the information was sent successfully to the printer, but nothing is printed. The printer display is suppose to remain active for a while indicating it's buffer is being loaded for a print but instead it gets activated for a brief while and then off again.

---

### Post by plucky on 2014-05-02
> **guilherme6 said:**
> I have followed these steps to install the printer correctly:

[http://askubuntu.com/questions/260621/installing-brother-dcp-j315w](http://askubuntu.com/questions/260621/installing-brother-dcp-j315w)

It seems that the printer is configured correctly, though when I try to print anything it says the information was sent successfully to the printer, but nothing is printed. The printer display is suppose to remain active for a while indicating it's buffer is being loaded for a print but instead it gets activated for a brief while and then off again.

Open a terminal and post output for ```
dpkg -l | grep -i brother
``` This will show what drivers are installed for the printer.


Found [This](http://ubuntuforums.org/showthread.php?t=1921644&highlight=DCP-J315W) with a forum search.

Good Luck

---

### Post by guilherme6 on 2014-05-03
This was the output:

> ii  balazarbrothers                                       1.0~rc1-4.2                                         all          3D puzzle game
ii  brother-cups-wrapper-ac                               1.0.3-1-0ubuntu3                                    amd64        Cups Wrapper drivers for ac brother printers
ii  brother-cups-wrapper-bh7                              1.0.0-10-0ubuntu6                                   amd64        Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common                           1.0.0-10-0ubuntu6                                   amd64        Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                            1.2.1-0ubuntu4                                      amd64        Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser                            2.0.1-2-0ubuntu6                                    amd64        Cups Wrapper drivers for laser brother printers
ii  brother-cups-wrapper-laser1                           1.0.2-1-0ubuntu8                                    amd64        Cups Wrapper drivers for laser1 brother printers
ii  brother-cups-wrapper-mfc9420cn                        1.0.0-1-0ubuntu6                                    amd64        Cups Wrapper drivers for mfc9420cn brother printers
ii  brother-lpr-drivers-ac                                1.0.3-1-0ubuntu4                                    amd64        LPR drivers for ac brother printers
ii  brother-lpr-drivers-bh7                               1.0.1-1-0ubuntu6                                    amd64        LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common                            1.0.0-4-0ubuntu3                                    amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                             1.2.0-2-0ubuntu5                                    amd64        LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser                             2.0.1-3-0ubuntu5                                    amd64        LPR drivers for laser brother printers
ii  brother-lpr-drivers-laser1                            1.0.0-3-0ubuntu6                                    amd64        LPR drivers for laser1 brother printers
ii  brother-lpr-drivers-mfc9420cn                         1.0.0-3-0ubuntu4                                    amd64        LPR driver for mfc9420cn brother printer
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan3                                               0.2.11-5                                            amd64        Brother Scanner Driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers



I'll try the way proposed in the link and post the results.

EDIT: I've tried the way proposed in here [http://ubuntuforums.org/showthread.php?t=1921644&highlight=DCP-J315W](http://ubuntuforums.org/showthread.php?t=1921644&highlight=DCP-J315W) but I wasn't able to even complete step 1. I went to software center and tried to install ia32-libs from there via apturl and just couldn't.

---

### Post by pdc on 2014-05-03
Brother do now offer an installer: what you want is a driver created that will initiate a successful printer: 

can I suggest you try the Brother installer; it should do all the work for you; it will create a title that may differ from what you already have: but theirs should work..... so before you start this, if you list what you have; so you can pick the new name that the Brother install creates; when you use the printer;

go here [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=dcpj315w_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=dcpj315w_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625) and you will download [COLOR="#008000"]linux-brprinter-installer-2.0.0-1.gz[/COLOR] and if you choose to download and SAVE 

the commands (if you open a terminal and paste the commands from below into it) .....are................

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 DCP-J315W[/COLOR]

...............according to Brother, that should let their installer create a printer driver for you (and I think also a scanner driver)

(One can always delete these entries and start again ................if you paste [http://localhost:631/printers/](http://localhost:631/printers/) into a browser (or click on the link) it opens cups and I mention that here so you may feel more comfortable about the ability to delete printer entries as needed

---

### Post by guilherme6 on 2014-05-08
I've tried this last method. It created a printer for me, but it's URI was set tu usb://etc but I'm trying to access the printer using wifi. What should I do? I tried changing the URI to the printer's IP adress using with http protocol and it didn't work (not sure if it was supposed to work).

---

### Post by pdc on 2014-05-08
on this page [http://support.brother.com/g/s/id/linux/en/instruction_prn1a.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_prn1a.html?c=us_ot&lang=en&redirect=on)

Brother suggest how to configure a network printer using CUPS [http://localhost:631/printers/](http://localhost:631/printers/)              If you click on the existing settings for your printer, you should be able to alter them 

...........was the printer joined to the computer by USB cable when you ran the install script? ................

---

