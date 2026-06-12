---
title: "Starting Bluetooth from a script?"
date: 2015-11-07
forum: General Help
---

### Post by chess1974lover on 2015-11-07
Hello Ubuntu users,

I have just moved from Raspbian Wheezy to Ubuntu MATE 15.10 on a Raspberry Pi 2.

On Wheezy I used to connect to a Bluetooth device at boot using a script. The script called bluez-simple-agent and rfcomm to establish the connection. This way, I could run the Pi2 headless.

On Ubuntu MATE 15.10 there seems to be no bluez-simple-agent. I can connect to the device manually with Bluetooth Manager, but would like to know which command I should put into an init file to connect without using the GUI.

All the device information is written correctly in /etc/bluetooth/rfcomm.conf.

Obviously there should be an alternative to bluez-simple-agent?

Thanks for any tips.

---

### Post by wow64gr on 2016-01-14
Same here, after adding second device over GUI, GUI stopped working and all manuals have bluez-simple-agent and co in them.

---

### Post by chess1974lover on 2016-01-20
The problem seems to be that:
(1) BlueZ 5 does not have /usr/bin/bluez-simple-agent (unlike BlueZ 4)
(2) BlueZ 5 seems to lack documentation about how to setup a Bluetooth serial (SPP) connection that will reconnect automatically after reboot.

Did anyone solve this same situation yet?

---

