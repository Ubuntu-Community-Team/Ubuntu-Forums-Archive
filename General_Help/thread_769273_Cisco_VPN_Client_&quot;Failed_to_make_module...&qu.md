---
title: "Cisco VPN Client &quot;Failed to make module...&quot;"
date: 2008-04-26
forum: General Help
---

### Post by igfud on 2008-04-26
Hello,

I am attempting to install the Cisco VPN client (distributed by my school), but I am receiving errors.  Below I've copied the output from the terminal.  I am running Ubuntu 8.04.

```

igfud@igfud-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/igfud/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/igfud/Desktop/vpnclient/linuxcniapi.o
In file included from /home/igfud/Desktop/vpnclient/Cniapi.h:15,
                 from /home/igfud/Desktop/vpnclient/linuxcniapi.c:31:
/home/igfud/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/igfud/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/igfud/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
igfud@igfud-laptop:~/Desktop/vpnclient$ 
```

Thanks,
igfud

---

### Post by sqrl on 2008-04-26
Try 
   [http://www.longren.org/2007/05](http://www.longren.org/2007/05) /17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/

just worked for me

---

### Post by ndeburn on 2008-04-26
The Fiesty Link above does not work for me with 8.04.  I did however find a fix for 8.04,  Here are the instructions,

1. Delete your current vpn installation files.

2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz]("http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff")

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!

P.S. Thanks Tuxx-Home.

---

### Post by igfud on 2008-04-26
The installation instructions worked great - thanks a bunch for the help!

After installation, I ran the "/etc/init.d/vpnclient_init start" command as specified by the terminal.  According to my school, I should use the command "vpnclient connect cuboulder" for off campus connections.  When I run this command, I receive the following output in the terminal:

```
igfud@igfud-laptop:~/Desktop/vpnclient$ vpnclient connect cuboulder
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Config file directory: /etc/opt/cisco-vpnclient

The profile specified could not be read.

```

I guess this makes enough sense; the school's copy of the software must have been modified to accept "cuboulder" as an alias for the VPN's IP address and other settings.

To remedy this, I tried reinstalling the old version of the program following the instructions for the .diff file.  Installation went just fine, but I still receive the same error when trying to connect.

