---
title: "Bluetooth fails to start after removing bluetooth keyboard"
date: 2013-12-04
forum: General Help
---

### Post by sunbird on 2013-12-04
Bluetooth _used to_ work great on my Lenovo x220 laptop. Never had any issues with it. I just installed a new bluetooth keyboard, but then accidentally hit the pair button again on the keyboard, so had to delete it from the list of devices. After I did this, bluetooth greyed out, but the keyboard was still listed. Kept hitting "remove" and it would not remove it. Then I finally stopped the bluetooth service, and now it won't start. Rebooting did not fix the problem.

I think I need to manually remove the bluetooth keyboard from the config files, but I don't know where those files are located. 

Any help?

---

### Post by sunbird on 2013-12-04
I found some of the other files in /var/lib/bluetooth, but still can't get it to start. When I click on the 'on' button on the gui, it turns on for a second and then turns off.

*Edit* I also tried apt-get remove --purge bluetooth and re-install no dice.

It can't be the case that I have to fully reinstall the OS to fix this...

---

### Post by sunbird on 2013-12-05
Bump. Anyone? I tried purging all things bluetooth and bluez related, still no dice.

---

### Post by tgalati4 on 2013-12-05
Try removing the battery for an hour.  Knock it on your head for good measure.  It's possible that the bluetooth radio needs to be reset.  Also check the bluetooth status using:

```
rfill list
```

Right after pairing the keyboard:

```
dmesg | tail -50
```  Look for bluetooth error messages.

Check the BIOS to make sure that bluetooth is turned on.  Make sure the blue Fn-F5 key (or whatever your bluetooth toggle is) works consistently.  Do some research on your machine to determine how many bluetooth devices you can pair to.  Some radios can only pair to one, some 3, others 5, etc.

---

