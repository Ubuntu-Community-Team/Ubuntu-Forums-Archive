---
title: "Getting z22 palm to sync with jpilot"
date: 2007-12-10
forum: General Help
---

### Post by gishaust on 2007-12-10
On and off for the last two weeks i have been trying to get my z22 palm to sync with jpilot.  I tried all the tutorials on udev and they never worked. Below is what worked for me....

The packages I have installed are,
sudo apt-get install jpilot (This is the gui for jpilot)
sudo apt-get install pilot-link (jpilot recommends that you install this)

Then I place the following in jpilots file->preferences->settings->serial port.
/dev/ttyUSB1

Then as an old windows user I restarted the computer. 

Then I synced the pda first and then followed up straight away by syncing jpilot and it worked first go.

---

### Post by K.Mandla on 2007-12-20
Moved to General Help.

---

