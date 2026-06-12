---
title: "Wireless N problem."
date: 2008-03-14
forum: General Help
---

### Post by SpenceMakesSense on 2008-03-14
I have my linksys Wireless N installed using ndisgtk which is a NDISWRAPPER GUI program. And everytime I start up Ubuntu I have to keep reinstalling the drivers. Anyone know how to fix that.

---

### Post by technotika on 2008-03-17
try one of these  - both worked for me at some point
################################
1.)
sudo gedit /etc/rc.local file

just before line exit=0

add

/etc/init.d/networking restart.

################################
2.)
Type (or copy/paste) the following into Terminal to open the modules list:
gksudo gedit /etc/modules

Type the following at the end of the text document that loads (if not already present):
ndiswrapper.


Please note the second option comes from this guide that got my N card working perfectly.
Except I used the drivers from the original windows cd.
################################

HOWTO: Get Airgo-Based WiFi Enabled Using ndiswrapper

*UPDATE* February 21, 2008
Due to some changes in the ndiswrapper software, this tutorial became obsolete. As per comments in the original post, I have changed the instructions to once again make them work.

For months I was trying to get my Belkin F5D8010 Pre-N WiFi card to work in my laptop under Ubuntu Feisty Fawn (7.04). Finally I have figured it out, using the Ubuntu Documentation & the NDISwrapper page on Sourceforge. Now I present these steps to you.
Cards This Will Work On:

Note: This list is from the ndiswrapper wiki. I do not know if these steps will actually work for your card. Verified cards are in bold. If you follow these steps and they work for your card, leave a comment and I will point it out.

·         Belkin F5D8010

·         Linksys WPC511GX

·         Netgear WGM511

·         Buffalo WLI-CB-G108

·         AeroGuard AGN1023PC

·         Planex CQW-NS108AG

·         Planex CQW-NS108G

·         amsung X20 Laptop

·         GemTek WPCO-131G

·         Corega CG-WLCB108GM
Ubuntu Version Required:

Ubuntu 6.10 (Edgy Eft) or later

Because I was able to get this to work under Feisty Fawn, I am going to write these steps as if you were using that version. I will post the links for files required by Edgy and Gutsy, but I can't guarantee it will work for you. I am providing two versions of instructions: one if you can get online through a wired connection (the preferred method), and one if you cannot get online through a wired connection.
Online Version

Part One: Installing ndisWrapper

1.      Open Terminal.

2.      Type lspci -nn

3.      Look for the following: 03:00.0 Ethernet Controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 01)

o        If the line is not present, these instructions will not work for you.

4.      Type (or copy/paste) the following lines into Terminal:
sudo modprobe -r ndiswrapper
sudo apt-get --purge remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

5.      Type (or copy/paste) the following line into Terminal:
sudo apt-get install linux-headers-$(uname -r)

6.      Type (or copy/paste) the following line into Terminal:
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

7.      Navigate to Sourceforge to download the latest version of ndisWrapper.

8.      Save the file you download in your Home folder

9.      Type (or copy/paste) the following lines into Terminal:
tar xvfz ndiswrapper-[current version].tar.gz
cd ndiswrapper-[current version]
(Where [current version] is the version number of the file you downloaded. i.e.: ndiswrapper-1.52.tar.gz)

10.  Type (or copy/paste) the following lines into Terminal:
sudo make uninstall
sudo make

11.  Type (or copy/paste) the following lines into Terminal:
fakeroot
sudo make install

Part Two: Installing the drivers

