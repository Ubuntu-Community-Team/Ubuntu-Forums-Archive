---
title: "Samsung Printer Drivers"
date: 2006-10-29
forum: General Help
---

### Post by Muntted on 2006-10-29
Hey, I was wondering if I could get help installing the samsung linux printer drivers.

I have downloaded the file, extracted it, followed the instructions that say to run the autorun file. I just end up with this
matt@plc:~/Desktop/cdroot$ ./autorun
./Linux/install.sh: 1230: source: not found
ERROR: HARDWARE_PLATFORM undefined, execution aborted

I read the autorun file which points to a file called install.ch but I get the same error. I also cannot configure or make this.

Any help?

---

### Post by Muntted on 2006-10-30
any help guys?

---

### Post by drpaul on 2006-10-30
Where did the files come from?

Paul

---

### Post by Sef on 2006-10-30
What Samsung model do you have?

---

### Post by Muntted on 2006-10-30
Model is the SCX-4100 I downloaded the unified driver from the website.

---

### Post by glitchiron on 2006-10-30
Hi, I am new to linux and this is my first post on this forum.

I have the same problem as Muntted.  Cannot install the Samsung unified driver 20060711102845140_UnifiedLinuxDriver.tar.gz

My printer is a ML-3051N.
It worked fine on Dapper.
On Edgy I get the same error 
that Muntted got.

Thanks

---

### Post by wastrel on 2006-10-30
Is this a dash vs. bash problem?  Try editing the driver installer file and change the top line from  ```
#!/bin/sh
```  to ```
#!/bin/bash
```   see if that fixes it.

---

### Post by Muntted on 2006-10-30
that doesnt work.
However if I change it from 

#!/bin/sh
to
#/bin/sh

it comes up with this...
> root@plc:~/Desktop/cdroot/Linux# ./install.sh 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

it then opens up the installer, where if you click next it comes up with the same hardware_platform undefined message

---

### Post by Xerix on 2006-10-31
I just purchased a SCX-4200 today and I have the same problem. If only I had saw this thread earlier.

---

### Post by Muntted on 2006-10-31
ok I manage to get the installer working but im still having problems.

What I did was take out all reference to the wacom devices in the xorg.conf file.

Reboot

Edit installer to #! /bin/bash as suggested

and it installed
so I rebooted but its still not installing the printer.
Its detecting it on the usb port but wont install one.

---

### Post by wastrel on 2006-10-31
I'm pretty sure this is a bash vs dash problem.  The "source" command is not understood by dash shell.

Changing the shebang path to point to /bin/bash should work...

---

### Post by Muntted on 2006-10-31
yeah it did, problem is the printer still doesnt show up

---

### Post by rusty0101 on 2006-10-31
I am not sure if this will help you, but it has worked for me with the Samsung CLP-510. There are instructions for installing the samsung drivers for that printer over on [Linuxprinting.org]("http://linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-510") that I was able to use to install the drivers for that printer. Basically ignore the 'install.sh' script, copy the correct libraries and ppd files to specified directories, and then use the printer configuration tool to select the correct printer driver.

Minor problems I had after that pretty much were all the applications are configured to use A4 as the default paper size, and need to be updated, or you will be given error messages every time you go to print.

Most of the isntructions do not include the fact that you have to copy most of the files sudo, rather than just copying them at the command line. Mostly the were written for Debian with a root login, rather than Ubuntu without one.

Hope this helps.

---

### Post by Muntted on 2006-10-31
Yeah! I got it working.

Ill write up a guide now.

---