If it would be of assistance to anyone, here is the link to setting up VPN for Linux on the school's IT site:
[http://www.colorado.edu/its/vpn/linux.html](http://www.colorado.edu/its/vpn/linux.html)

Thanks,
igfud

---

### Post by igfud on 2008-04-27
Cancel my previous post.... I tried uninstalling the VPN client *then* installing my school's copy.  Works great; I'm using it now. :guitar:

thanks,
igfud

---

### Post by zzottt on 2008-04-29
Thanks ndeburn

that worked for me

---

### Post by dl1000v on 2008-04-29
Hi All,

I'm having the same problem, followed the steps carefully, and am experiencing the same error. The patch installs fine. Could it be cause I'm running 8.04 64-bit?

Thanks!

---

### Post by dgavenda on 2008-04-30
ndeburn,

Worked for me too.  Much thanks!

Dan

---

### Post by ndeburn on 2008-04-30
> **dl1000v said:**
> Hi All,

I'm having the same problem, followed the steps carefully, and am experiencing the same error. The patch installs fine. Could it be cause I'm running 8.04 64-bit?

Thanks!

The 64-bit could be the problem.  The client is for 64bit as well, but the patch may not have been written for such.  

You can see in the error that the file does not exist.  That is because that file was moved in the newer kernels.  If it is failing because of the 64bit, it should fail in a different file or location.

Start over without patching, record the error.
Start over again and patch, record the error.
See if the 2 are different.

If they are, then it probably won't work on 64-bit as I outlined.  If they are the same, I would look at the way you are patching the install files.

---

### Post by cybil on 2008-04-30
thanks ndeburn, that worked great!

---

### Post by halfguard on 2008-04-30
> **ndeburn said:**
> The Fiesty Link above does not work for me with 8.04.  I did however find a fix for 8.04,  Here are the instructions

Thanks, ndeburn! This worked great!

---

### Post by jkilgrow on 2008-05-01
Hmmm....seemed to patch okay. But now I'm getting the following:

```

/home/jkilgrow/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/home/jkilgrow/vpnclient/interceptor.c:655: warning: assignment makes integer from pointer without a cast
/home/jkilgrow/vpnclient/interceptor.c:676: warning: passing argument 2 of ‘CniNewFragment’ makes pointer from integer without a cast
/home/jkilgrow/vpnclient/interceptor.c: In function ‘do_cni_send’:
/home/jkilgrow/vpnclient/interceptor.c:794: error: invalid operands to binary -
make[2]: *** [/home/jkilgrow/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/jkilgrow/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


```

any ideas?

---

### Post by jsn on 2008-05-01
> **jkilgrow said:**
> Hmmm....seemed to patch okay. But now I'm getting the following:

```

/home/jkilgrow/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/home/jkilgrow/vpnclient/interceptor.c:655: warning: assignment makes integer from pointer without a cast
/home/jkilgrow/vpnclient/interceptor.c:676: warning: passing argument 2 of ‘CniNewFragment’ makes pointer from integer without a cast
/home/jkilgrow/vpnclient/interceptor.c: In function ‘do_cni_send’:
/home/jkilgrow/vpnclient/interceptor.c:794: error: invalid operands to binary -
make[2]: *** [/home/jkilgrow/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/jkilgrow/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


```

any ideas?

Bump for same error..  I hate you M$ for making me weak!!

---

### Post by jsn on 2008-05-02
> **jsn said:**
> Bump for same error..  I hate you M$ for making me weak!!

OK got it.. If you are still having issues.. Delete all your vpn downloads and get the ones from this thread,. 

Extract the "vpnclient-linux-x86...." to your home folder (you can use the Archive manager)

Then copy the .diff file (patch) into the new vpnclient folder in your home folder.

cd into the vpnclient folder "cd vpnclient"

then do the 

1. sudo apt-get install patch
2. patch <./vpnclient-linux-2.6.24-final.diff
3. sudo ./vpn_install

It installed right away for me.

Then you can put your .pcf file into /etc/opt/cisco-vpnclient/Profiles/ folder

To connect you open a terminal and type "sudo vpnclient connect (your pcf file name)

If it fails and says something about something not loaded.. then type
sudo /etc/init.d/vpnclient_init start  (this starts the vpn "service" or what ever it is called)

then try to connect again..

You can add a icon to your desktop (Launcher) to do this for you.. Thats how I roll..

I hope this works for you.. I am 3 months into Ubuntu only.. So i hope this helps other newbies.

*edit* I am just restating the info from this tread hopfully in a way that helps other newbies..  So thanks everyone!

---

### Post by gmanpsycho on 2008-05-05
Thanks ndeburn,

Those instructions worked for me!!!

---

### Post by Odell on 2008-05-11
JSN, got the diff file to patch, but when I went to install I got the following:

Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/ian/Download/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/ian/Download/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ian/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I'm a noob so I figured the defaulrts would be correct. Any ideas from you guys would be appreciated.

---

### Post by ndeburn on 2008-05-12
> **Odell said:**
> JSN, got the diff file to patch, but when I went to install I got the following:

Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/ian/Download/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/ian/Download/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ian/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I'm a noob so I figured the defaulrts would be correct. Any ideas from you guys would be appreciated.
Odell, it looks like you are not using the correct vpn client version for the patch.  I would go back through the steps and make sure to download the vpnclient as well.  Also, when you extract the vpnclient, extract directly to your home folder.  I find I have less problems compiling when not deep in my home folder.  You can have folders with spaces, and other strange stuff.  Maybe it is just me!   

Also, a little trick and why JSN had to correct me originally.  Do a "sudo bash" before the steps.  You say you are a noob, that gives you a root prompt, only use it for compiling.  Use my steps, without the sudo.  After you are done, type exit, that takes you back to $.

---

### Post by twizler on 2008-06-13
ndeburn fixed it for me ALSO ndeburn is the MAN !!! 

>  Re: Cisco VPN Client "Failed to make module..."
The Fiesty Link above does not work for me with 8.04. I did however find a fix for 8.04, Here are the instructions,

1. Delete your current vpn installation files.

2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz](http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz)

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovp....24-final.diff](http://projects.tuxx-home.at/ciscovp....24-final.diff)

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!

P.S. Thanks Tuxx-Home.
ndeburn is offline   	Reply With Quote

if you have been doing what i did and installed like 10 times... just do 

a vpn_uninstall ... then do the above starting fresh. 

WORKS!!!

---

### Post by geezerone on 2008-06-30
Got it to work but is there a GUI that can be used with the above?

---

### Post by ndeburn on 2008-06-30
No GUI, command line only.  Put the pcf files in /etc/Cisc.../Profiles

Make sure the pcfs are writable.

Make sure your kernel module is loaded.  It does not load automatically with Ubuntu.  The startup script is in /etc/init.d/vpnclient_init.

use this syntax:
vpnclient connect <name of the pcf without the .pcf>

If you do not have a pcf, copy and edit the sample.pcf to your needs.

---

### Post by geezerone on 2008-06-30
Ok thanks. What process does the vpn show up as in case you want to end it?

My ifconfig file shows [I]cipsec0

**EDIT: **[/I]```
vpnclient disconnect
```in terminal which ends session.

---

### Post by ndeburn on 2008-06-30
it shows under vpnclient although I have never had to kill it.  If you want to disconnect, type the vpnclient disconnect.  Or do what I do and Press Ctrl C whenever you want to terminate the connection.

---

### Post by hackmeister on 2008-07-01
> **geezerone said:**
> Got it to work but is there a GUI that can be used with the above?

Yes there is. I found gvpndialer on sourceforge and created an Ubuntu package for HH(32-bit):
[http://pdavila.homelinux.org:8080/gvpndialer_1.1-1_i386.deb](http://pdavila.homelinux.org:8080/gvpndialer_1.1-1_i386.deb)

Unfortunately it doesn't automatically create a menu entry yet. If I have some time I'll see if I can get the installer to do it.

---

### Post by amartz on 2008-07-02
7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!


Following all the above steps (uname -r = 2.6.24-19-generic), and running ./vpn_install, I get the following after the questions:

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/art/Documents/Market America/Cisco VPN Client - Linux/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `America/Cisco'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can anybody suggest anything to try?
Art

---

### Post by geezerone on 2008-07-03
> **amartz said:**
> 7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!


Following all the above steps (uname -r = 2.6.24-19-generic), and running ./vpn_install, I get the following after the questions:

Making module
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/art/Documents/Market America/Cisco VPN Client - Linux/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `America/Cisco'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can anybody suggest anything to try?
Art

I had the same problem. There is an extra full-stop in step 7 of the guide. 

Use: ```
<./vpnclient-linux-2.6.24-final.diff
``` and this will do the trick.

---

### Post by amartz on 2008-07-03
> **geezerone said:**
> I had the same problem. There is an extra full-stop in step 7 of the guide. 

Use: ```
<./vpnclient-linux-2.6.24-final.diff
``` and this will do the trick.

You lost me there.  Am I supposed to change permissions and make this file executable and run it?  The file *is* there.
Art

---

### Post by geezerone on 2008-07-03
```
2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz](http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz)

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovp....24-final.diff](http://projects.tuxx-home.at/ciscovp....24-final.diff)

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <./vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files)

8. Now install successfully as you regularly would!
```Try this again and see how you get on.

---

### Post by amartz on 2008-07-03
7. Type: patch <./vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files)


OK.  I did do exactly that.  When I get out of some meetings later today, I'll try it again.  Thanks for the response!

---

### Post by amartz on 2008-07-03
Try this again and see how you get on.[/QUOTE]

Well, I went for plan B, and I'll be darned if it didn't work! I installed through the Ubuntu package manager "vpnc", and then "kvpnc". kvpnc showed up on the Applications>Internet menu, and had an option to import the Cisco pcf file that I already had working on the vista side of my laptop with the 5.0 Cisco client. So I imported, it offered to connect, and after telling it to use the correct domain (which it already had, just grayed out), it connected me right in. The telnet worked fine. Now I just need to figure out how to point Nautilus at the windows shares.
Art

---

### Post by cyrano_says on 2008-07-04
[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

I had the same problem. I used this and it worked for me.


> **Odell said:**
> JSN, got the diff file to patch, but when I went to install I got the following:

Directory containing linux kernel source code [/lib/modules/2.6.24-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-16-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-16-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/ian/Download/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/ian/Download/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/ian/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I'm a noob so I figured the defaulrts would be correct. Any ideas from you guys would be appreciated.

---

### Post by CritiKaster on 2008-07-09
> **ndeburn said:**
> The Fiesty Link above does not work for me with 8.04.  I did however find a fix for 8.04,  Here are the instructions ...

Thanks a bunch, ndeburn, I experienced the exact symptoms your describing and after following your instructions, i now have a working vpn client. :)

---

### Post by dl1000v on 2008-07-28
> **amartz said:**
> Try this again and see how you get on.

Well, I went for plan B, and I'll be darned if it didn't work! I installed through the Ubuntu package manager "vpnc", and then "kvpnc". kvpnc showed up on the Applications>Internet menu, and had an option to import the Cisco pcf file that I already had working on the vista side of my laptop with the 5.0 Cisco client. So I imported, it offered to connect, and after telling it to use the correct domain (which it already had, just grayed out), it connected me right in. The telnet worked fine. Now I just need to figure out how to point Nautilus at the windows shares.
Art[/QUOTE]



Amartz, you rock! I've been wrestling with this for months, the Cisco vpn client was the only thing I couldn't get to work on my 64-bit notebook. I installed these packages, imported my Cisco profile, and it's been working perfectly ever since. Thank you!

---

### Post by txcrackers on 2008-07-29
*network-manager-vpnc* worked just fine for me (whereas before I've always had to do the find/download/compile/install routine). I just went to [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode) to get the encrypted Cisco password from the .pcf file and used that (plus my regular credentials) and I go in from the NetworkManager system-tray icon.

---

### Post by amartz on 2008-08-06
> Amartz, you rock! I've been wrestling with this for months, the Cisco vpn client was the only thing I couldn't get to work on my 64-bit notebook. I installed these packages, imported my Cisco profile, and it's been working perfectly ever since. Thank you!

I've since switched. I installed "network-manager-vpnc", a vpnc plugin. It puts the vpn option right on the nm-applet as a drop-down menu option. It's very convenient that way. The only thing it didn't do that the kvpnc did is read the existing Vista-side profile record. I had to get the workgroup password from the network people to complete the setup, but now it works fine.
Art

---

### Post by jonathan.david.lim on 2008-08-26
All right, so I got vpnclient up and running and copied my school's .pcf file into the Profiles folder. However, everytime I type "vpnclient connect dubois", I get a message saying "No connection exists." Everything else works fine, so I've no idea what I should do. Any ideas?

---

### Post by jonathan.david.lim on 2008-08-26
Hmm, nevermind. I rebooted and it almost connects, but now it gives the following:

```
Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Unable to resolve server address.
```

What's going on?

---

### Post by 1/0 on 2008-09-04
I'm running Xubuntu 64bits and got the same problem. What solved it for me was the following (found the solution [here](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)):

* Change the line with the cflags in the makefile from this:

```

    CFLAGS += -mcmodel=kernel -mno-red-zone

```

to this:

```

    EXTRA_CFLAGS += -mcmodel=kernel -mno-red-zone

```

* From the vpnclient folder download and apply the following patches:

```

    wget lamnk.com/vpnclient-linux-2.6.24-final.diff

    wget lamnk.com/cisco_skbuff_offset.patch

    patch < ./vpnclient-linux-2.6.24-final.diff

    patch < ./cisco_skbuff_offset.patch

```

* Installation went fine from there.

---

### Post by cesar_spain on 2008-09-04
I wrote a script for VPN Client installation in Ubuntu 8.04. It worked for me, hope it helps.

[http://ubuntuforums.org/showthread.php?p=5725544&posted=1#post5725544](http://ubuntuforums.org/showthread.php?p=5725544&posted=1#post5725544)

[PHP]
#!/bin/bash
#####################################
# INSTALL_VPN.SH
#####################################
#  Script for installing the Cisco
# VPN Client in Ubuntu 8.04 - 64 bits
#
#   It can be easily adapted for 
# other distros and architectures
#####################################
# Author : Cesar Delgado Gonzalez
# Version: 1.0
# Date   : 10-March-2007
#####################################

##################################
# ENVIRONMENT
#################################

# 0.- General Variables
#----------------------
ERROR=1
OK=0
TRIES=1 # Attempts per Mirror

# 1.- Where to download
#----------------------
WORK_DIR=$HOME

# Syntax: Program - Mirror 1 - Mirror 2 ... Mirror N

# 64 bits Arch
PROGRAM=(vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz                 
         http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/  \
         http://www.longren.org/files/                                \
         )

# 32 bits Arch (not required, x86_64 source code works properly in i386 machines)
#PROGRAM=(vpnclient-linux-4.8.00.0490-k9.tar.gz                 \
#         http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.00/  \
#         http://www.longren.org/files/                                \
#         )


PATCH=(vpnclient-linux-2.6.24-final.diff              
       http://projects.tuxx-home.at/ciscovpn/patches/ \
       )

PATCH_2=(cisco_skbuff_offset.patch                     
         http://tuxx-home.at/projects/cisco-vpnclient/ \
        )

# 3.- Current Kernel Version
#---------------------------
KERNEL=`uname -r`
TYPE_KERNEL=`uname -r | awk 'BEGIN {FS="-";}{print $3}'`


################################################################################
# MODULE MISCELLANEOUS ====> GENERAL FUNCTIONS 
################################################################################

#-----------------------------------------------------------------------
# AYUDA 
#-----------------------------------------------------------------------
#  Muestra la ayuda por pantalla
#-----------------------------------------------------------------------

ayuda()
{
   echo "installVPN.sh --> Install Cisco VPN Client in Ubuntu 8.04"
   echo "  Best way to use it is through KVPNC, since it integrates it" 
}


#-----------------------------------------------------------------------
# TRATA_ERRORES
#-----------------------------------------------------------------------
#   Trata todos los posibles errores del script.
#
#    Se considerar salida err ea a toda salida del script sin la creaci 
#  de una estructura de datos (por ejm.: opcion -h provoca salida errea).
#
#     Variables de entrada:
#         $1 = Tipo de Error
#         $2 = Ruta a la que el usuario no tiene acceso (inexistencia o permisos)
#         $3 = Directorio de Trabajo
#-----------------------------------------------------------------------
trataErrores()
{

  ERROR="1"

  case $1 in
     -ayuda) # Solicitud de ayuda
            ayuda
        exit $ERROR;;

     -tryMirror) 
        echo "===========> Trying PACKAGE: $3 "
        echo "               from MIRROR : $2 "
        echo;;

     -downloadSucceed) 
        echo
        echo "*********************************************************************************"
        echo " Download succeed FOR  $3 "
        echo "                  FROM $2 "        
        echo "*********************************************************************************"
        echo ""  ;;

     -downloadFailed) 
        echo 
        echo "*********************************************************************************"
        echo "ERROR: PACKAGE $3 not found in" 
        echo "       MIRROR  $2"
        echo "*********************************************************************************"
        echo "" ;;

     -noMirrors) # There is no mirrors for this package
         echo 
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 has no mirror list"
         echo "*********************************************************************************"
         exit $ERROR;;


     -packageNotFound) # Package not found on any mirror
         echo
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 not found on any mirror of the list"
         echo "*********************************************************************************"
         exit $ERROR;;

     -requiredPack) # Failed installing required packages
         echo "ERROR ==> Can't install required packages: Linux source + Build Essentials"
         exit $ERROR;;
      
     -decompress) 
           echo " ERROR ==> File / Directory Not Available => Unpack Failed, cleaning and exiting"
           cleanEnvironment
           exit $ERROR ;;

  esac
}

