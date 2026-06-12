---
title: "WINE and USB support"
date: 2014-09-04
forum: General Help
---

### Post by tm-hart on 2014-09-04
While configuring a Windows program (WSJT-X ver. 1.3) for use under WINE on Ubuntu 14.04, I needed to set a WSJT-X "CAT" port.  A USB cable connects the computer to the radio.  WSJT-X has a drop down menu to select a device.  Choosing "USB" on the menu did not work.

**Solution:** Go to WINE's ".wine/dosdevices" folder.  Create a symbolic link from "USB" to "com2":

                               ** #ln -s /dev/ttyUSB0 com2**

Then, re-open WSJT-X and select "com2" on the drop down list.  CAT control now works.  Tests run on: a Kenwood TS-590S (USB cable) and an Icom IC R-75 (USB to Serial cable).  The same approach may work on other radios with a USB cable or a USB to Serial cable.

---

