---
title: "Wireless dead with Edgy upgrade(Belkin Wireless Adapter)"
date: 2007-03-08
forum: General Help
---

### Post by jdway on 2007-03-08
I have install Edgy on a dell workstation and the wireless does not work. I am connecting to the internet via usb bridge to a belkin wireless network adapter. Any ideas on how to get it running. I do not know how to even enter the WEP key because I have never worked with wireless compatibility in Ubuntu.

---

### Post by DagMan on 2007-03-08
See if you have a wireless interface when you do this
sudo network-admin
And if so set it, make sure not to miss the DNS part but likely it's already done since you're using the wired network.

If you have wireless there and it still doesn't work after that: 
cd /lib/firware
ls
And does that match up to the output of this:
uname -r

If not, you might have to compile your network driver module and firmware.  You can, at your own risk, try copying it to the name of the new kernel and rebooting.
cd /lib/firmware
cp -r NAME-OF-DIRECTORY `uname -r`

---