################################################################################
# MODULE DOWNLOAD ====> FUNCTIONS FOR DOWNLOADING THE PACKAGES 
################################################################################

#-----------------------------------------------------------------------
#  DOWNLOAD PACKAGE 
#-----------------------------------------------------------------------
#   Try to download one package
#  from several mirrors. If all of them
#  fails, return 1
#
#   $1 = Number of tries per mirror
#   $2 = Package to download 
#   $3 ...  $N = List of mirrors
#-----------------------------------------------------------------------
downloadPackage () { 


   # 1.- Check that exist at least one Mirror on the input List
   #-----------------------------------------------------------
   if [ $# = 2 ]; then 
      trataErrores -noMirrors $2


   # 2.- Search for a the package on the mirrors list
   #-----------------------------------------------------------
   else

       POSITION=1
       for MIRROR in $@; do

          # 2.1.- Capture tries per mirror
          if [ $POSITION = 1 ]; then
               TRIES=$MIRROR

          # 2.2.- Capture package name
          elif [ $POSITION = 2 ]; then
               PACKAGE=$MIRROR

          # 2.3.- Try to get the package from current mirror
          else

                # Try the download
                trataErrores -tryMirror $MIRROR $PACKAGE
                `wget --tries=$TRIES $MIRROR$PACKAGE` 

                # Check if succeed
              if [ $? = $OK ]; then
                   trataErrores -downloadSucceed $MIRROR$PACKAGE $PACKAGE
                   break;
                     
              fi

               # Report the fail
               trataErrores -downloadFailed $MIRROR$PACKAGE $PACKAGE

          fi

          # 2.4.- Incrementing position
          POSITION=`expr $POSITION + 1`

       done 
   fi

   # 4.- Package not found of the list of mirrors
   #-----------------------------------------------------------
   if [ $POSITION = $# ] && [ $? != $OK ]; then
    trataErrores -packageNotFound $PACKAGE
   fi
}

#-----------------------------------------------------------------------
#  GET PACKAGES 
#-----------------------------------------------------------------------
#   Downloading the packages
# from the current mirror
#-----------------------------------------------------------------------
getPackages() {

        echo  "================================================================================"
        echo  "                    DOWNLOADING CISCO VPN CLIENT "         
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PROGRAM[*]}
         
        echo  "================================================================================"
        echo  "      DOWNLOADING UBUNTU PATCHES FOR KERNEL  = ${KERNEL} "
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PATCH[*]}
        downloadPackage $TRIES ${PATCH_2[*]}
 }

