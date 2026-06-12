---
title: "Installing Qemu and KQemu with a script"
date: 2006-12-02
forum: General Help
---

### Post by techflat on 2006-12-02
Well, I've been using Qemu for about two month by now. I first used it without KQemu and it ran without problems, only it was kind of slow... So I installed KQemu, it worked pretty well.

I've used it to emulate Microsoft Windows, Minix 2, Minix 3, Ubuntu (yes, inside Ubuntu), Knoppix and DSL(Damn Small Linux). Emulation isn't as fast as my PC (AMD Athlon 64 3500+), but it's supposed to be somewhere between 1 and 1/2 the host's speed.

But, two weeks ago I decided to upgrade from Ubuntu 5.10 to 6.10, so I had to reinstall everything I was using. The Qemu + KQemu combo was among those things, so I decided to create a script to install it on my system and make it a package. I was inspired by these two sites:

[http://wiki.linuxbaja.org/doku.php?id=qemu_ubuntu](http://wiki.linuxbaja.org/doku.php?id=qemu_ubuntu)
[http://oui.com.br/n/content.php?article.23](http://oui.com.br/n/content.php?article.23)

I first tried to do it with Nando Florestan's script, but it had some errors so I began writing the script.

[InstallQemu.sh.zip]("http://ubuntuforums.org/attachment.php?attachmentid=20390&d=1165098814") is my script, I tested it on a fresh Ubuntu 6.10 Installation and It worked with no problems. I also tested it on the live cd, it worked as well.

So here's what you have to do to install Qemu+KQemu:

1 - [Dowload the script]("http://ubuntuforums.org/attachment.php?attachmentid=20390&d=1165098814") and unzip it (or copy it to a file from above)
2 - Make the file executable (chmod +x InstallQemu.sh)
3 - Run the script (./InstallQemu.sh)

It will take some time acording to you Internet Connection since it has to download Qemu's source, KQemu binaries and some other needed packages.

The script is very commented, so if you have any doubts, read the script.

Here it is:

```

#!/bin/bash
# This script was created by Felipe Caballero
#
# Meant (and tested) to be executed on Ubuntu 6.10, should work on 6.06 and 5.10 as well
# Probably works on regular Debian too
#
# This script installs qemu as a package, wich can be removed as a regular package
# via Synaptic or console typing: apt-get -r qemu
#
# No warranty is given, use it at your own risk - It shouldn't mess up your system anyway
#
# It will install several packages needed to compile Qemu by default, 
# it will not ask for confirmation to install this packages,
# to change this comment the variable IPBD

# This script is supposed to be run as root beacause it does administratif operations
if [ $USER != "root" -o $UID != 0 ]; then
	echo "This script is meant to be run as root"
	exit 1
fi

function clean {
	rm -rf $QEMU_HOME; rm -rf $KQEMU_HOME; rm -rf $QEMU_TAR; rm -rf $KQEMU_TAR
	echo ;
	echo "To avoid file corruption and/or IO errors, tar are deleted and directories too"
	echo "See the log files and then run the script again"
	echo ; echo ;
}

# These are the variables needed
echo "Creating Variables..." ; echo ;

QEMUVERSION=0.8.2
KQEMUVERSION=1.3.0pre9
# The following two variables are the package (file) name
QEMU_TAR=qemu-${QEMUVERSION}.tar.gz
KQEMU_TAR=kqemu-${KQEMUVERSION}.tar.gz
# The next two variables are the download url to download Qemu and KQemu
# If it doesn't work for the version of Qemu or KQemu, verify the url's
QEMUPKGSOURCE=http://fabrice.bellard.free.fr/qemu/${QEMU_TAR}
KQEMUPKGSOURCE=http://fabrice.bellard.free.fr/qemu/${KQEMU_TAR}

# Self explanatory variables
INSTALL_HOME=/home/${USER}/qemu+kqemu
QEMU_HOME=${INSTALL_HOME}/qemu-$QEMUVERSION
KQEMU_HOME=${INSTALL_HOME}/kqemu-${KQEMUVERSION}
LOG=${INSTALL_HOME}/log
ERROR_LOG=${INSTALL_HOME}/error_log
IPBD="--yes"

mkdir -p $INSTALL_HOME
cd $INSTALL_HOME

# Log and error_log are removed every time the script is executed for practical reasons
touch $LOG; rm $LOG ; touch $LOG;
touch $ERROR_LOG; rm $ERROR_LOG; touch $ERROR_LOG;

echo "To see the output, look at the log file in $INSTALL_HOME/log"
echo "To see the error output, look at the log file in $INSTALL_HOME/error_log"
echo 
# QEmu's source as well as KQemu binaries
echo "Retrieving Packages (i.e qemu source code and kqemu binaries)..."
echo "wget -nv $QEMUPKGSOURCE"
wget -nv $QEMUPKGSOURCE >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR downloading Qemu Source Package"; clean; exit 1; }
echo "wget -nv $KQEMUPKGSOURCE"
wget -nv $KQEMUPKGSOURCE >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR downloading KQemu Binary Package"; clean; exit 1; }
echo

# Downloaded packages are unpackaged
echo "unpackaging retrieved packages..."
tar xzf qemu-${QEMUVERSION}.tar.gz >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing untar of Qemu Source Package"; clean; exit 1; }
tar xzf kqemu-${KQEMUVERSION}.tar.gz >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing untar of KQemu Binary Package"; clean; exit 1; }
echo

# Necessary packages are installed
echo "Installing needed extra packages..."
echo "apt-get install gcc-3.4..."
apt-get install gcc-3.4 $IPBD >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: gcc-3.4"; clean; exit 1; }
echo "apt-get install libsdl1.2debian-all libsdl1.2-dev"
apt-get install libsdl1.2debian-all libsdl1.2-dev --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: libsdl1.2debian-all libsdl1.2-dev"; clean; exit 1; }
echo "apt-get install linux-headers-$(uname -r)"
apt-get install linux-headers-$(uname -r) --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: linux-headers-$(uname -r)"; clean; exit 1; }
echo "apt-get install checkinstall"
apt-get install checkinstall --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR installing: checkinstall"; echo "Please load \"Community maintained Open Source software (universe)\" from Synaptic Package Manager"; echo "or edit apt source files"; clean; exit 1; }
echo "apt-get build-dep qemu"
apt-get build-dep qemu --yes >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR doing: apt-get build-dep qemu"; clean; exit 1; }
echo

cd $QEMU_HOME

# Preparing compilation
echo "Runing the configuration script for Qemu..."
./configure --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)  >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR runing the configuration script for Qemu"; clean; exit 1; }
echo

# The file usb-linux.c is problematic under Ubuntu 6.10
# some changes are necessary
echo "Configuring file usb-linux.c ..."
sed -i "s/#include <linux\/compiler.h>/#include <\/usr\/src\/linux-headers-$(uname -r)\/include\/linux\/compiler.h>/" usb-linux.c >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR editing usb-linx.c"; clean; exit 1; }
echo

# Qemu gets compiled
echo "Qemu compilation"
echo "make clean..."
make clean >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make clean"; clean; exit 1; }
echo "make..."
make >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make"; clean; exit 1; }
echo

# Qemu package is made
echo "Creating Installation package and Installing it..."
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$QEMUPKGSOURCE --exclude=kqemu/install.sh >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR creating Qemu package"; clean; exit 1; }
echo

# KQemu gets installed
echo "KQemu installation"
cd $KQEMU_HOME
echo "Configuring KQemu..."
./configure >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR configuring KQemu"; clean; exit 1; }
echo "make..."
make >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make"; clean; exit 1; }
echo "make install"
make install >> $LOG 2>> $ERROR_LOG || { echo ; echo "-----> ERROR: make install"; clean; exit 1; }


```

---

### Post by fgeter on 2007-01-02
Appeared to install like a charm on my dapper Kubuntu install.  Have not tested running anything useful yet.

fgeter

---

### Post by techflat on 2007-01-02
Dear fgeter



Great!
Let me know with what you test it and if kqemu works with no problems.


Cheers

---

### Post by LucianoCamargo on 2007-01-06
i tried it, but i only got the error of apt-get not being able to build-dep qemu.
Why does it happens, and how can i fix it?
Thank you very much,
Luciano

---

### Post by jorgxus on 2007-01-07
i get the following problem:

jorg@ubuntu:/tmp$ sudo ./InstallQemu.sh
Creating Variables...

To see the output, look at the log file in /home/root/qemu+kqemu/log
To see the error output, look at the log file in /home/root/qemu+kqemu/error_log

Retrieving Packages (i.e qemu source code and kqemu binaries)...
wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz)
wget -nv [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)

unpackaging retrieved packages...

Installing needed extra packages...
apt-get install gcc-3.4...

-----> ERROR installing: gcc-3.4

To avoid file corruption and/or IO errors, tar are deleted and directories too
See the log files and then run the script again



anyone who knows how to solve it ?

---

### Post by techflat on 2007-01-07
> **LucianoCamargo said:**
> i tried it, but i only got the error of apt-get not being able to build-dep qemu.
Why does it happens, and how can i fix it?
Thank you very much,
Luciano

Hi there

Please read the error log file, since the whole output for your error should be there, it'll guide you on how to correct the error. Post it here if you want too and I'll try to help you figure out what's wrong.

Did you select "Community maintained Open Source software (universe)" from the Synaptic Package Manager? And reloaded it?

Cheers

---

### Post by techflat on 2007-01-07
> **jorgxus said:**
> i get the following problem:

jorg@ubuntu:/tmp$ sudo ./InstallQemu.sh
Creating Variables...

To see the output, look at the log file in /home/root/qemu+kqemu/log
To see the error output, look at the log file in /home/root/qemu+kqemu/error_log

Retrieving Packages (i.e qemu source code and kqemu binaries)...
wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz)
wget -nv [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)

