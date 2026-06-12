---
title: "Problems installing print driver"
date: 2007-07-16
forum: General Help
---

### Post by festher on 2007-07-16
Hi, i have a brother dcp-340cw  and found out i needed a mfc-210c driver. i downloaded the driver (MFC210C-1.0.2-3.i386.deb) and installed it - then i went to "add printer" and Ubuntu detected my printer and the IP correctly. then i click "forward" to chose the driver but the newly added "mfc210c" driver is not showing on the list of available drivers - I tried rebooting but its still not there even though it installed withoiut errors and the files are located here and there in /usr/local/brother 

what did i do wrong?

---

### Post by phidia on 2007-07-16
Your printer is shown as supported and working at [www.linuxprinting.org](www.linuxprinting.org)

This page refrences the drivers: [http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-340CW](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-340CW)

This is a slight difference in the version # for the deb file there, but I don't know if that is just an updating thing or not? You might look at the addtional info there though.

---

### Post by festher on 2007-07-16
My problem is not to find a working driver, but to install it. I already installed a mfc210c.deb driver,  that is supposed to work but its not on the driver list when i try to "add new printer". thats my problem

---

### Post by phidia on 2007-07-16
> **festher said:**
> My problem is not to find a working driver, but to install it. I already installed a mfc210c.deb driver,  that is supposed to work but its not on the driver list when i try to "add new printer". thats my problem

Yes-I read that. I was trying to provide you with more info to work with. The driver version at the linux printing site is slightly different for the deb file.

You say you installed the driver but you don't say how. Did you use dpkg or debi to install that file?

---

### Post by festher on 2007-07-16
I am all new so i used Gdebi.

included files:

./
usr/
usr/share/
usr/share/doc/
usr/share/doc/cupswrappermfc210c/
usr/share/doc/cupswrappermfc210c/copyright
usr/share/doc/cupswrappermfc210c/changelog.Debian.gz
usr/local/
usr/local/Brother/
usr/local/Brother/cupswrapper/
usr/local/Brother/cupswrapper/cupswrapperMFC210C-1.0.2

i tried to manually select the driver and pointed to cupswrapperMFC210C-1.0.2 but it didnt work - notthe right file format i think. (it needs to be some ppd.gz or something i dont have)

im trying to install with gnome-cups-add

---

### Post by phidia on 2007-07-16
From a link at the ubuntu community documentation I found this: 

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

I think you could try to uninstall and re-install the drivers per the brother's guide there.
Let the thread know how that goes, and hope that's helpful.

---

### Post by festher on 2007-07-16
i don't think installing another version will help list the driver when adding a new printer - i don't know how this is suppose to work but i expect installed print drivers to show on the printer driver list when i wanna add a new printer, huh? sorry for my misstrust but can i be certain it will be shown under "brother printers" at all?


normally this is in windows a "click'n go" procedure so i didnt check the terminal after the installation - Since gdebi did not tell me there was a problem with the installation i didnt care to look - i did this with the new driver and it showed some errors - some files were not able to be copied due to missing folders. i manually created the /var/spool/lpd folder (lpd) and the installation ran without errors, duh! - never the less i still dont have the driver on the driver list under brother print drivers....

every OS has its strength, this is certainly not linux's - the weirdest thing is that even before i install anything, ubuntu automatically detect that my wireless network printer is a DCP-340CW IP: 10.10.10.101 - and then it completely fail to even create a folder during driver installation :smile:

another thing that freaks my out is that when i pick adriver to be installed with my "new printer" it pops up a browser windows and tell me to brows to a ppd file, WHY? i just picked a (random) driver on the list - why would it ask me to brows to a folder with some ppd file.

---

### Post by phidia on 2007-07-16
> **festher said:**
> i don't think installing another version will help list the driver when adding a new printer - i don't know how this is suppose to work but i expect installed print drivers to show on the printer driver list when i wanna add a new printer, huh? sorry for my misstrust but can i be certain it will be shown under "brother printers" at all?


normally this is in windows a "click'n go" procedure so i didnt check the terminal after the installation - Since gdebi did not tell me there was a problem with the installation i didnt care to look - i did this with the new driver and it showed some errors - some files were not able to be copied due to missing folders. i manually created the /var/spool/lpd folder (lpd) and the installation ran without errors, duh! - never the less i still dont have the driver on the driver list under brother print drivers....