#-----------------------------------------------------------------------
#  INSTALL REQUIRED PACKAGES 
#-----------------------------------------------------------------------
#   Procedure that install required 
#-----------------------------------------------------------------------
installDependencies() {
 
     echo  "=============================================================================================="
     echo  " INSTALLING REQUIRED UBUNTU PACKAGES: linux kernel + build essentials + unpacking packages    "
     echo  "=============================================================================================="
     echo  " --> Command: "
     echo  " sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip zip unzip rar unrar "  
     sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip2 zip unzip rar unrar 
      
     # Error Treatment
     if [ ! "$?" -eq "$OK" ] ; then
        trataErrores -requiredPack
     fi 
}


################################################################################
# MODULE INSTALL ====> FUNCTIONS FOR COMPILING AND INSTALLING PROGRAM 
################################################################################

#-----------------------------------------------------------------------
#  UNPACK PACKAGES 
#-----------------------------------------------------------------------
#   Uncompress packages. Check file extension and uncompress
#  properly
#-----------------------------------------------------------------------
unpackPackages() {


   #----------------------
   # ENVIRONMENT
   #----------------------
   local OUT=$OK

   #----------------------
   # ACTIONS
   #----------------------
 
   # 0.- Tracing
   #---------------------
   echo  "================================================================================"
   echo  "             UNPACK PACKAGE: $1  "
   echo  "================================================================================"
   echo
 
   # 1.- Deflating File
   #------------------------------------------------------------
   echo "................................. FILE DECOMPRESSION .............................. "
   echo "File Extension: \${1##*.}=${1##*.}"
   local EXTENSION=${1##*.}
   echo "File Name: \${1%.*}=${1%.*}"
   FILENAME=${1%.*}

   case "$EXTENSION" in
     gz)  echo " ===> Decompress gz: gunzip -d $1"
          gunzip -d "$1" ; OUT="$?" ;;
     bz)  echo " ===> Decompress bz: bzip2 -d $1"
          bzip2 -d "$1"   ; OUT="$?" ;;
     zip) echo " ===> Decompress .zip: unzip $1" 
          unzip "$1"     ; OUT="$?" ;;
     rar) echo " ===> Decompress .rar: unrar $1"
          unrar "$1"     ; OUT="$?" ;;
     *) FILENAME="$1" ;;
   esac

   # 2.- Unpacking File
   #------------------------------------------------------------
   if [ "$OUT" -eq "$OK" ]; then
        TAR=${FILENAME##*.}

        if [ -n $TAR ] ; then # ================> There is an extension to check 

            if [ "$TAR" == "tar" ] ; then  # ====> Extension = .tar
                 echo ".............................. UNPACK TAR FILE .............................. "
                 
                 # 2.1.- Tar Base Detection
                 echo " ---> TAR base path detection: tar -tf ""$FILENAME"" | awk 'BEGIN {FS=""/""} {print $1}' | uniq"
                 TAR_BASE=`tar -tf "$FILENAME" | awk 'BEGIN {FS="/"} {print $1}' | uniq` 
                 echo " TAR Base = $TAR_BASE"

                 # 2.2.- Unpacking Tar File
                 echo " --> Unpack .tar: tar-xvf $FILENAME"
                 tar xvf "$FILENAME"

                 # 2.3.- Returning Output path to File
                 local RUTA=`dirname $FILENAME`
                 FILENAME="${RUTA}/${TAR_BASE}"
                 OUT="$?"
            fi 
        fi
   else
         trataErrores -decompress
   fi


   # 3.- Error Treatment
   #------------------------------------------------------------
   echo "................................... RESULTING FILE  ................................... "
   echo " Filename = $FILENAME "
   if [ -e $FILENAME ] && [ "$?" -eq "$OK" ] ; then 
        echo " File / Directory Available     => Unpack OK"
   else
        trataErrores -decompress
   fi

}

#-----------------------------------------------------------------------
#  APPLY PATCHES 
#-----------------------------------------------------------------------
#   Apply all Ubuntu specific patches 
#-----------------------------------------------------------------------
applyPatches() {
     

   #----------------------
   # ACTIONS
   #----------------------
   
     echo  "================================================================================"
     echo  " APPLY PATCHES AND ADJUSTMENTS  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"


     # 1.- Adjusting MakeFile 
     #---------------------
     echo " ......................... ADJUSTING MAKEFILE .............................. "
     echo " ========> > Replace CFLAGS to EXTRA_CFLAGS"
     echo "sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'              "${PROGRAM[0]}/Makefile"
     echo "sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  "${PROGRAM[0]}/Makefile" 
     
     echo 
     echo "  Resulting MakeFile"
     cat ${PROGRAM[0]}/Makefile

     # 2.- Applying Patches 
     #---------------------
     echo " ......................... APPLYING PATCHES .............................. "

     echo "......... sudo patch < ""${PATCH[0]}"""
     sudo patch < "${PATCH[0]}"

     echo "......... sudo patch < ""${PATCH_2[0]}"""
     sudo patch < "${PATCH_2[0]}"
}

#-----------------------------------------------------------------------
#  COMPILE PROGRAM 
#-----------------------------------------------------------------------
#   Compile and install program 
#-----------------------------------------------------------------------
compileProgram() {
     echo  "================================================================================"
     echo  " COMPILE AND INSTALL PROGRAM  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"
    
     echo " =======> Installing VPN Client"
     echo "......... sudo ""${PROGRAM[0]}/vpn_install"""
     sudo "${PROGRAM[0]}/vpn_install"

     if [ "$?" -eq "$OK" ] ; then
         echo " =======> Starting Cisco VPN Client"
         echo "......... sudo /etc/init.d/vpnclient_init start"
         sudo /etc/init.d/vpnclient_init start
     else
         trataErrores -installProgram
     fi
}

