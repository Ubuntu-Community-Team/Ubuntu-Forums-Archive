---
title: "clamav on ubuntu touch/how?"
date: 2014-05-05
forum: General Help
---

### Post by colsk on 2014-05-05
Hi,

My local store had a price slasher weekend on Nexus 7 2013, so I bagged a deal on one knowing touch is supported for the device. Pleasantly surprised that everything works fine with flashing the device first time in under an hour. Now, my initial research showed I could run the main apps I wanted, ufw, ssn, vpn and clamav (or other basic terminal based virus check). That is all fine except for the clam, which is not a biggie, I can always schedule periodical scans from my desktop with avast.

However, I have seen some general searches showing people claiming to run clamav on tablets and I would like to do it, if possible. My quick initial attempts were to try pkcon from adb/bootloader. It connects up, goes through most of the process then fails at a point saying daemon has crashed. Apparently because the package is not a click package? So then I tried a straightforward apt-get install and push process but that runs into permissions/lock file aborts which as I understand now is not a possible way to install on touch. I even looked at the touch app store in the browser on the tablet that has clamav listed as available with reviews but whenever I tried to follow the install app link it either returns a link unavailable or dead.

So, this was just a quick initial test after the OS setup.Does anyone know if there is a fundamental issue with exploring it any further at this stage (given the development stage status of touch at this time) or indeed if anyone can confirm it has worked form them?

cheers

---

### Post by grahammechanical on 2014-05-05
As far as I know everything about Ubuntu on phones/tablets is experimental and will remain so until we purchase a phone/tablet with Ubuntu pre-installed. You may need to set a repository. See the headings Select your Device Image Channel and Upgrading Automatically.

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

I can tell you this. I am running desktop Ubuntu Utopic Unicorn on the devel repositories and clamav is in the software centre. Also I do not think that sufficient work has been done on converging the phone/tablet code base with the desktop code base for desktop applications to be much use when run on a tablet, even when connected to a desktop monitor. 

As I understand things a lot of work has gone into Ubuntu for phones/tablets to make the OS secure. Click packaged applications are tightly controlled by the OS to prevent malicious code from being run.

Regards.

---