every OS has its strength, this is certainly not linux's - the weirdest thing is that even before i install anything, ubuntu automatically detect that my wireless network printer is a DCP-340CW IP: 10.10.10.101 - and then it completely fail to even create a folder during driver installation :smile:

another thing that freaks my out is that when i pick adriver to be installed with my "new printer" it pops up a browser windows and tell me to brows to a ppd file, WHY? i just picked a (random) driver on the list - why would it ask me to brows to a folder with some ppd file.

It's a click and go procedure in windows because proprietary hardware makers create  proprietary software to work with microsoft's OS.  Those people rarely share their code with linux developers.

Anyway you won't know if a different version of the driver, or even re-installing the driver by the Brother procedures I provided the link to, will work unless you try.

I'm sorry that this is frustrating. I am trying to be helpful. 
If you want to argue the merits or drawbacks of linux or ubuntu there are places [here]("http://ubuntuforums.org/forumdisplay.php?f=11") for that.

---

### Post by festher on 2007-07-17
I appreciate your help very much and im not giving up just yet. though i am totally confused about the installation: lpr driver, cups driver, cupswrapper, "do this to print on network", "do this to use usb", "connect to  [http://localhost:631](http://localhost:631) "etc. the more i look the more different howto's i find. "installing brother into a cups based system" - seriously i have no idea what kind of system this is..

i can download any driver and follow any howto - but i need to know which one - the link you provided did not have an installation guide as far as i can see and those guides i find im not certain is really for my system. also i havent found any guide on how to setup of the base stuff. i think im missing some general spool-lpr-lpd or something to begin with. but i don't really know.


right now im trying to follow this guide: [http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)

my biggest problem right now is that i dont have the ppd file im asked to brows to nor the folder - i have /usr/share/cups/module - im asked to go to "modules) if this is important i dont know but at this point any little variation could mean failer for all i know.


found something important:

I'm using Debian/Ubuntu Linux. My Brother model name is not listed in the CUPS Web interface.

1.Ensure that csh/tcsh is installed.
2. Copy the PPD file from "/usr/share/cups/model/xxxxx.ppd" to "/usr/share/cups".
(where "xxxxx" stands for your model name)
2. Restart CUPS.
3.The model name should now be listed in the model list

its a jungle!


okay i dont have the ppd file so thats a big problem ofcourse - why i dont have it after installing multiple drivers i dont know.

------------------------------------------------------------------------------------------


i went through the files installed with the driver and there are no .ppd -  so no wonder i dont have a driver.

mfc210clpr-1.0.2-1.i386.deb


./
usr/
usr/bin/
usr/bin/brprintconfij2
usr/lib/
usr/lib/libbrcompij2.so.1.0.2
usr/local/
usr/local/Brother/
usr/local/Brother/inf/
usr/local/Brother/inf/brMFC210Cfunc
usr/local/Brother/inf/brMFC210Crc
usr/local/Brother/inf/brPrintListij2
usr/local/Brother/inf/brio04aa.bcm
usr/local/Brother/inf/brio04ab.bcm
usr/local/Brother/inf/brio04ac.bcm
usr/local/Brother/inf/brio04ad.bcm
usr/local/Brother/inf/paperinfij2
usr/local/Brother/inf/setupPrintcapij
usr/local/Brother/lpd/
usr/local/Brother/lpd/filterMFC210C
usr/local/Brother/lpd/psconvertij2
usr/local/Brother/lpd/rastertobrij2

---

### Post by phidia on 2007-07-17
The link you inserted in post #9 is for a networked printer. Is your printer connected to a network i.e ethernet?
This [how-to]("http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html") which was a link from the page I previously posted should work for you.
If you have problems with that please specify (step by step) what happened and any output you get.
The lp or lpr is the command line or CLI (commandline interface) core behind any/all gui printing methods.
Having said that most of what you're experiancing here is not generally necessary but Brother printers are IMO not as well supported as one would like.

---

### Post by festher on 2007-07-17
okay.

i download the mfc-210c driver to my home folder and open a terminal and do "ls" to see its really there. (mfc210clpr-1.0.2-1.i386.deb)

i start with dpkg -i --force-all and notice that "tab" dosent work, like if the command syntax isent correct. instead i type the driver name manually "mfc210clpr-1.0.2-1.i386.deb" and hit enter - result in danish. im sure you understand it:

[COLOR="Red"]dpkg: error under behandling af mfc210clpr-1.0.2.1.i386.deb (--install):
No such file or directory[/COLOR]

