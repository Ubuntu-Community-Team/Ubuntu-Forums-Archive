---
title: "WinUSB Exit code 256 +log"
date: 2017-03-19
forum: General Help
---

### Post by donarennekstann on 2017-03-19
Hello. I wanted to create an bootable usb (win vista sp2 official) and i was using winusb.
I started it from the terminal (sudo winusbgui) and selected the .iso file and my usb stick.
Before that i used GParted to create an msdos table in fat32 with boot flag on it.

Here is the log of winusb 

Installation failed !
Exit code: 256
Log:
Formatting device...
Wait 3 seconds for block device nodes to populate...
mkfs.fat: warning - lowercase labels might not work properly with DOS or Windows
mkfs.fat 3.0.28 (2015-05-16)
Mounting...
Copying...
grep: /media/winusb_iso_1489934372_19682/sources/cversion.ini: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;    @No such file or catalog.
Installing grub...
&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072; &#1076;&#1083;&#1103; &#1087;&#1083;&#1072;&#1090;&#1092;&#1086;&#1088;&#1084;&#1099; i386-pc.
&#1059;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1082;&#1072; &#1079;&#1072;&#1074;&#1077;&#1088;&#1096;&#1077;&#1085;&#1072;. &#1054;&#1096;&#1080;&#1073;&#1086;&#1082; &#1085;&#1077;&#1090;.  @ No errors
Installing grub.cfg...
Exiting...
Syncing...
/usr/bin/winusb: &#1089;&#1090;&#1088;&#1086;&#1082;&#1072; 78: 23512 &#1047;&#1072;&#1074;&#1077;&#1088;&#1096;&#1077;&#1085;&#1086;      while true; do  @Finished
    sleep 0.05; echo 'pulse';
done
Cleaning...
/usr/bin/winusb: &#1089;&#1090;&#1088;&#1086;&#1082;&#1072; 78: 23689 &#1047;&#1072;&#1074;&#1077;&#1088;&#1096;&#1077;&#1085;&#1086;      while true; do       @Finished
    sleep 0.05; echo 'pulse';
done
Unmounting and removing '/media/winusb_iso_1489934372_19682'...
Unmounting and removing '/media/winusb_target_1489934372_19682'...

What should i do? Please help, i am trying to make an bootable usb for three (!) days now))))

---

