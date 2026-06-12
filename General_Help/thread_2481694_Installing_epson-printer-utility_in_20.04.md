---
title: "Installing epson-printer-utility in 20.04"
date: 2022-12-06
forum: General Help
---

### Post by grey1beard on 2022-12-06
I've successfully installed the Epson drivers for my new ET-2800 printer, and copied and printed from it ok using document scanner, but I think I need to install the printer utility to get more control over the printing.
I've downloaded the utility file, and following the instructions found on tutorialforlinux.com web site, got as far as **sudo apt install gdebi gdebi-core**, then tried the next instruction **sudo gdebi epson-printer-utility*.deb** and ran into a problem.

[B]sudo gdebi epson-printer-utility*.deb
gdebi error, file not found: epson-printer-utility*.deb[/B]

The only idea I've had is that should I have changed directory to **Downloads**  first ?
It's many years since I've navigated this, so please bear with me.

John

---

### Post by MAFoElffen on 2022-12-07
Look to see what 'is' there...
```

ls $HOME/Downloads/*.deb

```

---

### Post by ajgreeny on 2022-12-07
I haven't bothered with gdebi for a very long time now as apt does more or less the same job of installing local .deb packages but has the added advantage of dealing with any dependencies required. 

It looks as if gdebi does not accept the wildcard * that you used in your command and needs the full package name so try that, but you will need the full pathway to that package so assuming it is in your home folder, not Downloads, try ***sudo gdebi ./fullname.deb*** the ./ being a shortcut for the directory from which you're running the command.

---

### Post by grey1beard on 2022-12-07
Thanks for heads up. 
While I seem to have got the package installed, trying to run it threw up a missing dependency, as your message hinted at !
So I'm inclined to use apt, as I am used to using that. Do I need to remove what I have done so far, or can I simply run **sudo apt install epson-printer-utility** ?
MTIA
John

---

### Post by ajgreeny on 2022-12-07
Sorry but I do not have and have never used an Epson printer in Linux so can't help with any details of drivers needed.

However, what was the missing dependency that you were informed about when trying to run the package you downloaded, and have you looked in the repos to see if it is easily available?

---

### Post by grey1beard on 2022-12-07
In order to check for the missing dependency, I ran the package again in terminal and got a different result, but not clear what it means.
> 
~$ sudo gdebi epson-printer-utility_1.1.1-1lsb3.2_amd64.deb
[sudo] password for john: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

Epson Printer Utility for Linux
 This is a Printer Utility program for Epson Printer Driver.
 Using this software, you can check ink levels, view error and other status... on EPSON Printers.
 For detail list of supported printer, please refer to below site:
 [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)
 .
 (Converted from a rpm package by alien version 8.86.)
Do you want to install the software package? [y/N]:
/usr/bin/gdebi:113: FutureWarning: Possible nested set at position 1
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()

I'm also trying to find out if it's possible to launch the printer utility independently, both as a means to discover if it's installed, and what adjustments are available to me.

---

### Post by mIk3_08 on 2022-12-08
> **grey1beard said:**
> In order to check for the missing dependency, I ran the package again in terminal and got a different result, but not clear what it means.
I'm also trying to find out if it's possible to launch the printer utility independently, both as a means to discover if it's installed, and what adjustments are available to me.
Maybe you will need to add 
```
sudo dpkg install <package.deb>
```
when installing the downloaded package or maybe you need to answer the package setup question with "y" then press enter. To do the exact process setup in your system. Regards and cheers.
```
Do you want to install the software package? [y/N]:
```

---

### Post by grey1beard on 2022-12-08
Story so far -

> 
john@john-HP-ProDesk-600-G1-SFF:~$ sudo dpkg -i epson-printer-utility_1.1.1-1lsb3.2_amd64.deb
(Reading database ... 213503 files and directories currently installed.)
Preparing to unpack epson-printer-utility_1.1.1-1lsb3.2_amd64.deb ...
Unpacking epson-printer-utility (1.1.1-1lsb3.2) over (1.1.1-1lsb3.2) ...
Setting up epson-printer-utility (1.1.1-1lsb3.2) ...
Install Message > Start /usr/lib/epson-backend/setup to change setup.
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
john@john-HP-ProDesk-600-G1-SFF:~$ 


Not sure if this is it.
Do the last two lines indicate I still need to do something else ?

> john@john-HP-ProDesk-600-G1-SFF:~$ epson-printer-utility
epson-printer-utility: error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory
john@john-HP-ProDesk-600-G1-SFF:~$ 

So I need to do more. If I open Synaptic Package Manager, and search for Epson, I find that the printer Utility is installed.

Just searched, and found this site, **[https://gist.github.com/bompus/b0dab76a58397b880af90cf88f281c57](https://gist.github.com/bompus/b0dab76a58397b880af90cf88f281c57)** but don't have enough experience to follow the 'instructions'.  

Very hesitant to proceed with something I don't understand !

---

### Post by mIk3_08 on 2022-12-08
Try to run the ./epson-printer-utility.sh based on your installed epson-printer-utility_1.1.1-1lsb3.2_amd64.deb. then paste the result here in this thread.  Regards and cheers.

---

### Post by MAFoElffen on 2022-12-09
I have an Epson T2760 and installed the Linux Drivers on my laptop... On the .deb I installed with 'dpkg'... On the install script, I ahd to install package lsb, then fix the broken dependencies with 
```

sudo apt install -f

```
I'm a bit disappointed with the scanner utility. It's even more basic than the default installed scanner application. I guess I expected it would be more like the Windows version of the driver, but it was not.

I have to say that the basic cups printer driver had worked just fine before this.

---

### Post by mIk3_08 on 2022-12-09
> **MAFoElffen said:**
> 
I'm a bit disappointed with the scanner utility. It's even more basic than the default installed scanner application. I guess I expected it would be more like the Windows version of the driver, but it was not.
I have to say that the basic cups printer driver had worked just fine before this. If this is the situation, I prefer to use the xsane scanner application. I've been using this xsane scanner applications for almost a decade and its pretty amazing tool to me. I also use this document scanner with same results as xsane. And if theirs a need to be edited with the scanned image I always use gimp on it. Regards and cheers.

---