#-----------------------------------------------------------------------
#  CLEAN ENVIRONMENT 
#-----------------------------------------------------------------------
#   Remove everything used 
#-----------------------------------------------------------------------
cleanEnvironment() {

    echo  "================================================================================"
    echo  " CLEAN ENVIRONMENT  "
    echo  "================================================================================"

    echo "......... rm -R ${PROGRAM[0]}*"
    rm -fR ${PROGRAM[0]}*

    echo "......... rm ${PATCH[0]}*"
    rm -f ${PATCH[0]}*

    echo "......... rm ${PATCH_2[0]}*"
    rm -f ${PATCH_2[0]}*
}


#-----------------------------------------------------------------------
#  INSTALL PROGRAM 
#-----------------------------------------------------------------------
#   "Public" procedure of module 
#-----------------------------------------------------------------------
installProgram() {

     # 1.- Unpack files 
     #-------------------
     unpackPackages "${WORK_DIR}/${PROGRAM[0]}"
     PROGRAM[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH[0]}"
     PATCH[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH_2[0]}"
     PATCH_2[0]="$FILENAME"

     # 2- Apply Ubuntu Specific modifications
     #-------------------
     applyPatches

     # 3.- Compile Program
     #-------------------
     compileProgram 

     # 4.- Clean Environment
     #-------------------
     cleanEnvironment 
}

################################################################################
# MAIN
################################################################################
cd $WORK_DIR
installDependencies
getPackages
installProgram
exit "$OK"
#------------------------------------------------------------------------------
#                             END INSTALL VPN 
#------------------------------------------------------------------------------ 
[/PHP]

---

### Post by jlinoff on 2008-09-22
This is an excellent post but I also had trouble getting to work on a 64b machine because of compile problems. Here is what I did to get it working (steps 1-7 are the same as before). 

1. Delete your current vpn installation files.

2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz](http://projects.tuxx-home.at/ciscovp...0640-k9.tar.gz)

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovp....24-final.diff](http://projects.tuxx-home.at/ciscovp....24-final.diff)

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <../vpnclient-linux-2.6.24-final.diff

8. Download diff file for 64b kernels to "../" from:
[http://tuxx-home.at/projects/cisco-vpnclient/cisco_skbuff_offset.patch](http://tuxx-home.at/projects/cisco-vpnclient/cisco_skbuff_offset.patch)
(citation: [http://ciscovpnclient.blogspot.com/2008/03/cisco-vpn-client.html)\](http://ciscovpnclient.blogspot.com/2008/03/cisco-vpn-client.html)\)

9. Type: patch <../cisco_skbuff_offset.patch

10. Edit the Makefile and change CFLAGS to EXTRA_CFLAGS at line 15.

11. Now install successfully as you regularly would!
    Type: sudo ./vpnclient_install
    Type: sudo ./vpnclient_init start
    Type: sudo ./vpnclient connect <foo>

Also, many thanks to tuxx home.

---

### Post by ee19921 on 2008-10-08
> **jonathan.david.lim said:**
> Hmm, nevermind. I rebooted and it almost connects, but now it gives the following:

```
Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Unable to resolve server address.
```

What's going on?

Me too stuck at the same error. In my school FAQs, has the following instructions. I have no idea how to do it.

```

If you are using ipchains or ipfilter (which is default on Redhat 7.2 and above installations) 
or another type of firewall on the linux platform,  you will need to open 
it up for the vpn connection. If you are using transparent tunneling,
which is the default for the UF client, you will need to open the 
following ports to and from XXX.XXX.XXX.116-118

TCP port 32611 
UDP port 32611 
UDP port 4500 
UDP port 500 

If you have disabled transparent tunneling, you will need to allow the 
following to XXX.XXX.XXX.116-118 
IP protocol 50 (ESP) 
UDP port 500 

Please see the ipchains/ipfilter documentation for your distribution on the correct way of making these changes. 
Alternatively, you may also allow all communication between your system 
and XXX.XXX.XXX.116-118.
```

---

### Post by ee19921 on 2008-10-14
> **ee19921 said:**
> Me too stuck at the same error. In my school FAQs, has the following instructions. I have no idea how to do it.



I had to import the root certificate for it to work. Thought [this]("http://ubuntuforums.org/showthread.php?t=807622") might be helpful for other n00bs.

---

### Post by eatingganesh on 2008-10-15
I have followed these directions exactly and all looks good until I try to install. Then I get bash:command not found. Here is the directory:

kharyssa@kharyssa-desktop:~/Desktop/vpnclient$ ls
cisco_cert_mgr   IPSecDrvOSFunctions.h  linuxcniapi.c     vpnapi.h
Cniapi.h         IPSecDrvOS_linux.c     linuxcniapi.h     vpnclient
config.h         IPSecDrvOS_linux.h     linuxkernelapi.c  vpnclient.ini
cvpnd            ipseclog               linux_os.h        vpnclient_init
driver_build.sh  libdriver64.so         Makefile          vpn_install
frag.c           libdriver.so           mtu.h             vpn_ioctl_linux.h
frag.h           libvpnapi.so           sample.pcf        vpn_uninstall
GenDefs.h        license.rtf            unixcniapi.h
interceptor.c    license.txt            unixkernelapi.h
kharyssa@kharyssa-desktop:~/Desktop/vpnclient$ vpn_install
bash: vpn_install: command not found


What am I doing wrong? After 4 hours of trying multiple things, downloads, etc. I'm about ready to chuck my system out the window.

Thanks in advance!

EG


> **ndeburn said:**
> The Fiesty Link above does not work for me with 8.04.  I did however find a fix for 8.04,  Here are the instructions,

1. Delete your current vpn installation files.

2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz]("http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff")

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!

P.S. Thanks Tuxx-Home.

---

### Post by eatingganesh on 2008-10-15
Hi ee19921! I just switched to Hardy and am at UF too - trying to get the darn VPN to work. How did you finally manage to make it work for you? I've been stuck for days. I'd be very grateful if you could take the time to share your fix. :)


> **ee19921 said:**
> Me too stuck at the same error. In my school FAQs, has the following instructions. I have no idea how to do it.

```

If you are using ipchains or ipfilter (which is default on Redhat 7.2 and above installations) 
or another type of firewall on the linux platform,  you will need to open 
it up for the vpn connection. If you are using transparent tunneling,
which is the default for the UF client, you will need to open the 
following ports to and from XXX.XXX.XXX.116-118

TCP port 32611 
UDP port 32611 
UDP port 4500 
UDP port 500 

If you have disabled transparent tunneling, you will need to allow the 
following to XXX.XXX.XXX.116-118 
IP protocol 50 (ESP) 
UDP port 500 

Please see the ipchains/ipfilter documentation for your distribution on the correct way of making these changes. 
Alternatively, you may also allow all communication between your system 
and XXX.XXX.XXX.116-118.
```

---

### Post by geezerone on 2008-10-15
> **cesar_spain said:**
> I wrote a script for VPN Client installation in Ubuntu 8.04. It worked for me, hope it helps.

[http://ubuntuforums.org/showthread.php?p=5725544&posted=1#post5725544](http://ubuntuforums.org/showthread.php?p=5725544&posted=1#post5725544)

[php]
#!/bin/bash
#####################################
# INSTALL_VPN.SH
#####################################
#  Script for installing the Cisco
# VPN Client in Ubuntu 8.04 - 64 bits
#
#   It can be easily adapted for 
# other distros and architectures
#####################################
# Author : Cesar Delgado Gonzalez
# Version: 1.0
# Date   : 10-March-2007
#####################################

##################################
# ENVIRONMENT
#################################

# 0.- General Variables
#----------------------
ERROR=1
OK=0
TRIES=1 # Attempts per Mirror

# 1.- Where to download
#----------------------
WORK_DIR=$HOME

# Syntax: Program - Mirror 1 - Mirror 2 ... Mirror N

# 64 bits Arch
PROGRAM=(vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz                 
         http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/  \
         http://www.longren.org/files/                                \
         )

# 32 bits Arch (not required, x86_64 source code works properly in i386 machines)
#PROGRAM=(vpnclient-linux-4.8.00.0490-k9.tar.gz                 \
#         http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.00/  \
#         http://www.longren.org/files/                                \
#         )


PATCH=(vpnclient-linux-2.6.24-final.diff              
       http://projects.tuxx-home.at/ciscovpn/patches/ \
       )

PATCH_2=(cisco_skbuff_offset.patch                     
         http://tuxx-home.at/projects/cisco-vpnclient/ \
        )

# 3.- Current Kernel Version
#---------------------------
KERNEL=`uname -r`
TYPE_KERNEL=`uname -r | awk 'BEGIN {FS="-";}{print $3}'`


################################################################################
# MODULE MISCELLANEOUS ====> GENERAL FUNCTIONS 
################################################################################

#-----------------------------------------------------------------------
# AYUDA 
#-----------------------------------------------------------------------
#  Muestra la ayuda por pantalla
#-----------------------------------------------------------------------

ayuda()
{
   echo "installVPN.sh --> Install Cisco VPN Client in Ubuntu 8.04"
   echo "  Best way to use it is through KVPNC, since it integrates it" 
}


#-----------------------------------------------------------------------
# TRATA_ERRORES
#-----------------------------------------------------------------------
#   Trata todos los posibles errores del script.
#
#    Se considerar salida err ea a toda salida del script sin la creaci 
#  de una estructura de datos (por ejm.: opcion -h provoca salida errea).
#
#     Variables de entrada:
#         $1 = Tipo de Error
#         $2 = Ruta a la que el usuario no tiene acceso (inexistencia o permisos)
#         $3 = Directorio de Trabajo
#-----------------------------------------------------------------------
trataErrores()
{

  ERROR="1"

  case $1 in
     -ayuda) # Solicitud de ayuda
            ayuda
        exit $ERROR;;

     -tryMirror) 
        echo "===========> Trying PACKAGE: $3 "
        echo "               from MIRROR : $2 "
        echo;;

     -downloadSucceed) 
        echo
        echo "*********************************************************************************"
        echo " Download succeed FOR  $3 "
        echo "                  FROM $2 "        
        echo "*********************************************************************************"
        echo ""  ;;

     -downloadFailed) 
        echo 
        echo "*********************************************************************************"
        echo "ERROR: PACKAGE $3 not found in" 
        echo "       MIRROR  $2"
        echo "*********************************************************************************"
        echo "" ;;

     -noMirrors) # There is no mirrors for this package
         echo 
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 has no mirror list"
         echo "*********************************************************************************"
         exit $ERROR;;


     -packageNotFound) # Package not found on any mirror
         echo
         echo "*********************************************************************************"
         echo "ERROR ==> Package $2 not found on any mirror of the list"
         echo "*********************************************************************************"
         exit $ERROR;;

     -requiredPack) # Failed installing required packages
         echo "ERROR ==> Can't install required packages: Linux source + Build Essentials"
         exit $ERROR;;
      
     -decompress) 
           echo " ERROR ==> File / Directory Not Available => Unpack Failed, cleaning and exiting"
           cleanEnvironment
           exit $ERROR ;;

  esac
}

