---
title: "Transferring photos from cell phone"
date: 2017-05-07
forum: General Help
---

### Post by fedora-refugee2 on 2017-05-07
Probably an easy question. I have an lgb450 (3g) cell phone and I am trying to transfer some pictures. I have it connected to my laptop with Ubuntu Gnome (yakkety) via usb, but I can't find the phone. Where Should I be looking? Anyone know any settings I should worry about?

---

### Post by TheFu on 2017-05-07
Does **lsusb** or **dmesg** show the phone as connected?
When my Nexus4 was new, I had to tell the udev subsystem how to connect to it.

If you put them on the same wifi network, you could use lots of different methods.
* rsync - needs ssh
* sftp - needs ssh
* nextcloud/owncloud - I don't consider this secure outside my LAN without a full VPN running

Watch out for SMB/CIFS/FTP methods. Those aren't secure.

Of course, none of these will be as fast as using a USB cable after you get the udev stuff fixed.  The only faster way is to move the photos to another SD inside the phone, then pull that storage out and connect insert it into an SD reader on the computer.

BTW, I searched for the udev rule needed for that phone.  Didn't see any reference to 'lgb450' anywhere.

---

### Post by Autodave on 2017-05-07
I had to enable it in my phone: it was under *Settings.*

---

### Post by fedora-refugee2 on 2017-05-07
Thanks for the help. Lsusb and dmesg do not list the phone. I checked the Settings page in my phone and set the usb connection to data but no luck. I tried setting it up on my wireless but could not find the right settings. I guess I am SOL. :(

---

### Post by Olav on 2017-05-07
I am not familiar with the LG 450. But on a similar simple (non-Android) phone I once had as a backup the way to transfer photos was to 'share' them from the phone to the laptop using Bluetooth. Had to do it one-by-one even, a proper pain. If at least the phone has a memory card you could try sticking that in a card reader.

---

### Post by SeijiSensei on 2017-05-08
> **Olav said:**
> If at least the phone has a memory card you could try sticking that in a card reader.
I looked at the phone's specs when this was first posted in search of a memory card.  It has none.

---

### Post by Autodave on 2017-05-08
When you connect it to the PC, do any new icons show on the screen? If so, it may not be identified as a phone, it would just show as a drive.

You can also try connecting the phone with the phone off and THEN turn it on and see if it is recognized that way.

---

### Post by efflandt on 2017-05-09
Which Ubuntu version are you running? Newer Android phones use MTP to connect via USB cable and I never could get MTP to work properly in 12.04 with my Samsung S3 trying all sorts of things related to MTP. But in Ubuntu 14.04 or newer it simply works with the default file manager (nautilus).

Some apps for your phone that may be of interest for transferring via WiFi: "AndFTP" sftp client. "JuiceSSH" or "ConnectBot" ssh clients. "SimpleSSHD" (works best using ssh keys) or "SSHServer" ssh servers for Android.

Note that an ssh client is installed on Ubuntu by default, but not the server. There is a meta-package called "ssh" that installs everything ssh related not already installed (openssh-server and openssh-sftp-server):```
sudo apt-get update
sudo apt-get install ssh
```.

---

### Post by Kris_M on 2017-05-09
On my phone, which is a Moto G 3rd gen 2015, when I plug usb to Ubuntu I have to swipe top down on the screen of the phone - see box USB charging this phone, tap it, choose transfer files. At this point the sdcard and internal memory will pop up in a window on Ubuntu.

You may also note that in settings/developer options/select USB configuration - mine is set to MTP.

EDIT: a close look at the LG B450 manual does not indicate any use of the USB port for anything other than charging.  You might need to get a BT dongle for the computer, set it up, and xfer files that way.

---

### Post by sp40140 on 2017-05-10
If nothing works (to connect phone via usb), you can install ESExplorer. It can work with network shares like samba. If you don't have samba set-up, you can use a server built in to the ES Explorer on TEMP basis to get the data transferred. Provided you are on same network.
Now, ES Explorer at one time in past was excellent app for android. Lately, it's been not so good (they messed it up trying to monetize it). I am really tempted to remove it from my phone. But it has lots of features and comes on handy.
So, This is not approval for the app, but just a suggestion to get your job done.

---

### Post by leunam12 on 2017-05-10
In your phone, install total Commander and the LAN plugin for Total commander and now you can access your computer's shared folders wirelessly. Open Total Commander and click the LAN plugin and create a new server that points to your PC's shared folder. Use your IP address. Something like this:```
192.168.1.121/path/to/shared/directory
```Obviously, you must use your own IP address and also you must have a shared folder. If you only enter your IP address when creating the server, it will list all your shares, which is, maybe, more convenient.

---

### Post by Olav on 2017-05-15
Suggestions to go into Developer Options, or to install this or that app, are missing the point that this isn't Android we are talking about. LG 450 is a simple flip phone.

---

### Post by Kris_M on 2017-05-15
Yes, but on that phone I believe it has bluetooth file transfer protocol. Get a BT dongle for your PC and connect the 2 .

---