i remove "--force-all" and now i can use "tab" to finish the driver name so it looks right - i hit enter - result:
[COLOR="Red"]
Reading database... 124742 installed)
Gør klar til at erstatte mfc210clpr 1.0.2-1 (med mfc210clpr-1.0.2-1.i386.deb)...
Unpacking mfc210clpr...
Configuring mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists[/COLOR]

The outcome is not surprising since i installed the driver with the packet-manager several times already.

Now i just need to edit /etc/printcap

[COLOR="Red"]sudo gedit /etc/printcap:

MFC210C:\
        :mx=0:\
        :sd=/var/spool/lpd/MFC210C:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/lpd/filterMFC210C:
        :rm=10.10.10.101\ << my printer IP
        :rp=lp\[/COLOR]

one last thing is to restart lpd

 /etc/init.d/lpd restart - result:

[COLOR="Red"]thomas@thomas-laptop:~$ /etc/init.d/lpd restart
bash: /etc/init.d/lpd: No such file or directory[/COLOR]


Just to check i start gnome-cups-add and still there is no mfc210c driver to pick or anything indicating there has been any installation going on at all - tried restarting too but nothing...

im **** out of luck - it begin with errors and end with errors. heh

---

### Post by phidia on 2007-07-17
> **festher said:**
> okay.

i download the mfc-210c driver to my home folder and open a terminal and do "ls" to see its really there. (mfc210clpr-1.0.2-1.i386.deb)

i start with dpkg -i --force-all and notice that "tab" dosent work, like if the command syntax isent correct. instead i type the driver name manually "mfc210clpr-1.0.2-1.i386.deb" and hit enter - result in danish. im sure you understand it:

[COLOR="Red"]dpkg: error under behandling af mfc210clpr-1.0.2.1.i386.deb (--install):
No such file or directory[/COLOR]

i remove "--force-all" and now i can use "tab" to finish the driver name so it looks right - i hit enter - result:
[COLOR="Red"]
Reading database... 124742 installed)
Gør klar til at erstatte mfc210clpr 1.0.2-1 (med mfc210clpr-1.0.2-1.i386.deb)...
Unpacking mfc210clpr...
Configuring mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists[/COLOR]

The outcome is not surprising since i installed the driver with the packet-manager several times already.

Now i just need to edit /etc/printcap

[COLOR="Red"]sudo gedit /etc/printcap:

MFC210C:\
        :mx=0:\
        :sd=/var/spool/lpd/MFC210C:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/lpd/filterMFC210C:
        :rm=10.10.10.101\ << my printer IP
        :rp=lp\[/COLOR]

one last thing is to restart lpd

 /etc/init.d/lpd restart - result:

[COLOR="Red"]thomas@thomas-laptop:~$ /etc/init.d/lpd restart
bash: /etc/init.d/lpd: No such file or directory[/COLOR]


Just to check i start gnome-cups-add and still there is no mfc210c driver to pick or anything indicating there has been any installation going on at all - tried restarting too but nothing...

im **** out of luck - it begin with errors and end with errors. heh

> i start with dpkg -i --force-all and notice that "tab" dosent work, like if the command syntax isent correct. 

You need to preface dpkg -i and in fact most all admin commands with "sudo" If you have not been doing that it is one of the reasons the driver isn't showing. 
Although I know you used Gdebi at least once in this process and you would have _had_ to enter your admin user password for that.
See what happens when you use > sudo dpkg -i --force-all 
(the complete command as given in the how-to with sudo in front)

Ok you also said that tab or commandline completion isn't bringing up that driver. At least I think that's what you meant by "...tab doesn't work.." I can only repeat try with sudo and if that doesn't work copy and paste the output.

---

### Post by phidia on 2007-07-17
Since this is obviously complex and difficult to set up I did a little research.
The results of that [here]("http://forums.freestandards.org/read.php?24,318") appear to show that others, not specifically running ubuntu, have had the same lack of success. I've used epsons, canons, and hp printers in linux. I've only used Brothers in a work (windows) environment. 
I guess it's fair to say that some of their models don't work well with linux.
I apologize that I haven't been able to help you with this. Based on what I've read from the [linux foundation's  brother printing forums]("http://forums.freestandards.org/read.php?24,318") I would recomend asking there for help. Again sorry I couldn't be more helpful.

---

### Post by festher on 2007-07-17
I used "sudo" doing the installation, just forgot to mention it.

don't worry about it, you helped a lot. thanks

---

