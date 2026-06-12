---
title: "ndiswrapper errors??"
date: 2007-09-23
forum: General Help
---

### Post by giant22000 on 2007-09-23
I've got a gateway ml3109 and have followed a guide to get wireless networking and sound working and it involves ndiswrapper.  I finally got ndiswrapper to compile and install.  I try to install a driver that has been reported to work, but i'm getting an error message.  I execute the command and these are the results I get:

ndiswrapper -i net8185.inf
net8185.inf already installed!

ndiswrapper -l
net8185.inf: invalid driver!

So I try to remove the driver and re-install it:

ndiswrapper -r net8185.inf
Can not uninstall net8185.inf, file or directory does not exist.

Also under the GUI it does not show up as being an installed driver.

Any ideas?  Thanks for you help!

---

### Post by giant22000 on 2007-09-23
bump

---

### Post by CrazyBoyD on 2007-09-25
I just set this up myself.  The key is apparently to extract the archive onto your desktop, and install from the command line inside the resulting folder on the desktop.  Make sure you've removed any failed install first.

---

### Post by danbh on 2007-09-25
can you post a link to the guide you were using?

---

### Post by taylmeistr on 2007-10-16
I had the same problem on my Toshiba Satellite 1800 S203 while trying to get a Belkin F5D7010 v7 Wifi card set up with ndiswrapper.

My (newbie) mistake was that on the first run through, I executed all of the install commands from my username rather than switching to "root" (sudo su - [enter password]).

To straighten it all out - I first uninstalled my erroneous driver install (nsidwrapper -r net8185) from my "username prompt".... then I checked to be sure it was gone (ndiswrapper -l) and got the "all clear" (nothing there).

Then I repeated the same process as "root" just to be sure the driver was completely uninstalled.......

Then, as CrazyBoyD mentioned above, I repeated the install process as "root" from inside the directory where I had extracted the net8185.inf driver file. Everything works perfectly now...

Here are the directions I used for the driver install (performed from within the directory where the driver was extracted):

1.       Card: Belkin Wireless G Cardbus PCI F5D7010 ver.7 (Do Not Use the Driver from the CD it only Crashes Ndiswrapper.

o        Chipset: Realtek 8185

o        Driver: net8185 from ([http://www.realtek.com.tw/](http://www.realtek.com.tw/)) Search and Download the windows driver for L8185

o        Using Mandriva 2007.0 Kernel 2.6.17-5mdv

o        Using Fedora Core 6 Kernel 2.6.19-1.2911.6.5.fc6.stk16 Downloaded new kernel with stack set to 16k from ([http://www.linuxant.com/driverloader/wlan/full/downloads-fc6-kernel-i686.php](http://www.linuxant.com/driverloader/wlan/full/downloads-fc6-kernel-i686.php))

o        dkms-ndiswrapper-1.37 kernel driver installed in Mandrivia

o        dkms-ndiswrapper-1.38 kernel driver installed in Fedora Core 6 ([http://freshrpms.net/packages/](http://freshrpms.net/packages/))

o        Installation : Install most current ndiswrapper and dkms for you *nix system as of this writing This card is working in mandriva and fedora. You will have to try it on your distribution of *nix. You have to unzip the driver into a directory you can access. There will be 3 files net8185.inf net8185.sys net8185.cat. Open a terminal and change to user root with su and root password, then type ndiswrapper -i net8185.inf in the folder where you extracted the driver files hit enter. next ndiswrapper -l shows net8185 driver installed we now have to get the device id from root prompt type lspci -n at the bottom of the list is the belkin card card ID info 1799:701f write this down you will need it for the next portion of the installation. Now from root prompt type ndiswrapper -a 1799:701f net8185 hit enter this associates the net8185 driver with the device ID of the belkin card. from root ndiswrapper -l should now show

<br>net8185 : driver installed<br>&nbsp;&nbsp;&nbsp;device (1799:701f) present<br>
from root prompt type modprobe ndiswrapper it will pause for a moment and then the lights on the card should come on. Once the card is running from root prompt type ndiswrapper -m to install an alias for you so the card will activate on boot. Card pulled an ip my mandriva server and associated with the linksys router running dd-wrt 23sp2. On Fedora: As soon as the card is recognized it and the ndiswrapper kernel module loads fine, run 

ndiswrapper -m
(as root). Then add the line 

alias wlan0 ndiswrapper
to /etc/modprobe.conf. After this you can now go to configure it by running the &#8220;Network&#8221; program from system settings (or just run system-config-network). Select &#8220;New&#8221; > &#8220;Wireless connection&#8221;. The card should show up like &#8220;wlan0 (ndiswrapper)&#8221;. Proceed with the rest of the settings. If you want, you can check here to activate it at boot time. Note: If you are using a WEP key in hexadecimal format (numbers and letters from A to F) make sure you proceed it with a 0x when prompted.

---

### Post by GraFfiX420 on 2007-10-16
ndiswrapper -i net8185.inf
net8185.inf already installed!

ndiswrapper -l
net8185.inf: invalid driver!

So I try to remove the driver and re-install it:

ndiswrapper -r net8185.inf
Can not uninstall net8185.inf, file or directory does not exist.

**instead of ndiswrapper -r net8185.inf try ndiswrapper -r net8185

---