unpackaging retrieved packages...

Installing needed extra packages...
apt-get install gcc-3.4...

-----> ERROR installing: gcc-3.4

To avoid file corruption and/or IO errors, tar are deleted and directories too
See the log files and then run the script again



anyone who knows how to solve it ?

Hi there

Please take a look at the error log, it'll help you figure out what's wrong. You could post the output from the log here too and I'll try to help you know what's wrong.

Cheers

---

### Post by paleid on 2007-01-07
Hi, I try to run your script, but gets the following error message

pme@ubuntu:~/Data/Kqemu$ sudo ./installQemu.sh 
Creating Variables...

To see the output, look at the log file in /home/root/qemu+kqemu/log
To see the error output, look at the log file in /home/root/qemu+kqemu/error_log

Retrieving Packages (i.e qemu source code and kqemu binaries)...
wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz)
wget -nv [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)

unpackaging retrieved packages...

Installing needed extra packages...
apt-get install gcc-3.4...
apt-get install libsdl1.2debian-all libsdl1.2-dev
apt-get install linux-headers-2.6.17-10-generic
apt-get install checkinstall
apt-get build-dep qemu

-----> ERROR doing: apt-get build-dep qemu

To avoid file corruption and/or IO errors, tar are deleted and directories too
See the log files and then run the script again

