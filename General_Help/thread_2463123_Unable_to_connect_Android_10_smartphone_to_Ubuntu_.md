---
title: "Unable to connect Android 10 smartphone to Ubuntu 18.04 LTS laptop via USB"
date: 2021-06-04
forum: General Help
---

### Post by t0p on 2021-06-04
I have had no problem before connecting Android phones to my laptop running Ubuntu 18.04 LTS. But now I have a phone running Android 10, and the setup for connecting via USB cable has changed. So I activated Developer Tools and set the default USB behaviour to file transfer as described at [https://www.techrepublic.com/article/how-to-set-the-default-usb-behavior-in-android-10/](https://www.techrepublic.com/article/how-to-set-the-default-usb-behavior-in-android-10/).

But it doesn't work - default behaviour is set for file transfer but when I plug in the USB cable the computer does not detect the phone, not does the phone detect the computer (though the battery charging icon does appear on the phone, so there is certainly a physical connection). 

So my question is: is this normal for Ubuntu 18.04 LTS? Has anyone else successfully connected an Android 10 phone to a computer running Ubuntu 18.04 LTS? If so, how did you do this?

Another question: has anyone successfully connected a later version of Ubuntu to an Android 10 phone via USB? I would certainly consider upgrading my laptop to a more recent version of Ubuntu if users are definitely reporting that USB connection to Android 10 works. But if no one is reporting success, upgrading Ubuntu right now is not a priority. 18.04 support is set to continue for a while, and I will carry on using this version - I can still transfer the microSD card from phone to laptop, or upload files to Google Drive if I have to; it's a palaver I'd rather avoid though.

So, can anyone offer any reports or advice? Cheers.

---

### Post by tea for one on 2021-06-04
Ubuntu 20.04 with Gnome 3.36.7
Android 10

Power on phone
Attach USB cable to PC
Open settings on phone
Connected devices
USB
File transfer

Open Files (nautilus) on PC

Both internal storage and SD card (if installed) should be visible.

It definitely connected with 18.04 and I'm pretty sure that the process was similar.

---

### Post by jolibe on 2021-09-28
I have also tried connecting my smartphone via USB. I've tried plugging and unplugging many times. Until the USB connector on the phone broke. I looked at [mobile spare parts online]("https://spare-parts-mobile.com"). I thought to order. Is it possible to fix this breakdown myself? How difficult is it?

---

### Post by Autodave on 2021-09-28
I have no problem here, but I am running 20.04.  You may need to upgrade.  But, before you try that, try another cable: those wires are very thin inside and you could have broken one of them.

---

### Post by ActionParsnip on 2021-09-28
If you reboot with the device not connected and log in. Let the OS settle and connect the phone. Press CTRL + ALT + T and run:
```

dmesg | tail

```
What is the output please?

---

