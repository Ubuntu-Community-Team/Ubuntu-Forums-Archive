---
title: "ubuntu14.04 on usb stalling on netbook - lots on net - no solutions?"
date: 2015-02-21
forum: General Help
---

### Post by jones5 on 2015-02-21
New to Ubuntu. Trying to upload Ub.14 from pendrive onto samsung notebook n140. Read loads of error reports about pendrive not being recognised or read by bios. I have changed order of load up to USB HHD first etc. 

Current situation , on stroking f2 during reboot get basic black white ubuntu 'installer menu screen'. It will not cursur up or down or enter to try any of the choices?

Seems stuck. Any answers - hope not a fat issue etc as cannot stomach any of these things. Surely one of the main targets for expanding Linux/ubuntu would be netbooks/running older windows. Can't believe still getting hiccups like these after major ubuntu overhaul by conon???? Need to sell this system folks?   Anyway grateful there is an alternative to the dreadful Windows. So hopefully someone can fix?

---

### Post by jones5 on 2015-02-22
Hi All

I will risk answering my own thread. Hope that is ok. Not a Linux expert but this might help those who want to try Ubuntu or other Linux systems live booted from a pendrive. As said earlier - the method described and recommended on Ubuntu
 
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)   

- using a usb flash/pen drive, downloaded iso ubuntu 14.04 and the universal  usb installer pendrivelux was not working. I became Suspicious because the usb pendrive I had was formatted properly and checked on other machines. So suspicion fell on Usb pendrivelinux  installer and u netbootin version which i also tried without success. 

I googled a bit and came across this solution which solves the issue: 
[https://bbs.archlinux.org/viewtopic.php?id=172250](https://bbs.archlinux.org/viewtopic.php?id=172250)
In it the author describes the above scenario and both USB univesal and Unetbootin failing to create a bootable stick.

I do not understand the gobbldygook but it is a efi  vs Bios issue - bios not used any more. This is further detailed as a syslinux v4 (some USB's?) and syslinux v6 issue. V6 needs to be installed in the USB's you use. Either the USB creators or the USB univesal or unetbootin software are still using v 4. The Ubuntu (and other distros) I guess need v6 to be compatible.

A USB writer that does work is here:  [http://sourceforge.net/projects/usbwriter/](http://sourceforge.net/projects/usbwriter/)

This worked for me and I wrote both Ubuntu and elementary linux on usb to try out.

I think someone on Ubuntu main site might change the recommended usb writers as they clearly do not work for windows users trying to put linux onto usb's o try out. This results in a lot of needless frustration and surely compounds the misguided view that Linux things do not work for those who are newbies. Just a thought.

---

### Post by HermanAB on 2015-02-22
Hmm, goodness knows why the Ubuntu team still haven't figured out how to make multimode ISO files.  The trouble you ran into is unique to the cripple Ubuntu ISOs.  Pretty much all other distributions make ISO files that boot both on CDs and USB sticks with no problems.

---

### Post by jones5 on 2015-03-11
Thanks for the contribution and some useful things for newbies. i will now mark as solved.

---