### Post by Muntted on 2006-10-31
Guide can be found at [http://mattgordon.wordpress.com/howto/installing-a-samsung-printer/]("http://mattgordon.wordpress.com/howto/installing-a-samsung-printer/") as the quoted version doesnt show some bits up correctly

> 


This is a guide that should hopefully ease you through the stress of getting a Samsung printer working in Linux.
I made this guide with Ubuntu 6.10 and a Samsung SCX-4100 but most versions, distributions and models should be fairly similar.
I will also be updating the guide in the future hopefully if I manage to work out scanning as well.

Getting the driver:
To start off with you need to head to [www.samsung.com](www.samsung.com) and get the latest version of the driver. Look for the linux driver that ends in .tar.gz (at the time of writing 20060719092647968_UnifiedLinuxDriver.tar.gz was the file to look for). Save this file to your desktop and once it has finished extract it by right clicking on the file and selecting &#8220;extract here&#8221;.

Installing the driver via supplied instructions:
From here we install the drivers which should be as simple as moving to the correct directory and running the script:

    cd Desktop/cdroot/Linux
    sudo ./install.ch

If everything runs fine and dandy and the printer installs and you can use a test page, then wow your a lucky one. If your like the rest of us then it will not be so pain free. However with the release of the new unified Linux printer drivers for linux, it is only a quick task to get things going.

Editing the needed files:
The first thing we have to do it edit the install script, however it is currently read only file. This can be done by moving opening up the directory via the GUI: &#8216;Right click on install.ch > properties > permissions&#8217; then change owner access to &#8216;read and write&#8217;.
Now we have the permissions to edit the file. Which we can do by opening the file with gedit:

    sudo gedit install.ch
    we then change the top line from
    #! /bin/sh
    to
    #! /bin/bash

apparently this is just something that is different between some versions of Linux.
Installing drivers:
We now try to install the drivers again

    cd Desktop/cdroot/Linux
    sudo ./install.ch

It should now work and an installation screen should pop up. Move through the install and another window will pop up trying to get you to install the printer. Do this, but chances are when you click on the &#8216;print test page&#8217; button nothing will work. This just seems to be a minor problem, we will fix that up now.

Adding your printer:

Go into &#8217;system > administration > printing&#8217; and then click on &#8220;New printer&#8221;. It might show a few printers connected, select the one that is like &#8216;Samsung SCX-4100 series&#8217;. There should be a driver listed for your printers model now too. Finish the installer off and your printer should now be installed properly.

Confirming your printer is properly installed:

Right click on your printers new flashy icon and click &#8220;Properties&#8221;, choose &#8220;Print test page&#8221; and it should now reward you with a hot freshly printed test page.



give reports back on your results

---

### Post by rusty0101 on 2006-11-01
Not significant, but I think you only need to restart X after you edit the xorg.conf file. Save any open files, then [Ctrl]-[Alt]-[BkSpace] and x will shut down and restart with the new xorg.conf configuration and give you a login prompt.

-Rusty

---

### Post by Scunizi on 2006-11-09
I just installed the unified driver for my Samsung ML-2010 and the instructions there are the same as the 4200...

> 1. Make sure that you connect your machine to your computer.
Turn both the computer and the machine on.

2. When the Administrator Login window appears, type in root in the Login field
and enter the system password.

3. Download and extract the driver
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]

4. The driver will be extracted as 'cdroot' folder in current path.

5. Execute installation program.
[root@localhost root]#./cdroot/autorun


By doing this it installed the driver just fine with one exception... I still had to go to System/Admin/Printers and add the new printer choosing the new driver (listed now).  Everything worked like a champ!:D

---

### Post by samurai1200 on 2006-11-09
Wow, you's be lucky, AFAIC.
BTW, I thought the root su was disabled on ubuntu?
And you were in 6.06 or 6.10?

I'll have to try that soon as I'm done here in Winblows.
What I'm afraid of is not properly uninstalling what i have installed right now... a non-working driver setup.

---

