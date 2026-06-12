---
title: "cant boot xubuntu 8.04beta iso image from hard drive"
date: 2008-04-06
forum: General Help
---

### Post by kissson on 2008-04-06
I followed this guide
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_boot_Ubuntu_from_ISO_image_on_hard_drive_or_USB_stick)
for 7.10, it works
but for 8.04, it doesnt
is any new kenerl parameters needed for 8.04 ? or this method is no longer supported ?
thx

I am a windows user
my windows installed on one hard drive

my method
I added grldr in c:\ and modify boot.ini addiny ```
c:\grldr="boot grldr"
```
the c:\menu.lst
> title xubuntu 7.10 live cd 
find  --set-root  /ubuntu-7.10-desktop-i386.iso
kernel  /vmlinuz  boot=casper  find_iso=/xubuntu-7.10-desktop-i386.iso
initrd  /initrd.gz
downloaded xubuntu-7.10-desktop-i386.iso on c:\
I extracted vmlinuz and initrd.gz to c:\

---

### Post by kissson on 2008-04-07
drag it up

---

