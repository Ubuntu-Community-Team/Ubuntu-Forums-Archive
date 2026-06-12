---
title: "Backing up or making bootable image of 14.04 installation."
date: 2014-12-29
forum: General Help
---

### Post by Sieges on 2014-12-29
Hello, 

I'd like to make a bootable backup of my current 14.04 installation. Sort of like a Recovery USB with all my settings.
Documents I dont worry about, cause they are all sync to my cloud, but it's the settings that take time when setting up a system. Is this possible?

Thanks!

---

### Post by TheFu on 2014-12-29
There are many, many, many ways to accomplish this - though I think you'll want to use a RescueCD/USB boot then provide the tools with your image to restore.  However, that is storage in-efficient and IMHO, there are better techniques.
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains the options and the way I do this.
I do NOT use images anymore. Too slow and too much of an inconvenience to create since a running system cannot be made into an image safely.

Some tools that can be used to make images:
* dd
* ddrescue
* partimage
* fsarchive
You only need one.  There is also a tool that makes re-installable Linux based on a current install.  With EFI, I think that tool has not been maintained as well. Might not work at all anymore.
* [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
* [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
* [http://ubuntuforums.org/showthread.php?t=2086843](http://ubuntuforums.org/showthread.php?t=2086843) - this is what I recall. Don't know if it still works.

---

