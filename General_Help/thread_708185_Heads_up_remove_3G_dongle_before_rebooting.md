---
title: "Heads up: remove 3G dongle before rebooting"
date: 2008-02-26
forum: General Help
---

### Post by stoffe on 2008-02-26
Just sharing in case someone else has this problem. :)

I had a lot of problems trying to install Wubi from the Alpha 5 CD and none of the posts here seemed to be helping.

What happened was that after reboot, and a short while of the Ubuntu progress bar, it would just drop into Busybox. And the logs didn't seem to give anything away... until I spotted that it seemed to recognize my 3G internet dongle as a CD a short while before everything went south.

Sure enough, unplugging that and it worked just fine. It's one of these thingies: [http://en.wikipedia.org/wiki/Huawei_E220](http://en.wikipedia.org/wiki/Huawei_E220) which are pretty common among several operators in Sweden. It's detected as a USB drive with a CD file system (because it has some Windows drivers on it), and somehow that got detected as the ISO instead I guess?

Is this the place to file bugs btw?

---

### Post by ago on 2008-02-26
> **stoffe said:**
> Just sharing in case someone else has this problem. :)

I had a lot of problems trying to install Wubi from the Alpha 5 CD and none of the posts here seemed to be helping.

What happened was that after reboot, and a short while of the Ubuntu progress bar, it would just drop into Busybox. And the logs didn't seem to give anything away... until I spotted that it seemed to recognize my 3G internet dongle as a CD a short while before everything went south.

Sure enough, unplugging that and it worked just fine. It's one of these thingies: [http://en.wikipedia.org/wiki/Huawei_E220](http://en.wikipedia.org/wiki/Huawei_E220) which are pretty common among several operators in Sweden. It's detected as a USB drive with a CD file system (because it has some Windows drivers on it), and somehow that got detected as the ISO instead I guess?

Is this the place to file bugs btw?

Interesting.

If the USB device also supports USB-mass storage interface which does come with a filesystem, then it will be mounted and scanned as any other device to find the ISO/installation folder. Not sure though why that would fail.

You may want to try "mounting" and browsing your device after installation and provide more info.

---

### Post by ago on 2008-02-26
A workaround on my side might be to scan only devices larger than X MB...
But I am afraid that would not be too robust.

---

### Post by ago on 2008-02-26
If you boot in debug mode (hit esc at the countdown), you should have a  /casper.log. Of course you need to boot with the usb device in...

You can mount manually the windows device and copy it over. That would help a lot.

---

### Post by stoffe on 2008-02-27
How can I do this the easiest way, now that I have gotten it to work? It only gives this failure on the install boot, when it's properly installed I can have the dongle inserted with no problem.

I'd rather not blow my installation away. :) Can I make a backup of the ubuntu directory and just restore it later or something like that, to try this out?

---

### Post by ago on 2008-02-27
> **stoffe said:**
> How can I do this the easiest way, now that I have gotten it to work? It only gives this failure on the install boot, when it's properly installed I can have the dongle inserted with no problem.

I'd rather not blow my installation away. :) Can I make a backup of the ubuntu directory and just restore it later or something like that, to try this out?

Yes simply rename the ubuntu folder to something else
Then run wubi with the dongle in, selecting verbose mode
Then at the busy box copy casper.log and any log you may see in /tmp to your windows drive (you might have to mount that manually first).

---

