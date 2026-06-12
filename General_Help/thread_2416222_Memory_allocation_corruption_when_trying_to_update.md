---
title: "Memory allocation corruption when trying to update oem-audio-hda-daily"
date: 2019-04-07
forum: General Help
---

### Post by martinv279 on 2019-04-07
I was trying to do a regular sudo apt-get update/upgrade, when I got a lot of errors on both commands. I am using Ubuntu 16.04. After this, I tried to purge and reinstall the Module "oem-audio-hda-daily", but after I did that I have no sound whatsoever now. I only get Dummy Output. 
This sound problem has been persistent ever since I have installed ubuntu 16.04 on my Dell Inspiron 5767, but I solved it SOMEHOW a couple of months ago. So this reappearance of that sound problem is really annoying, especially that now I can not even try the same routine since I get errors like:
> snd-hda-codec-ca0132.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-145-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version..

I have uploaded the feedback (to this link [https://justpaste.it/4ekbc](https://justpaste.it/4ekbc) )that I get in terminal when I run:
sudo apt-get update
sudo apt-get upgrade.

You can see a lot of IGN and error/fails on update, and dpkg fails on upgrade.

---