### Post by Scunizi on 2006-11-10
What I did to get around the "root" issue was to just begin on line 3 and enter ... sudo tar xzf [Downloaded File Name(XXXX.tar.gz).  It will prompt for your password and decompress the file.  In order to do this I saved the downloaded file to the Desktop (or your preferrable location), opened a terminal and changed my directory to the desktop ie.  cd Desktop.  It's been 19 hours since you posted so if you haven't already figured it out hopefully this will do the trick for you.

---

### Post by 2beers on 2006-11-15
I. Download the unified driver from samsung HP (and untar it)
II.  Enable the web administration interface of CUPS (Common UNIX Printing System).

   1.  Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups
   2.  Select the group shadow and click Properties.
   3.  Add the user cupsys to the group.
   4.  Restart CUPS with this command:
      $sudo /etc/init.d/cupsys restart

III. Visit the web interface by entering [http://localhost:631/admin](http://localhost:631/admin) in your browser's location bar.
    1. Choose the printer u desire to use - press "add"
    2. It will most likley not offer the propper ppd file BUT - the needed file is hidden in the "unified driver" u untared in step I.
So - just browse manually for the propper *.ppd file wich is located in:
location_where_u_untared_unified_driver/cdroot/Linux/noarch/at_opt/share/ppd/
Find the appropiriate *.ppd (i.e. if your printer is a CLP 510 - use the CLP-510splc.ppd)

Check if all settings are correct (i.a. in my case the format was set to "letter" insted of "A4")

Hope that might help some of u guys.

Btw - the unified driver with auto-script worked fine for me using Xubuntu 6.06 - but not with Kubuntu 6.10.

---

### Post by confusimo on 2006-12-03
I have a 2510.  Samsung Tech support was very helpful.  The unified whatever from their website works flawlessly.  But on 6.06.  I tried 6.10 and it was too buggy so I went back to 6.0.6.

Thanks,
Confusimo

---

### Post by marcelloconti on 2007-03-28
I change de "#!/bin/sh" to "#!/bin/bash".

Instalation OK, but only graphic mode when user is not root.

---

### Post by John Doe on 2007-04-01
Has anyone tried to install Samsung's Unified Printer Driver in Ubuntu 7.04 beta with any success?

---

### Post by noMScraig on 2007-05-24
I am more of a newbie so here is some steps that really helped me

login to nautilus as su in terminal which gives you write permission to root

su nautilus

browse to the cdroot folder that you created and double click on autorun which will start the installation

installation found my samsung clx-3160 without a problem and worked on reboot

Next going to scanner and fax...will post my results.

---

### Post by rusty0101 on 2007-07-03
If your printer is supported in the package, take a look at the SPLIX package.

```
 sudo apt-get install splix 
```

will install the package. 

Then open the printers control panel under System > Administration

Double click on 'New Printer' and start setting up the printer as you normally would.

The biggest problem I had wa that there are some 4 splix drivers to select from and only one or two are 'english.' The problem is that the pick list just indicates that it is driver 1.0, not what language it is in. You don't end up running into the language issue until you go to print something and then the dialog is in French or some other language.

That said, it allows me to use my color laser printer at 1200 dpi, rather than the 600 dpi that Samsung's driver is limited to. Also my ML-1750 ends up with different resolution options as well.

Home page for the project, including a list of supported printers is [http://splix.ap2c.org/]("http://splix.ap2c.org/")

---

### Post by dubstar on 2007-09-20
model: samsung 3051N (networked)

on ubuntu 7.04 and kubuntu 7.04 works fine with the latest unified driver. once you've set all the extracted files as read and write and executable where applicable.

altho i did have to copy the driver off the cd whatever it was .ppd manually, but once that was done the unified driver worked fine, and configured cups. 

to note, for some reason, manually setting it up, via system - admin - printing or the kubuntu equivalent, did not work, altho the driver's setup used the same details.... bizarre. dont know if its to do with permissons? im no expert.

so in summary, copy relevant .ppd file off cd to the local machine ( you can see where the files are stored by a simple find *.ppd from the ubuntu menu.

extract the downloaded driver, right click on its folder, and setup for read/write access

open terminal, browse to aforementioned folder, and then type "sudo ./autorun" and then follow on screen instructions.

it worked for me. the autorun off the cd never did.

---

### Post by roxy99 on 2007-10-12
I am going to be installing the Samsung 4521f on Ubuntu 7.04 and was wondering why you are copying the ppd file from the cd if you are downloading anyway the latest unified driver?

---

### Post by pe3no on 2008-01-08
> **noMScraig said:**
> 
[...]

installation found my samsung clx-3160 without a problem and worked on reboot

Next going to scanner and fax...will post my results.

Hi, noMScraig :)

I would like to buy Samsung CLX-3160FN and use it with Ubuntu, via USB only :) :) :)
Could you, please, tell me how your "All-in-one" works under Ubuntu?

1. How is the quality of printing (colour and black-and-white)?
2. Does scanning at flatbed work ok?
3. Does ADF scanning work fine too?

Thank you very much in advance.

BestRegards~~Piotrek~~pe3no.

---

### Post by tayroni on 2008-04-22
Samsung SCX-4200 scanner does not work on Ubuntu 8.04 Hardy Heron
Summary: I have installed the samsung unified driver in gutsy and on hardy. The scanner works on gutsy but NOT on HARDY.

Description: I've installed the driver first using the script provided by samsung, and manually. The manual installation was done because that the script allows /etc read and write by users (I really want to know the name of the programmer who did this mess!)

In both ways: installation by script or manually, the driver for the printer and scanner works on a clean install of gutsy. The same don't happen for hardy: the printer works but the scanner is not recognized by xsane.

