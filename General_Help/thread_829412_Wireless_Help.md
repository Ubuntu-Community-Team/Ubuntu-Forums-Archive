---
title: "Wireless Help"
date: 2008-06-14
forum: General Help
---

### Post by Lex-Man on 2008-06-14
I trying to use get access to my wireless network with Ubuntu I using a asus wl167g wireless USB dongle and connecting to a BT home hub which has a WEP key on it.

Using Ubuntu I can see the network and enter my key but when I do the connection fails.

---

### Post by pytheas22 on 2008-06-14
Try doing this:
```

sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt73usb' >> /etc/modprobe.d/blacklist

apt-get install build-essential rutilt
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*/Module
make
make install
exit
```

then reboot and see if you can connect.  This is going to blacklist the default Ubuntu drivers for your card, which don't work well for a lot of people, and replace them with a driver that is much more reliable.

The important to note is that using the new driver, you will not be able to connect with Network Manager.  Instead, you need to use a program called Rutilt, which will also be installed if you follow the instructions above.  You can find Rutilt at System>Administration>Rutilt Wireless Manager.

Let me know how this goes.  If you still can't connect after doing the stuff I list above, please post the output of:
```

lspci
lsusb
iwconfig
cat /etc/modprobe.d/blacklist
```

---

