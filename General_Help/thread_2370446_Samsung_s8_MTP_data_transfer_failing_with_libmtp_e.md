---
title: "Samsung s8 MTP data transfer failing with libmtp error 'Could not send object'"
date: 2017-09-03
forum: General Help
---

### Post by makem2 on 2017-09-03
I am using MTP when connecting my Samsung s8 with Android v8 to my laptop.

```

makem@ssdTOSH:~$ lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
makem@ssdTOSH:~$

```

Extract from mtp-detect:

```

makem@ssdTOSH:~$ mtp-detect
libmtp version: 1.1.10


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 3, dev 12
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP ERROR: couldnt parse extension samsung.com/devicestatus:1
Error 1: Get Storage information failed.

```

It goes like this:

1. Connect phone vis USB: Phone appears in File manager as unmounted
2. Click on the entry: Phone shows a permissions request 'allow or not'
3. Allow makes no apparent change to File Manager status- phone is still not mounted.
4. Click on the entry in File manager and the phone contents are listed and viewable at any level. Phone is mounted
5. Folders and files can be created in any of the phone folders.
6. Copy a file from the laptop and attempt to paste to mtp://[usb:003,027]/Phone/Movies/
7. libmtp error
8. Now unable to create a folder or file in the 'Movies' folder.
9. Failed to create directory "New Folder"; libmtp error: Could not send object info.
10. Phone is still mounted but unable to browse out of the 'Movies' folder.
11. The 'Movies' folder is browseable from within the phone.

Running mtp-detect before any attempt to copy /paste a file causes a permission requested on the phone. When granted it is not possible to browse the phone contents and any attempt to do so produces another permissions request. So a circular problem.

I have installed the gmtp and mtp-tools packages.

Also installed are:
libmtp-common
libmtp-runtime
libmtp9

The phone was last automatically updated on 1/8/17. I am sure that I have been able to copy paste file back and forth in the past so I am not sure if the problem lies with xubuntu or the phone.

---