################################################################################
# MODULE DOWNLOAD ====> FUNCTIONS FOR DOWNLOADING THE PACKAGES 
################################################################################

#-----------------------------------------------------------------------
#  DOWNLOAD PACKAGE 
#-----------------------------------------------------------------------
#   Try to download one package
#  from several mirrors. If all of them
#  fails, return 1
#
#   $1 = Number of tries per mirror
#   $2 = Package to download 
#   $3 ...  $N = List of mirrors
#-----------------------------------------------------------------------
downloadPackage () { 


   # 1.- Check that exist at least one Mirror on the input List
   #-----------------------------------------------------------
   if [ $# = 2 ]; then 
      trataErrores -noMirrors $2


   # 2.- Search for a the package on the mirrors list
   #-----------------------------------------------------------
   else

       POSITION=1
       for MIRROR in $@; do

          # 2.1.- Capture tries per mirror
          if [ $POSITION = 1 ]; then
               TRIES=$MIRROR

          # 2.2.- Capture package name
          elif [ $POSITION = 2 ]; then
               PACKAGE=$MIRROR

          # 2.3.- Try to get the package from current mirror
          else

                # Try the download
                trataErrores -tryMirror $MIRROR $PACKAGE
                `wget --tries=$TRIES $MIRROR$PACKAGE` 

                # Check if succeed
              if [ $? = $OK ]; then
                   trataErrores -downloadSucceed $MIRROR$PACKAGE $PACKAGE
                   break;
                     
              fi

               # Report the fail
               trataErrores -downloadFailed $MIRROR$PACKAGE $PACKAGE

          fi

          # 2.4.- Incrementing position
          POSITION=`expr $POSITION + 1`

       done 
   fi

   # 4.- Package not found of the list of mirrors
   #-----------------------------------------------------------
   if [ $POSITION = $# ] && [ $? != $OK ]; then
    trataErrores -packageNotFound $PACKAGE
   fi
}

#-----------------------------------------------------------------------
#  GET PACKAGES 
#-----------------------------------------------------------------------
#   Downloading the packages
# from the current mirror
#-----------------------------------------------------------------------
getPackages() {

        echo  "================================================================================"
        echo  "                    DOWNLOADING CISCO VPN CLIENT "         
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PROGRAM
[*]}
         
        echo  "================================================================================"
        echo  "      DOWNLOADING UBUNTU PATCHES FOR KERNEL  = ${KERNEL} "
        echo  "================================================================================"
        echo
        downloadPackage $TRIES ${PATCH
[*]}
        downloadPackage $TRIES ${PATCH_2
[*]}
 }

#-----------------------------------------------------------------------
#  INSTALL REQUIRED PACKAGES 
#-----------------------------------------------------------------------
#   Procedure that install required 
#-----------------------------------------------------------------------
installDependencies() {
 
     echo  "=============================================================================================="
     echo  " INSTALLING REQUIRED UBUNTU PACKAGES: linux kernel + build essentials + unpacking packages    "
     echo  "=============================================================================================="
     echo  " --> Command: "
     echo  " sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip zip unzip rar unrar "  
     sudo apt-get install  linux-${TYPE_KERNEL} linux-headers-${KERNEL} build-essential gcc gzip bzip2 zip unzip rar unrar 
      
     # Error Treatment
     if [ ! "$?" -eq "$OK" ] ; then
        trataErrores -requiredPack
     fi 
}


################################################################################
# MODULE INSTALL ====> FUNCTIONS FOR COMPILING AND INSTALLING PROGRAM 
################################################################################

#-----------------------------------------------------------------------
#  UNPACK PACKAGES 
#-----------------------------------------------------------------------
#   Uncompress packages. Check file extension and uncompress
#  properly
#-----------------------------------------------------------------------
unpackPackages() {


   #----------------------
   # ENVIRONMENT
   #----------------------
   local OUT=$OK

   #----------------------
   # ACTIONS
   #----------------------
 
   # 0.- Tracing
   #---------------------
   echo  "================================================================================"
   echo  "             UNPACK PACKAGE: $1  "
   echo  "================================================================================"
   echo
 
   # 1.- Deflating File
   #------------------------------------------------------------
   echo "................................. FILE DECOMPRESSION .............................. "
   echo "File Extension: \${1##*.}=${1##*.}"
   local EXTENSION=${1##*.}
   echo "File Name: \${1%.*}=${1%.*}"
   FILENAME=${1%.*}

   case "$EXTENSION" in
     gz)  echo " ===> Decompress gz: gunzip -d $1"
          gunzip -d "$1" ; OUT="$?" ;;
     bz)  echo " ===> Decompress bz: bzip2 -d $1"
          bzip2 -d "$1"   ; OUT="$?" ;;
     zip) echo " ===> Decompress .zip: unzip $1" 
          unzip "$1"     ; OUT="$?" ;;
     rar) echo " ===> Decompress .rar: unrar $1"
          unrar "$1"     ; OUT="$?" ;;
     *) FILENAME="$1" ;;
   esac

   # 2.- Unpacking File
   #------------------------------------------------------------
   if [ "$OUT" -eq "$OK" ]; then
        TAR=${FILENAME##*.}

        if [ -n $TAR ] ; then # ================> There is an extension to check 

            if [ "$TAR" == "tar" ] ; then  # ====> Extension = .tar
                 echo ".............................. UNPACK TAR FILE .............................. "
                 
                 # 2.1.- Tar Base Detection
                 echo " ---> TAR base path detection: tar -tf ""$FILENAME"" | awk 'BEGIN {FS=""/""} {print $1}' | uniq"
                 TAR_BASE=`tar -tf "$FILENAME" | awk 'BEGIN {FS="/"} {print $1}' | uniq` 
                 echo " TAR Base = $TAR_BASE"

                 # 2.2.- Unpacking Tar File
                 echo " --> Unpack .tar: tar-xvf $FILENAME"
                 tar xvf "$FILENAME"

                 # 2.3.- Returning Output path to File
                 local RUTA=`dirname $FILENAME`
                 FILENAME="${RUTA}/${TAR_BASE}"
                 OUT="$?"
            fi 
        fi
   else
         trataErrores -decompress
   fi


   # 3.- Error Treatment
   #------------------------------------------------------------
   echo "................................... RESULTING FILE  ................................... "
   echo " Filename = $FILENAME "
   if [ -e $FILENAME ] && [ "$?" -eq "$OK" ] ; then 
        echo " File / Directory Available     => Unpack OK"
   else
        trataErrores -decompress
   fi

}

