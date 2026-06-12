---
title: "Unable to boot - ? disk problem"
date: 2015-06-12
forum: General Help
---

### Post by alasdair3 on 2015-06-12
Hi,

I'd be grateful if anyone can shed some light on an issue with my system.

I've been running Ubuntu Server 14.04 for a while without issue. My system had been up for about 10 days and working fine. I turned shut it down and now it wont boot. I get a boot menu and if I try to boot Ubuntu server it just hangs on a black screen. Via advanced options from the boot menu I can boot in recovery mode. This does start to boot but eventually hangs. The attached photo shows the screen and error messages.

My system is installed onto a USB drive - sdd2. I notice that some of the errors relate to this partition and I wonder if the USB drive has become corrupted somehow or is otherwise not working - I'm not sure how to test this though or if there is anything else I can do.

Many thanks in advance for any help with this.

---

### Post by yancek on 2015-06-12
I'd try doing a filesystem check, either booted from recovery or from a Live CD.  See the link below for options:

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

---

