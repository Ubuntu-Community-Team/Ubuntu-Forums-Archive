---
title: "USB stick not mounting"
date: 2012-12-11
forum: General Help
---

### Post by jso22785 on 2012-12-11
Hi,

I would like to know what the below error means:

[1366883.956615] usb 2-1: new full-speed USB device number 21 using ohci_hcd
@ [1366899.184338] usb 2-1: device descriptor read/64, error -110
@ [1366916.100536] usb 2-1: device descriptor read/all, error -110 

My USB stick doesn't get recognized and this is the error I get. I would like to know what error -110 means.

---

### Post by Rebelli0us on 2012-12-11
"-110" is just an arbitrary number. Try gparted, you can mount/dismount any drive from there.

---

### Post by rnerwein on 2012-12-11
> **jso22785 said:**
> Hi,

I would like to know what the below error means:

[1366883.956615] usb 2-1: new full-speed USB device number 21 using ohci_hcd
@ [1366899.184338] usb 2-1: device descriptor read/64, error -110
@ [1366916.100536] usb 2-1: device descriptor read/all, error -110 

My USB stick doesn't get recognized and this is the error I get. I would like to know what error -110 means.
hi
your errno 110 tells you: #define ETIMEDOUT   110 /* Connection timed out */
(those errnos are normaly for network - but i think it can make sense in your problem. looks like the system recognize your usb but get's no answer from it ( but i ain't really know).
for errnumbers you can look at:
 /usr/include/asm-generic/errno-base.h  (errno 1 to 34)
and
/usr/include/asm-generic/errno.h (errno 35 to 133)
cheers

---