#-----------------------------------------------------------------------
#  APPLY PATCHES 
#-----------------------------------------------------------------------
#   Apply all Ubuntu specific patches 
#-----------------------------------------------------------------------
applyPatches() {
     

   #----------------------
   # ACTIONS
   #----------------------
   
     echo  "================================================================================"
     echo  " APPLY PATCHES AND ADJUSTMENTS  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"


     # 1.- Adjusting MakeFile 
     #---------------------
     echo " ......................... ADJUSTING MAKEFILE .............................. "
     echo " ========> > Replace CFLAGS to EXTRA_CFLAGS"
     echo "sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/CFLAGS/EXTRA_CFLAGS/g'              "${PROGRAM[0]}/Makefile"
     echo "sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  ""${PROGRAM[0]}/Makefile"""
     sudo sed -i 's/EXTRA_EXTRA_CFLAGS/EXTRA_CFLAGS/g'  "${PROGRAM[0]}/Makefile" 
     
     echo 
     echo "  Resulting MakeFile"
     cat ${PROGRAM[0]}/Makefile

     # 2.- Applying Patches 
     #---------------------
     echo " ......................... APPLYING PATCHES .............................. "

     echo "......... sudo patch < ""${PATCH[0]}"""
     sudo patch < "${PATCH[0]}"

     echo "......... sudo patch < ""${PATCH_2[0]}"""
     sudo patch < "${PATCH_2[0]}"
}

#-----------------------------------------------------------------------
#  COMPILE PROGRAM 
#-----------------------------------------------------------------------
#   Compile and install program 
#-----------------------------------------------------------------------
compileProgram() {
     echo  "================================================================================"
     echo  " COMPILE AND INSTALL PROGRAM  "
     echo  "================================================================================"
     echo "cd ""${PROGRAM[0]}"""
     cd "${PROGRAM[0]}"
    
     echo " =======> Installing VPN Client"
     echo "......... sudo ""${PROGRAM[0]}/vpn_install"""
     sudo "${PROGRAM[0]}/vpn_install"

     if [ "$?" -eq "$OK" ] ; then
         echo " =======> Starting Cisco VPN Client"
         echo "......... sudo /etc/init.d/vpnclient_init start"
         sudo /etc/init.d/vpnclient_init start
     else
         trataErrores -installProgram
     fi
}

#-----------------------------------------------------------------------
#  CLEAN ENVIRONMENT 
#-----------------------------------------------------------------------
#   Remove everything used 
#-----------------------------------------------------------------------
cleanEnvironment() {

    echo  "================================================================================"
    echo  " CLEAN ENVIRONMENT  "
    echo  "================================================================================"

    echo "......... rm -R ${PROGRAM[0]}*"
    rm -fR ${PROGRAM[0]}*

    echo "......... rm ${PATCH[0]}*"
    rm -f ${PATCH[0]}*

    echo "......... rm ${PATCH_2[0]}*"
    rm -f ${PATCH_2[0]}*
}


#-----------------------------------------------------------------------
#  INSTALL PROGRAM 
#-----------------------------------------------------------------------
#   "Public" procedure of module 
#-----------------------------------------------------------------------
installProgram() {

     # 1.- Unpack files 
     #-------------------
     unpackPackages "${WORK_DIR}/${PROGRAM[0]}"
     PROGRAM[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH[0]}"
     PATCH[0]="$FILENAME"
     unpackPackages "${WORK_DIR}/${PATCH_2[0]}"
     PATCH_2[0]="$FILENAME"

     # 2- Apply Ubuntu Specific modifications
     #-------------------
     applyPatches

     # 3.- Compile Program
     #-------------------
     compileProgram 

     # 4.- Clean Environment
     #-------------------
     cleanEnvironment 
}

################################################################################
# MAIN
################################################################################
cd $WORK_DIR
installDependencies
getPackages
installProgram
exit "$OK"
#------------------------------------------------------------------------------
#                             END INSTALL VPN 
#------------------------------------------------------------------------------ 
[/php]

Have you tried this script?

---

### Post by ee19921 on 2008-10-16
> **eatingganesh said:**
> 
kharyssa@kharyssa-desktop:~/Desktop/vpnclient$ vpn_install
bash: vpn_install: command not found