My error.log reads:

22:33:05 URL:[http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz) [1810909/1810909] -> "qemu-0.8.2.tar.gz" [1]
22:33:08 URL:[http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz) [190070/190070] -> "kqemu-1.3.0pre9.tar.gz" [1]
E: Beklager, du må legge inn noen kilder (nettadresser) i din «sources.list».

The last sentence says (in Norwegian):
E: sorry, you have to add som repositories in your "sources.list"

I have already selected "Community maintained Open Source software (universe)" from the Synaptic Package Manage.

Which repositories can I possibly miss?

Thanks

Paul

---

### Post by houstonbofh on 2007-01-07
Post the repositories you have.  My bet is you have deb but not deb-src somewhere.

---

### Post by jorgxus on 2007-01-08
this was my problem

jorg@ubuntu:/tmp$ sudo ./InstallQemu.sh
Creating Variables...

To see the output, look at the log file in /home/root/qemu+kqemu/log
To see the error output, look at the log file in /home/root/qemu+kqemu/error_log

Retrieving Packages (i.e qemu source code and kqemu binaries)...
wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz)
wget -nv [http://fabrice.bellard.free.fr/qemu/...3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/...3.0pre9.tar.gz)

unpackaging retrieved packages...

Installing needed extra packages...
apt-get install gcc-3.4...

-----> ERROR installing: gcc-3.4

To avoid file corruption and/or IO errors, tar are deleted and directories too
See the log files and then run the script again

the error_log said:

9:59:09 URL:[http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz) [1810909/1810909] -> "qemu-0.8.2.tar.gz" [1]
19:59:27 URL:[http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz) [190070/190070] -> "kqemu-1.3.0pre9.tar.gz" [1]
E: There are problems and -y was used without –force-yes


the log said:

Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  wamerican bochsbios libgtk1.2 libmikmod2 oaf libxml1 libdb3
  openoffice.org-thesaurus-en-us libgtk1.2-common liborbit0 xmms
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za wbritish
  openoffice.org-help-en-us liboaf0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cpp-3.4
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2180kB of archives.
After unpacking 8602kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  cpp-3.4 gcc-3.4

---

### Post by venuspcs on 2007-01-11
Simple fix for "apt-get build-dep qemu" errors

This error is caused when you have repositories in your sources.list file that:
a.) You do not have the key for, or
b.) are offline, dead or unreachable

