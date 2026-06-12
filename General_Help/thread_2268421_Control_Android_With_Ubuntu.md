---
title: "Control Android With Ubuntu?"
date: 2015-03-08
forum: General Help
---

### Post by michael_king2 on 2015-03-08
My wife broke her phone and I'm wondering since the digitizer is fubared is there any way for me to control the phone from the computer?

Michael

---

### Post by tgalati4 on 2015-03-09
You might have better luck plugging a USB mouse into the microUSB connector of the phone and loading an Android module to read it.

[http://www.howtogeek.com/164783/how-to-connect-mice-keyboards-and-gamepads-to-an-android-phone-or-tablet/?PageSpeed=noscript](http://www.howtogeek.com/164783/how-to-connect-mice-keyboards-and-gamepads-to-an-android-phone-or-tablet/?PageSpeed=noscript)

[https://www.youtube.com/watch?v=W8HVEHNOy7I](https://www.youtube.com/watch?v=W8HVEHNOy7I)

[http://www.makeuseof.com/tag/how-to-connect-a-usb-android-keyboard/](http://www.makeuseof.com/tag/how-to-connect-a-usb-android-keyboard/)

It's difficult to connect an Android phone to Ubuntu and it's not clear of how you could control it.  The needed software frameworks are missing.

---

### Post by efflandt on 2015-03-09
Normally you should be able to access files on the phone storage with Ubuntu 14.04 or newer (actually obsolete 13.10 supported that), if the phone is not locked. But not sure how to unlock it if locked, unless it uses a numerical PIN or password to unlock it which might work using Bluetooth or microUSB to USB connected keyboard or wireless keyboard dongle.

I have used SSHServer app to connect ssh or sftp to my Android phone (especially in Ubuntu 12.04 which did not support MTP), but that would require that SSHServer be installed, configured, running, and maybe phone unlocked for that to work over working WiFi.

Not sure how any of that works if internal storage or SD/microSD is encrypted, but unencrypted SD/microSD should be able to be read in external card reader.

PS: If you have a security app on the phone like Lookout Security, maybe there is a way to remotely backup the phone from their website, if that is not automatic. But what all you can do might depend whether you have a free version or pay version.

---

