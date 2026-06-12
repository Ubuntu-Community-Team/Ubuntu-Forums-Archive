---
title: "Issue while installing Canon 6100 printer driver package"
date: 2014-12-28
forum: General Help
---

### Post by Bhavini on 2014-12-28
Hello, my system runs on 12.04 LTS and is 32-bit. There are four drivers which need to be installed to run the Canon 6100 series printer from my Ubuntu laptop. When I try to open the 'mg6100 series' files (they are supposed to open via Software Centre when I double-click on it) from both folders - cnijfilter-mg6100series-3.40-1-deb and scangearmp-mg6100series-3.40-1-deb - I get an error message from the Software Centre which says: 

"Dependency is not satisfiable: libtiff4" - for the mg6100-series file from the cnijfilter-mg6100series folder

"Dependency is not satisfiable: scangearmp-common (>=1.60) - for the mg6100-series file from the scangearmp-6100series folder

Common files from folders have been successfully installed by the Software Centre.

This is where I got the installation instructions for these drivers from: [http://ubuntuforums.org/showthread.php?t=1656821](http://ubuntuforums.org/showthread.php?t=1656821)

Can anyone help?

---

### Post by pdc on 2014-12-29
Hi Bhavani;

so if I suggest you run an install script that Canon provides? It should do all the work for you;

but firstly the Canon linux driver for the MG6100 series is version 3.4 so you need libtiff4 installed; (Ubuntu took away libtiff4 recently);

one gets libtiff4 from the debian respositories: click here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and I count it as 17 down the list: libtiff4 for the i386 ............so click to download and install................... ubuntu software centre should offer to do this for you

__________________________-

then for the debian package Canon provide for you: go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100301802.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100301802.html) and click to download and save what will be cnijfilter-mg6100series-3.40-1-deb.tar.gz

..................by default, it should end up in your Downloads folder .............

_________________

if you can open a terminal; and copy the commands listed below; and paste them line by line into the terminal; and hit the ENTER key after each paste .............

```
cd Downloads
```

```
tar -zxvf  cnijfilter-mg6100series-3.40-1-deb.tar.gz
```

```
cd  cnijfilter-mg6100series-3.40-1-deb
```

```
./install.sh
```

the last command will ask you for your sudo password

____________________________________________________________________________________

You mentioned ScanGearMP that Canon provide for the scanner side of things;

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100303102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100303102.html)

and click to download and save what will be scangearmp-mg6100series-1.60-1-deb.tar.gz

________________________

If you close the terminal; and then open it again please: 

the commands are: similar to the above: 

cd Downloads
tar -zxvf scangearmp-mg6100series-1.60-1-deb.tar.gz
cd scangearmp-mg6100series-1.60-1-deb
./install.sh

..........again line by line please:

to run ScanGearMP type or copy to the terminal ```
scangearmp
``` and if all is good, one sets up a launcher ..............if we cover that later?

---

### Post by Bhavini on 2015-01-01
I have not tested it yet, but it looks good. Thanks a lot, pdc. Your instructions were clear. Can we start on the launcher, or should I test the printer and scanner out first?

---

### Post by pdc on 2015-01-01
to create a launcher, if you copy these commands; one at a time; into a terminal

```
sudo apt-get install gnome-panel
```

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

then complete the box as shown in the attached thumbnail

---

### Post by Bhavini on 2015-01-01
Hi pdc, just tested the printer: strange thing, the printer keeps asking me to load more paper, although when it's connecting to a different, non-Ubuntu laptop, it's printing without issues.

---

### Post by Bhavini on 2015-01-01
I am running the printer by connecting it via USB cable, then going to 'Printers' from the search board on the top left, and using the test-page option.

---

### Post by Bhavini on 2015-01-01
Also, in the command box, what do I enter? (reference: your attached picture)

---