To fix this, temporarily open a Terminal and do the following commands:

sudo -s              // Give password and it makes you root
cd /etc/apt
cp sources.list sources.list.qemu      // Makes a backup of your sources.list file
rm sources.list    // Deletes the sources.list file - Don't panic we are going to make a new one

Now open Synaptics and enable all the repositories with Universe. This will create a new sources.list Then close Synaptics and go back to your terminal and run the make command.

After it has finished compiling/installing do the following to restore your sources.list file to pre qemu form.

cd /etc/apt
rm sources.list                             // Deletes the new sources.list
cp sources.list.qemu sources.list   // Copies the backup back

---

### Post by wxnker on 2007-01-27
Great with a script that can make this install simple because I find the install of kqemu quite difficult (I'm a bit of a newbie).

But when I try to use the script I get an error.

_From terminal (root):_
[COLOR="Red"]:~/Desktop/f# ./InstallQemu.sh
Creating Variables...

To see the output, look at the log file in /home/root/qemu+kqemu/log
To see the error output, look at the log file in /home/root/qemu+kqemu/error_log

Retrieving Packages (i.e qemu source code and kqemu binaries)...
wget -nv [http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz)
wget -nv [http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz)

unpackaging retrieved packages...

Installing needed extra packages...
apt-get install gcc-3.4...
apt-get install libsdl1.2debian-all libsdl1.2-dev
apt-get install linux-headers-2.6.17-10-generic
apt-get install checkinstall
apt-get build-dep qemu

-----> ERROR doing: apt-get build-dep qemu

To avoid file corruption and/or IO errors, tar are deleted and directories too
See the log files and then run the script again
[/COLOR]

_Error log:_
[COLOR="Red"]18:26:53 URL:[http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz](http://fabrice.bellard.free.fr/qemu/qemu-0.8.2.tar.gz) [1810909/1810909] -> "qemu-0.8.2.tar.gz" [1]
18:26:56 URL:[http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz](http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz) [190070/190070] -> "kqemu-1.3.0pre9.tar.gz" [1]
E: Unable to find a source package for qemu[/COLOR]

I bet it's something simple. I have used qemu with win98 before and installing it with synaptic package manager is very simple but kqemu drives me nuts, so I'd really like if this script could work and setup both qemu and kqemu for me. :-)
What is the problem?

Regards wxnker

BTW I tried the simple solution with packages above but I got the same error when running the script so I undid the package changes again.

---

### Post by houstonbofh on 2007-01-27
You need to enable the repositories that hold qemu.  Then reload.  This is easy from synaptic.  Go to repositories, and enable universe and multiverse. (Not sure which one.  I have them both) Click reload, and search for qemu.  If you find it, you can re-run the script.

---

### Post by wxnker on 2007-01-27
> **houstonbofh said:**
> You need to enable the repositories that hold qemu.  Then reload.  This is easy from synaptic.  Go to repositories, and enable universe and multiverse. (Not sure which one.  I have them both) Click reload, and search for qemu.  If you find it, you can re-run the script.

Well I have those enabled and I can search and find qemu in synaptic package manager without problems. I still get the same error log.

but I now get these 2 errors when reloadin synaptic package manager:
1. cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
2. cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/edgy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[COLOR="Red"]
**EDIT: Fixed the cdrom problem and the script runs. I hope it works it's running right now[/COLOR]**

**[COLOR="Red"]IT WORKS![/COLOR]** Great script for us "newbies" who still lack some skill but love Ubuntu.
Thanks to **techflat **

---

