---
title: "Trying to install 32-bit Canon printer driver in Xubuntu 20.04, but fails"
date: 2021-07-11
forum: General Help
---

### Post by ardouronerous on 2021-07-11
My printer is a Canon PIXMA iP2770. The official driver is 32-bit only and while there is a driver in CUPS called Canon iP2700 series - CUPS+Gutenprint v5.3.3, it's lacking in features such as draft mode.

I created this [tutorial]("https://ubuntuforums.org/showthread.php?t=2395967&p=13798127#post13798127") for myself for installing the printer driver in 18.04, however, this tutorial no longer works in 20.04. These are my failed attempts to install the dependencies:

Enable 32-bit support:

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

Attempted to install libtiff4:

```
sudo gdebi libtiff4_3.9.7-2ubuntu1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: multiarch-support
```

According to the error message, libtiff4 needs multiarch-support, so I downloaded two versions, the 64-bit and 32-bit versions:

```
[multiarch-support_2.27-3ubuntu1.2_amd64.deb]("http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_amd64.deb")
[multiarch-support_2.27-3ubuntu1.2_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1.2_i386.deb")
```

Tried to install multiarch-support (64-bit):

```
sudo gdebi multiarch-support_2.27-3ubuntu1.2_amd64.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

Transitional package to ensure multiarch compatibility
 This is a transitional package used to ensure multiarch support is present
 in ld.so before unpacking libraries to the multiarch directories.  It can
 be removed once nothing on the system depends on it.
Do you want to install the software package? [y/N]:y
/usr/bin/gdebi:113: FutureWarning: Possible nested set at position 1
  c = findall("[[(](\S+)/\S+[])]", msg)[0].lower()
Selecting previously unselected package multiarch-support.
(Reading database ... 229736 files and directories currently installed.)
Preparing to unpack multiarch-support_2.27-3ubuntu1.2_amd64.deb ...
Unpacking multiarch-support (2.27-3ubuntu1.2) ...
Setting up multiarch-support (2.27-3ubuntu1.2) ...
```

Trying to install libtiff4 again wielded the same results: **Dependency is not satisfiable: multiarch-support**

So I tried to install multiarch-support (32-bit):

```
[URL="https://paste.ubuntu.com/p/n2xppcw692/"]sudo gdebi multiarch-support_2.27-3ubuntu1.2_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
...
Unpacking multiarch-support:i386 (2.27-3ubuntu1.2) over (2.27-3ubuntu1.2) ...
Setting up multiarch-support:i386 (2.27-3ubuntu1.2) ...[/URL]
```

Tried to install libtiff4 again, but same result: **Dependency is not satisfiable: multiarch-support**

I also tried to install libpng12:

```
[URL="https://paste.ubuntu.com/p/Mb9YDP9Qt2/"]sudo gdebi libpng12-0_1.2.54-1ubuntu1.1_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
...
(Reading database ... 230047 files and directories currently installed.)
Preparing to unpack libpng12-0_1.2.54-1ubuntu1.1_i386.deb ...
Unpacking libpng12-0:i386 (1.2.54-1ubuntu1.1) ...
dpkg: error processing archive libpng12-0_1.2.54-1ubuntu1.1_i386.deb (--install):
 unable to install new version of '/lib/i386-linux-gnu/libpng12.so.0': No such file or directory
Processing triggers for libc-bin (2.31-0ubuntu9) ...
Errors were encountered while processing:
 libpng12-0_1.2.54-1ubuntu1.1_i386.deb[/URL]
```

---

