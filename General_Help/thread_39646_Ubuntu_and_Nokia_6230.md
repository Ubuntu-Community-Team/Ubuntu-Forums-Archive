---
title: "Ubuntu and Nokia 6230"
date: 2005-06-05
forum: General Help
---

### Post by Digitallysick on 2005-06-05
Does anyway know of a way that i can use my nokia 6230 with ubuntu? I have used it with winxp and the data cable with nokie pc suite for sometime. I have read posts of possible bluetooh to the phone, but i dont have bluetooth on the old comp, and would like to use the data cable, any ideas????

---

### Post by rjs on 2005-06-06
this might help you - [http://tuxmobil.org/phones_survey_nokia.html](http://tuxmobil.org/phones_survey_nokia.html)

paz y amor,
-rjs.

---

### Post by Digitallysick on 2005-06-07
thats a great site, but im currently bluetoothless on this old pc. I guess i will have to find an old bluetooth adapter, thanks

---

### Post by nicklogan on 2005-06-20
These sites sites or threads very helpful to me in getting my 6230 working with bluetooth:

[http://zenit.xs4all.nl/html/deb6230en.html#setup](http://zenit.xs4all.nl/html/deb6230en.html#setup)
[http://www.ubuntuforums.org/showthread.php?t=41498&highlight=gnokii](http://www.ubuntuforums.org/showthread.php?t=41498&highlight=gnokii)
[http://www.ubuntuforums.org/showthread.php?t=41180&highlight=gnokii+6230](http://www.ubuntuforums.org/showthread.php?t=41180&highlight=gnokii+6230)
[http://www.ubuntuforums.org/showthread.php?t=41180&highlight=gnocky+alien](http://www.ubuntuforums.org/showthread.php?t=41180&highlight=gnocky+alien)

I used a D-Link DBT-120 usb bluetooth dongle.

In general, this is what worked:

Install bluez, gnokii, and xgnokii or gnocky. (see the links above)

Turn on bluetooth on the 6230 and make it discoverable (known) to other devices.

In a root terminal, restart bluez: /etc/init.d/bluez-utils restart

Type 'hciconfig -a' then ' hcitool scan' .
The output should be the MAC address of the phone and the name you gave it. Note down or cut the address number.

Type 'sdptool browse 00:E0:03:xx:xx:xx' using your address.
Note the channel under "OBEX Object Push" . (9 in my case)

Edit /etc/bluetooth/rfcomm.conf and add the following using your address and channel and save:

rfcomm0 {
        device 00:E0:03:xx:xx:xx;
        channel 9;
        comment "6230 OBEX push";
}

Restart bluez again: '/etc/init.d/bluez-utils restart' .

Run 'rfcomm bind /dev/rfcomm0 00:E0:03:xx:xx:xx 9' .

Run 'rfcomm connect /dev/rfcomm0 00:E0:03:xx:xx:xx 9' 

It should tell you you're connected.

Edit /etc/gnokiirc to include the following:

[global]
port = 00:E0:03:xx:xx:xx
model = 6310
initlength = default
connection = bluetooth
use_locking = no
serial_baudrate = 19200
rfcomm_channel = 9
smsc_timeout = 10
[gnokiid]
bindir = /usr/sbin/
[connect_script]
TELEPHONE = 1234567890 (your number if wanted)
[disconnect_script]

Run xgnokii or gnokii and you should be able to open the addressbook on the phone.

I'm new at this but i thought I'd share this - maybe others can add more.

---

