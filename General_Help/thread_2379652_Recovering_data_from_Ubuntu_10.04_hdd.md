---
title: "Recovering data from Ubuntu 10.04 hdd"
date: 2017-12-07
forum: General Help
---

### Post by furoido2 on 2017-12-07
Hi guys,

My desktop recently died and I want to recover the data from my hdd. I am not 100% sure which version of Ubuntu it is running, but I'm pretty sure its 10.04.

I presume the way to recover the data is to stick the hdd in an enclosure and plug it into my (Windows) laptop. 

However, I'll need to create an Ubuntu partition in the laptop to allow it to read the hdd. 

My question is what version of Ubuntu should I install? Will the latest version read an hdd running 10.04, or should I install 10.04? (At this stage I don't care what version is installed - I simply want to get access to the files on the hdd).

Also, is there anything else I need to do such as change the BIOS settings to allow the laptop to read my hdd?

(Btw, I am assuming that installing Ubuntu on the laptop will automatically allow it to read my hdd and to copy and save the data, and that there's nothing more to do. Please correct me if I am wrong!).

Many thanks!

---

### Post by Impavidus on 2017-12-08
You don't have to install Ubuntu, running a life session should be sufficient and doesn't risk destroying your Windows. It doesn't have to be the same version, any more recent version should work.

Create a life usb of Ubuntu 16.04 (or similar), put it in your Windows laptop and boot it. Select "Try Ubuntu before installing". Put the old hard drive in an enclosure and plug it into a second usb port. You should be able to access the hard drive. Save the files on yet another usb drive, the Windows drive or the cloud.

If you want to save the files to your Windows drive, make sure you fully shut down Windows (no fast boot, if running Win8 or later) and don't use partition C. Most Windows systems have something called "Drive D:", which should be safe. Otherwise Ubuntu may refuse to write to the Windows drive or may damage Windows.

---

### Post by furoido2 on 2017-12-08
Thank you SO much for that, Impavidus!

---

