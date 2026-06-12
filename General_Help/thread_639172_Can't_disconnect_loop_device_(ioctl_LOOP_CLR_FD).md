---
title: "Can't disconnect loop device (ioctl: LOOP_CLR_FD)"
date: 2007-12-12
forum: General Help
---

### Post by casperlingus on 2007-12-12
I have a 1GB encrypted file on my USB key (dmcrypt/LUKS).  When I plug in my key, I execute a script which searches for the first loop device, maps the file to the loop device, decrypts the device (asks for password), then mounts the decrypted volume to my HDD.  The script is not the problem as I've had this problem doing everything manually, too.

When I run the umount script, it just does everything in the reverse order.  The problem is it can't disconnect the loop device ( "losetup -d /dev/loop0" )  ==> can't umount USB key ==>  need to unsafely remove USB key. 

```

$ sudo losetup -a
/dev/loop0: [0851]:38 (/media/USB_ACR/CRYPT.FILE)
$ sudo losetup -d /dev/loop0
ioctl: LOOP_CLR_FD: Device or resource busy

$ sudo umount /dev/sdg1
umount: /media/USB_ACR: device is busy
umount: /media/USB_ACR: device is busy

```

This problem wasn't a huge deal until today.  I wrote a bunch of stuff to my disk, couldn't disconnect the loop device, removed key unsafely.  Usually it's fine (although makes me uneasy).  This time, some directories on my key are hosed.  I NEED to figure this out!

What is the problem??  Why won't the loop device free itself.  It works sometimes, but more often than not it doesn't let me do the 'losetup -d' command successfully.  What info can I provide that would help someone figure out this problem?

Note:  even after the key is removed, the loop device is still there and still "busy".  Thus, anytime until after this happens the first time and before I reboot that I plug my in the key, even if I don't mount the encrypted filesystem, my key is held hostage by the loop device forcing me to unsafely remove it.

-Casper

---