Output of sane-find-scanner (both Gutsy and Hardy). Using sudo scanimage -L, the scanner is found on gutsy, but not on hardy.
__________________________________________________ __________________________________________________ __________________________________________________ _
found USB scanner (vendor=0x04e8 [Samsung], product=0x341b [SCX-4200 Series]) at libusb:002:003
__________________________________________________ __________________________________________________ __________________________________________________ _


On GUTSY (sudo xsane and sudo scanimage -L WORKS), the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.159257] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu kernel: [ 1263.246583] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.246596] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.246662] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.352916] lp0: using parport0 (interrupt-driven).
Apr 21 19:14:25 galileu kernel: [ 1263.394944] pnp: Device 00:0b disabled.
Apr 21 19:14:25 galileu rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:14:25 galileu kernel: [ 1263.450626] pnp: Device 00:0b activated.
Apr 21 19:14:25 galileu kernel: [ 1263.450638] parport_pc 00:0b: reported by Plug and Play ACPI
Apr 21 19:14:25 galileu kernel: [ 1263.450702] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Apr 21 19:14:25 galileu kernel: [ 1263.564420] lp0: using parport0 (interrupt-driven).
__________________________________________________ __________________________________________________ __________________________________________________ _


On HARDY (sudo xsane DOESN'T WORK and sudo scanimage -L don't find the scanner) the relevant lines of /var/log/syslog are
__________________________________________________ __________________________________________________ __________________________________________________ _
Apr 21 19:11:46 kepler kernel: [ 1166.177485] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.236853] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.253490] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.257871] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.275009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler rmmod: ERROR: Module ppdev does not exist in /proc/modules
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.282338] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.287454] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler kernel: [ 1166.453319] lp: driver loaded but no devices found
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.511863] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.516347] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_956').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.562628] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.567925] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_888').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.589722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:11:46 kepler NetworkManager: <debug> [1208815906.594256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/platform_parport_pc_632').
Apr 21 19:17:01 kepler /USR/SBIN/CRON[7696]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
__________________________________________________ __________________________________________________ __________________________________________________ _


So, please, help me to figure out what's happening with the samsung scx-4200 scanner on hardy. Any help is welcome.


PS: To install the driver manually (best way), only for reference:

1) Download 20070720152943906_UnifiedLinuxDriver.tar.gz from samsung, extract the files, go to new directory cdroot and type these commands
cp Linux/noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
cp -r Linux/noarch/at_opt/share/ppd/* /usr/share/ppd/custom/
cp Linux/i386/at_root/usr/lib/libmfp.so.1.0.1 /usr/lib/
cp Linux/i386/at_root/usr/lib/sane/libsane-smfp.so.1.0.1 /usr/lib/sane/
cp Linux/i386/at_root/usr/lib/cups/backend/mfp /usr/lib/cups/backend/
cp Linux/i386/at_root/usr/lib/cups/filter/* /usr/lib/cups/filter/
cd /usr/lib
ln -s libmfp.so.1.0.1 libmfp.so.1
ln -s libmfp.so.1.0.1 libmfp.so
cd sane
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so.1
ln -s libsane-smfp.so.1.0.1 libsane-smfp.so

2) Edit /etc/sane.d/dll.conf and add the line "smfp" to the end of file. Add yourself to the groups lp and scanner.

3) Reboot

---

### Post by tayroni on 2008-04-24
I DID IT!!!!! The SAMSUNG SCX-4200 now works on HARDY HERON!!!!!!

The problem was the driver software by SAMSUNG looks for the usb device on

/proc/bus/usb/00*/00*

and 8.04 drops support to /proc/bus/usb/00*/00* and port all software to look only on /dev/bus/usb/00*/00*

To reenable support on /proc/bus/usb I edited

/etc/init.d/mountdevsubfs.sh

and modify the lines

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

to

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

and reboot.

ONE CAVEAT: Using patched /usr/lib/libmfp.so.1.0.1 from [http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian](http://jacobo.tarrio.org/Samsung_SCX-4200_on_Debian) allows me to use xsane with normal user.

---

### Post by jackbox on 2008-07-05
How do you edit the LPD of the printer so the Jacobo Terrio fix works? I cannot figure out how to change the LPD to /dev/usb/lp0 as instructed for his modified libmfp.so.1.0.1 file to work. Now applications cannot find any scanner instead of the segmentation. Your help would be appreciated.

---