1.      Type (or copy/paste) the following into a terminal to download the drivers:
wget [http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz](http://77.91.202.10/~alpoimco/Satanas/belkin_pre-n.tar.gz)
Mirror (If the first link is down): wget [http://www.someawe.com/uploads/belkin_pre-n.tar.gz](http://www.someawe.com/uploads/belkin_pre-n.tar.gz)

2.      Type (or copy/paste) the following into a terminal to extract the drivers you just downloaded:
tar xvfz belkin_pre-n.tar.gz
cd belkin_pre-n

3.      Type (or copy/paste) the following line into terminal:
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

4.      Type (or copy/paste) the following line into terminal:
sudo ndiswrapper -i NetAni.inf

5.      Type (or copy/paste) the following line into terminal:
ndiswrapper -l

6.      Look for the following:
tmimo3p: driver installed
     device (17CB:0001) present

7.      Type (or copy/paste) the following into Terminal to activate the driver:
sudo depmod -a
sudo modprobe ndiswrapper

8.      Type (or copy/paste) the following into Terminal to check for errors:
tail /var/log/messages

9.      Type (or copy/paste) the following into Terminal to open the Network Manager:
gksudo network-admin

10.  Verify the connection labeled "Wireless connection" says "Roaming mode enabled" beneath it.

11.  Perform the following steps if it does not say "Roaming mode enabled:"

1.      Click the Wireless connection to highlight it.

2.      Click the Properties button to open the properties window.

3.      Click the check box next to Enable roaming mode and click Ok.

4.      Verify that the wireless connection now says "Roaming mode enabled."

12.  Click the close button on the Network manager to close it and return to the Terminal.

13.  Type (or copy/paste) the following into Terminal to create an alias for your wireless card:
sudo ndiswrapper -m

14.  Type (or copy/paste) the following into Terminal to open the modules list:
gksudo gedit /etc/modules

15.  Type the following at the end of the text document that loads (if not already present):
ndiswrapper

16.  Reboot your system to make sure everything is in full working order
Offline Version

1.      Open Terminal.

2.      Type lspci -nn

3.      Look for the following: 03:00.0 Ethernet Controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 01)

o        If the line is not present, these instructions will not work for you.

4.      Download the files you need to install the drivers:

o        Download the driver file from either here or here. This file is required for all distributions of Ubuntu.

o        Download the ndisWrapper files for your distribution:

§         Ubuntu 6.10 (Edgy Eft):
ndiswrapper-common
ndiswrapper-utils-1.8
ndisgtk

§         Ubuntu 7.04 (Feisty Fawn):
ndiswrapper-common
ndiswrapper-utils-1.9
ndisgtk

§         Ubuntu 7.10 (Gutsy Gibbon):
ndiswrapper-common
ndiswrapper-utils-1.9
ndisgtk

5.      Copy the four files you downloaded to your Home folder on your Ubuntu system using a flash drive, CD-ROM, or other means.

6.      Open terminal on your Ubuntu system.

7.      Type (or copy/paste) the following into Terminal to install ndisWrapper:
sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb

8.      Type (or copy/paste) the following into a terminal to extract the drivers you just downloaded:
tar xvfz belkin_pre-n.tar.gz
cd belkin_pre-n

9.      Type (or copy/paste) the following line into terminal:
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

10.  Type (or copy/paste) the following line into terminal:
sudo ndiswrapper -i NetAni.inf

11.  Type (or copy/paste) the following line into terminal:
ndiswrapper -l

12.  Look for the following:
tmimo3p: driver installed
     device (17CB:0001) present

13.  Type (or copy/paste) the following into Terminal to activate the driver:
sudo depmod -a
sudo modprobe ndiswrapper

14.  Type (or copy/paste) the following into Terminal to check for errors:
tail /var/log/messages

15.  Type (or copy/paste) the following into Terminal to open the Network Manager:
gksudo network-admin

16.  Verify the connection labeled "Wireless connection" says "Roaming mode enabled" beneath it.

17.  Perform the following steps if it does not say "Roaming mode enabled:"

1.      Click the Wireless connection to highlight it.

2.      Click the Properties button to open the properties window.

3.      Click the check box next to Enable roaming mode and click Ok.

4.      Verify that the wireless connection now says "Roaming mode enabled."

18.  Click the close button on the Network manager to close it and return to the Terminal.

19.  Type (or copy/paste) the following into Terminal to create an alias for your wireless card:
sudo ndiswrapper -m

20.  Type (or copy/paste) the following into Terminal to open the modules list:
gksudo gedit /etc/modules

21.  Type the following at the end of the text document that loads (if not already present):
ndiswrapper

22.  Reboot your system to make sure everything is in full working order

---

### Post by adult swim on 2008-03-17
i had this problem and adding nidswrapper to /etc/modules as tecknotika pointed out took care of it

---

### Post by SpenceMakesSense on 2008-03-17
> **adult swim said:**
> i had this problem and adding nidswrapper to /etc/modules as tecknotika pointed out took care of it

im not entirely sure how to do this but it sounds simple could you explain?

---

### Post by adult swim on 2008-03-18
hit alt-F2
type in
```
gksudo gedit /etc/modules
```
then go to the bottom of the text that is displayed in the text editor that pops up
go to a new line and type in ndiswrapper
save the file and close it and after you reboot your driver should load automatically

---