If you have done other steps, while installing try ```
./vpn_install
```

---

### Post by eatingganesh on 2008-10-16
wow! that worked! awesome!

---

### Post by tlowery on 2008-10-17
Well, I had this working fine according to the directions in this thread.  It's been working for several months until today when I installed the latest kernel and header updates from Ubuntu (2.6.24-21.27).  Tonight when I ran

    vpnclient_init start

I got a message that the kernel version specific modules directory didn't exist.  I tried uninstalling the vpn package (vpn_uninstall), rebuilding the client, and reinstalling it (vpn_install).

I no longer get the message about the missing module directory when I run

    vpnclient_init start

but I can't connect to my vpn server any more.  When I run

    vpnclient connect <myprofilename>

I get a message about failure to resolve host.  I can ping the hostname, so I tried modifying the profile using the resulting IP address as the host.  In that case when I try to connect I don't get the "failure to resolve" message, but the connect is closed by the local client.

Has anyone else had this problem?  Any suggestions on how to resolve it?

Thanks in advance!

---

### Post by ee19921 on 2008-10-17
I had the problem after installing 2.6.24-21, uninstalling(I didn't remove the profiles and certificates) and reinstalling it worked for me.

while uninstalling did you remove the profiles and certificates? are you getting this message? 


```

Secure VPN Connection terminated locally by the Client
Reason: Failed to establish a VPN connection.
There are no new notification messages at this time.

```

---

### Post by geezerone on 2008-10-26
Since upgrading I am also not able to get VPN to connect. I uninstalled (sudo ./vpn_uninstall) and left profiles and certs and can connect but cannot ping any resources. The problem is that when I reboot I get the following error when trying to connect:

```
sudo vpnclient connect vpnsite
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system
```If I issue the command:

```
sudo /etc/init.d/vpnclient_init start

``` I can connect but that is all.

Any ideas appreciated as many are having this problem since kernel upgrade looking at other threads.

---

### Post by ee19921 on 2008-10-26
> **geezerone said:**
> Since upgrading I am also not able to get VPN to connect. I uninstalled (sudo ./vpn_uninstall) and left profiles and certs and can connect but cannot ping any resources. The problem is that when I reboot I get the following error when trying to connect:

```
sudo vpnclient connect beltel
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system
```

If I issue the command:

```
sudo /etc/init.d/vpnclient_init start

``` I can connect but that is all.

Any ideas appreciated as many are having this problem since kernel upgrade looking at other threads.

After vpnclient_init, when you connect using vpnclient, do you see any unusual message apart from server/client IP addresses?

What do you see when you run this command
```
vpnclient stat
```

---

### Post by geezerone on 2008-10-26
Hi

I see VPN tunnel info, VPN traffic summary, configured routes.

I used the script above to re-install the client for what it's worth. Wonder if I should remove certs but as I connect can't see how this would make any difference?

---

### Post by ee19921 on 2008-10-26
> **geezerone said:**
> Hi

I see VPN tunnel info, VPN traffic summary, configured routes.

I used the script above to re-install the client for what it's worth. Wonder if I should removed certs but as I connect can't see how this would make any difference?

thats weird! You are connected but unable to connect to any resource. 

Me too, don't see any reason to redo cert import. I don't know if the script has any problem. But manual installation seems to work for at least 2 in the thread. 

I have I will leave it to the experts to solve. Sorry I am not of much help to you.

---

### Post by geezerone on 2008-10-26
Thanks for the replies. I have tried this on two different pcs and have the same problem - even using the old '..19' kernel.

If there is a way to access resources please tell anyone?

TIA

---

### Post by The Crazy Parrot on 2008-10-30
thanks guys

---

### Post by Divan Santana on 2008-11-10
Hi All,

This howto seems to work for ubuntu 8.04 hardy with kernel 2.6.24 but what about ubuntu intrepid ibex 8.10 with kernel 2.6.27-7-generic as the patch is not designed for this version hence I can't install cisco vpn client as it fails out with the usual:

Failed to make module "cisco_ipsec.ko".                                                                                             

Anyone have any ideas or get this working on intrepid?

---

### Post by ee19921 on 2008-11-10
> **Divan Santana said:**
> Hi All,

This howto seems to work for ubuntu 8.04 hardy with kernel 2.6.24 but what about ubuntu intrepid ibex 8.10 with kernel 2.6.27-7-generic as the patch is not designed for this version hence I can't install cisco vpn client as it fails out with the usual:

Failed to make module "cisco_ipsec.ko".                                                                                             

Anyone have any ideas or get this working on intrepid?

oh, I didn't realise that the patch was not meant for this kernel version. But, I uninstalled vpn client and followed [this how to]("http://ubuntuforums.org/showthread.php?p=4805775#post4805775"). It worked!

---

### Post by Divan Santana on 2008-11-11
I followed this howto exactly and it still doesn't seem to work :(

Are you using intrepid? I'm running:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

Uninstalled and resinstalled but still same error message.
I also had to change the following URL for the patch from this:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff)
to this:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff)

As the first one didn't work, the second one did patch 2 files correctly though.

Any ideas?
I have got build-essentials installed.

---

### Post by ee19921 on 2008-11-11
> **Divan Santana said:**
> I followed this howto exactly and it still doesn't seem to work :(

Are you using intrepid? I'm running:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

Uninstalled and resinstalled but still same error message.
I also had to change the following URL for the patch from this:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff)
to this:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24.diff)

As the first one didn't work, the second one did patch 2 files correctly though.

Any ideas?
I have got build-essentials installed.

I am using Kubuntu 8.10 Intrepid Ibex.

Are you using the installation file in step 2 of how to or the one provided by your network guys? As I had the same problem with my school copy, I used the one in the how to.

---

### Post by Divan Santana on 2008-11-13
I came right eventually. Thanks! :)

---

### Post by truthseek on 2009-09-30
> **geezerone said:**
> Have you tried this script?

thx a lot! this worked like a charm for me ;)

edit: I'm on Ubuntu 9.04 Jaunty Jackalope, with amd64

Maurizio

---

### Post by westyfresh on 2011-04-12
> **ndeburn said:**
> The Fiesty Link above does not work for me with 8.04.  I did however find a fix for 8.04,  Here are the instructions,

1. Delete your current vpn installation files.

2. Download new 4.8.01 from:
[http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz]("http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz")

3. Download diff file for 2.6.24 kernels from:
[http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff")

4. Extract the .gz.

5. cd into the vpnclient directory.

6. Type: sudo apt-get install patch

7. Type: patch <../vpnclient-linux-2.6.24-final.diff
(You should get a message that it updated 2 or so files. Sorry I am doing this from memory)

8. Now install successfully as you regularly would!

P.S. Thanks Tuxx-Home.


I am also having trouble install Cisco VPN Client, 4.8.02.0030. Ubuntu 10.10 (64 bit), running 2.6.35-28. Does anyone know how to fix this issue?

Here is the output "sudo ./vpn_install"

```

Making module
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/usr/local/bin/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /usr/local/bin/vpnclient/linuxcniapi.o
/usr/local/bin/vpnclient/linuxcniapi.c:14: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/local/bin/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/usr/local/bin/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


```

Here is my ./vpn_install output

---