### Post by monkeybrain20122 on 2021-07-11
I think the multi-arch thing is for installing packages and distributing them [https://wiki.debian.org/Multiarch/Implementation](https://wiki.debian.org/Multiarch/Implementation)

But what if you already have the i386 libs in your binary's LD_LIBRARY_PATH? Since you don't need to compile (cross compiling is tricky) can we do something like you did for audacity in [your other thread]("https://ubuntuforums.org/showthread.php?t=2464685") to bypass the whole installation process and get it to work? 

I suppose for driver instead of using a script to start like audacity you should export PATH and LD_LIBRARY_PATH to your .bashrc or .profile like so

```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/path/to/your/driver's/lib/dir

export PATH=$PATH:/path/to/your/driver's/bin
```

---

### Post by ardouronerous on 2021-07-11
You mean, download all the i386 dependencies needed to run the printer driver and package them like I did with Audacity? I can try that.

Last year, I gave up on trying to install the printer driver and went to VM instead, so I removed 32-bit from my machine, but I'm running into a bit of a problem trying to re-enable 32-bit support though:

```
sudo dpkg --add-architecture i386
sudo apt-get update
Hit:1 http://ph.archive.ubuntu.com/ubuntu focal InRelease                      
Get:2 http://ph.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:3 http://ppa.launchpad.net/openmw/openmw/ubuntu focal InRelease
Get:4 http://ph.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:5 http://ph.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Fetched 328 kB in 3s (100 kB/s)    
Reading package lists... Done
```

I don't see i386 in sudo apt-get update's output, did Ubuntu remove all 32-bit repos?

---

### Post by monkeybrain20122 on 2021-07-11
> **ardouronerous said:**
> You mean, download all the i386 dependencies needed to run the printer driver and package them like I did with Audacity? I can try that.

Yes. Except that you want the driver to be activated automatically when the device is plugged in so you don't want to start it with a script like audacity, so you have to export the environmental variables in your .profile or .bashrc. 



> 



Last year, I gave up on trying to install the printer driver and went to VM instead, so I removed 32-bit from my machine, but I'm running into a bit of a problem trying to re-enable 32-bit support though:

```
sudo dpkg --add-architecture i386
sudo apt-get update
Hit:1 http://ph.archive.ubuntu.com/ubuntu focal InRelease                      
Get:2 http://ph.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]     
Hit:3 http://ppa.launchpad.net/openmw/openmw/ubuntu focal InRelease
Get:4 http://ph.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:5 http://ph.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Fetched 328 kB in 3s (100 kB/s)    
Reading package lists... Done
```

I don't see i386 in sudo apt-get update's output, did Ubuntu remove all 32-bit repos?

I don't think it shows the i386 packages separately, also some i386 libs might have been removed from the repo even though the 86x64 version is still available. You can check easily if you have installed synaptic, just open it and check  architecture in the left hand panel and it will show you all i386 packages.

---

### Post by linuux on 2021-07-11
OP, try these:

[https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/](https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/)

[https://itsubuntu.com/how-to-install-canon-printer-driver-in-ubuntu-20-04/](https://itsubuntu.com/how-to-install-canon-printer-driver-in-ubuntu-20-04/)

---

### Post by ardouronerous on 2021-07-11
> **monkeybrain20122 said:**
> Yes. Except that you want the driver to be activated automatically when the device is plugged in so you don't want to start it with a script like audacity, so you have to export the environmental variables in your .profile or .bashrc. 





I don't think it shows the i386 packages separately, also some i386 libs might have been removed from the repo even though the 86x64 version is still available. You can check easily if you have installed synaptic, just open it and check  architecture in the left hand panel and it will show you all i386 packages.

Okay, I saw i386 packages in Synaptic, so the 32-bit repo is downloaded into my system.

How do I download all the dependencies I need for my printer driver though. I managed to do this with Audacity with this command:

```
sudo apt-get install --download-only audacity
```

Then I copied all the dependencies from **/var/cache/apt/archives** directory. How can I do this with deb files?

---

### Post by monkeybrain20122 on 2021-07-11
OK I downloaded it, the deb.tar.gz file contains two .deb files. If you extract them there are two sub-directories data and control, the control files tell you what the dependencies are, e.g
```

Package: cnijfilter-common
Version: 3.30-1
Section: graphics
Priority: optional
Architecture: i386
Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1) | libcups2, libpopt0 (>= 1.7)
Installed-Size: 304
Maintainer: Canon Inc. <sup-debian@list.canon.co.jp>
Description: IJ Printer Driver for Linux.
 This IJ Printer Driver provides printing functions for Canon Inkjet
 printers operating under the CUPS (Common UNIX Printing System) environment.
```

There is another one for the other .deb

Now the structures of these files look complicated, even after assembling the libs you may not be able to get it to work.  Not sure if you can symlink them if you are able assemble all the pieces. This looks a lot more complex than audacity. Not sure whether you need anything in "resources".

---

### Post by ardouronerous on 2021-07-11
> **monkeybrain20122 said:**
> Do you have a link to where I can download the deb for the driver?

[https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr](https://www.canon.com.au/support/sims-content?pid=9359fa0798c54eeeadf89843512d7882&cid=87FC144EA2C54EF29F637118BB6D6231&ctype=dr)

I also did this:

```
dpkg-deb -I /home/~/canon/cnijfilter-common_3.30-1_i386.deb
 new Debian package, version 2.0.
 size 104130 bytes: control archive=1139 bytes.
     442 bytes,    11 lines      control              
    1020 bytes,    14 lines      md5sums              
      61 bytes,     5 lines   *  postinst             #!/bin/sh
     282 bytes,    15 lines   *  postrm               #!/bin/sh
 Package: cnijfilter-common
 Version: 3.30-1
 Section: graphics
 Priority: optional
 Architecture: i386
 Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1) | libcups2, libpopt0 (>= 1.7)
 Installed-Size: 304
 Maintainer: Canon Inc. <sup-debian@list.canon.co.jp>
 Description: IJ Printer Driver for Linux.
  This IJ Printer Driver provides printing functions for Canon Inkjet
  printers operating under the CUPS (Common UNIX Printing System) environment.

dpkg-deb -I /home/~/canon/cnijfilter-ip2700series_3.30-1_i386.deb
 new Debian package, version 2.0.
 size 1661288 bytes: control archive=6311 bytes.
     816 bytes,    12 lines      control              
   15711 bytes,   194 lines      md5sums              
     423 bytes,    19 lines   *  postinst             #!/bin/sh
     778 bytes,    28 lines   *  postrm               #!/bin/sh
 Package: cnijfilter-ip2700series
 Version: 3.30-1
 Section: graphics
 Priority: optional
 Architecture: i386
 Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libcupsys2 (>= 1.2.1) | libcups2, libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.10.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.12.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, cnijfilter-common (>= 3.30)
 Installed-Size: 7496
 Maintainer: Canon Inc. <sup-debian@list.canon.co.jp>
 Source: cnijfilter-common
 Description: IJ Printer Driver for Linux.
  This IJ Printer Driver provides printing functions for Canon Inkjet
  printers operating under the CUPS (Common UNIX Printing System) environment.
```

---

### Post by monkeybrain20122 on 2021-07-11
Sorry, please see my edit.

---

### Post by monkeybrain20122 on 2021-07-11
If you look through install.sh, you may be able to figure out which piece goes where if you have resemble all the libs and make the symlinks to the system accordingly. This is going to be tedious.

---

### Post by ardouronerous on 2021-07-11
This is the reason why I gave up. This is also why I wished Ubuntu would have a compatibility mode, so you can run old versions of software in Ubuntu versions where they worked.

I'll just stick to my VM method. Sorry for giving up on this.

---

### Post by ardouronerous on 2021-07-11
I'll try to search and download all the dependencies and see what happens.

---

### Post by ardouronerous on 2021-07-12
> 
[libatk1.0-0_2.28.1-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libatk1.0-0/download")         
[libc6_2.27-3ubuntu1.2_i386.deb]("https://packages.ubuntu.com/bionic/i386/libc6/download")
[libcairo2_1.15.10-2_i386.deb]("https://packages.ubuntu.com/bionic/i386/libcairo2/download")
[libcups2_2.2.7-1ubuntu2.8_i386.deb]("https://packages.ubuntu.com/bionic/i386/libcups2/download")
[libcupsys2_1.3.9-17ubuntu3.9_all.deb]("https://launchpad.net/ubuntu/jaunty/amd64/libcupsys2/1.3.9-17ubuntu3.9")
[libfontconfig1_2.12.6-0ubuntu2_i386.deb]("https://packages.ubuntu.com/bionic/i386/libfontconfig1/download")
[libglib2.0-0_2.56.4-0ubuntu0.18.04.8_i386.deb]("https://packages.ubuntu.com/bionic/i386/libglib2.0-0/download")
[libgtk2.0-0_2.24.32-1ubuntu1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libgtk2.0-0/download")
[libpango1.0-0_1.40.14-1ubuntu0.1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libpango1.0-0/download")
[libpng12-0_1.2.54-1ubuntu1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_i386.deb")
[libpopt0_1.16-11_i386.deb]("https://packages.ubuntu.com/bionic/i386/libpopt0/download")
[libtiff4_3.9.7-2ubuntu1_i386.deb]("https://old-releases.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb")
[libx11-6_1.6.4-3ubuntu0.4_i386.deb]("https://packages.ubuntu.com/bionic/i386/libx11-6/download")         
[libxcursor1_1.1.15-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxcursor1/download")         
[libxext6_1.3.3-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxext6/download")
[libxfixes3_5.0.3-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxfixes3/download")
[libxi6_1.7.9-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxi6/download")
[libxinerama1_1.1.3-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxinerama1/download")
[libxml2_2.9.4+dfsg1-6.1ubuntu1.4_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxml2/download")
[libxrandr2_1.5.1-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxrandr2/download")
[libxrender1_0.9.10-1_i386.deb]("https://packages.ubuntu.com/bionic/i386/libxrender1/download")     


These are the dependencies I was able to find. I'll try combining them like we did with Audacity.

---

### Post by ardouronerous on 2021-07-12
> **monkeybrain20122 said:**
> I think the multi-arch thing is for installing packages and distributing them [https://wiki.debian.org/Multiarch/Implementation](https://wiki.debian.org/Multiarch/Implementation)

But what if you already have the i386 libs in your binary's LD_LIBRARY_PATH? Since you don't need to compile (cross compiling is tricky) can we do something like you did for audacity in [your other thread]("https://ubuntuforums.org/showthread.php?t=2464685") to bypass the whole installation process and get it to work? 

I suppose for driver instead of using a script to start like audacity you should export PATH and LD_LIBRARY_PATH to your .bashrc or .profile like so

```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/path/to/your/driver's/lib/dir

export PATH=$PATH:/path/to/your/driver's/bin
```

How do I add this code to my .bashrc or .profile? In .bashrc, the commands end with "fi" or "esac". And in .profile, the commands end with "fi".

---

### Post by monkeybrain20122 on 2021-07-12
> **ardouronerous said:**
> How do I add this code to my .bashrc or .profile? In .bashrc, the commands end with "fi" or "esac". And in .profile, the commands end with "fi".

Add after the fi, you have to logout and login again for that to take effect.

---

### Post by ardouronerous on 2021-07-12
This is what I've added in my .bashrc:

```
# This IJ Printer Driver provides printing functions for Canon Inkjet
# printers operating under the CUPS (Common UNIX Printing System)
# environment.

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/i386-linux-gnu

export PATH=$PATH:$HOME/canon/bin
```

Didn't work, I got this error: [B]Idle - "File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory"
[/B]
I've even tried to add more paths to the libs:

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/bjlib

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/cups

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/i386-linux-gnu

export PATH=$PATH:$HOME/canon/bin
```

Same problem.

---

### Post by monkeybrain20122 on 2021-07-12
pstocanonij is an executable so it should be in your path, not sure why it is in the lib folder

Try export PATH=$PATH:$HOME/canon/bin:$HOME/lib/cups/filter

---

### Post by ardouronerous on 2021-07-12
> **monkeybrain20122 said:**
> pstocanonij is an executable so it should be in your path, not sure why it is in the lib folder  That's where it was when I extracted cnijfilter-common_3.30-1_i386.deb.  > Try export PATH=$PATH:$HOME/canon/bin:$HOME/lib/cups/filter  Didn't work, still the same message as before.

---

### Post by monkeybrain20122 on 2021-07-12
Sorry, I forgot 'canon'

```

export PATH=$PATH:$HOME/canon/bin:$HOME/canon/lib/cups/filter 
```                     


and/or

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/cups/filter
``` (this appends $HOME/canon/lib/cups/filter to all other things you set in LD_LIBRARY_PATH before so just add this line without changing all the other paths you exported before)

---

### Post by ardouronerous on 2021-07-12
> **monkeybrain20122 said:**
> Sorry, I forgot 'canon'

```

export PATH=$PATH:$HOME/canon/bin:$HOME/canon/lib/cups/filter 
```                     


and/or

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/cups/filter
``` (this appends $HOME/canon/lib/cups/filter to all other things you set in LD_LIBRARY_PATH before so just add this line without changing all the other paths you exported before)

Same result.

This is my current bashrc:

```
# This IJ Printer Driver provides printing functions for Canon Inkjet
# printers operating under the CUPS (Common UNIX Printing System)
# environment.

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/bjlib

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/cups

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/cups/filter

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/canon/lib/i386-linux-gnu

export PATH=$PATH:$HOME/canon/bin:$HOME/canon/lib/cups/filter
```

I think it could be that I need to find more dependencies, like dependencies of dependencies, since I'm working with 32-bit dependencies instead of 64-bit, that could be the reason.

The drivers have 20 dependencies all in all, so I need to find dependencies for each and every deb file. I wish there was an easy way to download all the dependencies of these 20 debs that I have.

---

### Post by monkeybrain20122 on 2021-07-12
No, this is not due to missing dependencies but because your system can't find where the files are. 

Did you say you have a VM? Boot up your VM and check where these go in the file system, then maybe you can symlink them to the right places. 

e.g it is looking for pstocanonij  in /usr/lib/cups/filter/pstocanonij and yours is in /home/your_username/canon/lib/cups/filter/pstocanonij

so do

```
sudo ln -s /home/your_username/canon/lib/cups/filter/pstocanonij /usr/local/lib/cups/filter/
```

and do similar for rest of the folders

/usr/local overrides /usr  and symlinks are cleaner than copying because that way you keep things tractable

if everything in the same folder goes to the same place then instead of linking each item you can simply do something like (in this case there is only one file inside /home/your_username/canon/lib/cups/filter/ but if you have a lot this saves you a lot of time)


```
sudo ln -s /home/your_username/canon/lib/cups/filter/* /usr/local/lib/cups/filter/
```

of course you have to create those target directories before you can symlink to them, so for the example above would be

```
sudo mkdir -p /usr/local/lib/cups/filter
```

or in this case you can do simpler by linking from the lib folder if everything in it goes to /usr/local/lib (files and subfolders and subfolders of subfolders etc) without creating it

```
sudo ln -s /home/your_username/canon/lib/* /usr/local/lib/
```

---

### Post by ardouronerous on 2021-07-12
> **monkeybrain20122 said:**
> Did you say you have a VM?

Actually, I misremembered, I have Windows XP on VM not 18.04, sorry for that.

> No, this is not due to missing dependencies but because your system can't find where the files are. 

Did you say you have a VM? Boot up your VM and check where these go in the file system, then maybe you can symlink them to the right places. 

e.g it is looking for pstocanonij  in /usr/lib/cups/filter/pstocanonij and yours is in /home/your_username/canon/lib/cups/filter/pstocanonij

so do

```
sudo ln -s /home/your_username/canon/lib/cups/filter/pstocanonij /usr/local/lib/cups/filter/
```

and do similar for rest of the folders

/usr/local overrides /usr  and symlinks are cleaner than copying because that way you keep things tractable

if everything in the same folder goes to the same place then instead of linking each item you can simply do something like (in this case there is only one file inside /home/your_username/canon/lib/cups/filter/ but if you have a lot this saves you a lot of time)


```
sudo ln -s /home/your_username/canon/lib/cups/filter/* /usr/local/lib/cups/filter/
```

of course you have to create those target directories before you can symlink to them, so for the example above would be

```
sudo mkdir -p /usr/local/lib/cups/filter
```

or in this case you can do simpler by linking from the lib folder if everything in it goes to /usr/local/lib (files and subfolders and subfolders of subfolders etc) without creating it

```
sudo ln -s /home/your_username/canon/lib/* /usr/local/lib/
```

At this point, I'm just giving up on this now. This is too tedious of an operating. I'll just stick to using my VM for printing. Thanks for the time and effort of helping me out here, I really appreciate it.

---

