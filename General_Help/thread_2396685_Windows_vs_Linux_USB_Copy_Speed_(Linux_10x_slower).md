---
title: "Windows vs Linux USB Copy Speed (Linux 10x slower)"
date: 2018-07-19
forum: General Help
---

### Post by garzet on 2018-07-19
I have been transfering music to my MP3 player (yes, I still use MP3 player...) and I've noticed that the process takes A LOT longer then on Windows.

I went ahead and measured the time using [SIZE=3][FONT=courier new]time [/FONT][/SIZE]on Linux and just wrist-watch for windows:
```

119 Files, 687MB total
LINUX COPY:
    garzet@GarzetRig:~$ time cp -r Music/Norther/ /media/garzet/WALKMAN/
        real 19m38.427s
        user 0m0.005s
        sys 0m1.109s
    AVG SPEED: 0.58319185059 MB/s

WINDOWS COPY:
    time  2m5s
    AVG SPEED: 5.496 MB/s

```

I have tried using [SIZE=3][FONT=courier new]rsync [/FONT][/SIZE]and *GNOME files/Nautilus*- more or less the same results.
**OS**: Ubuntu 18.4   /  Windows 10
**USB:** 2.0
**CPU: **i7-6700k @ 4.4GHz
**Other:** Dual boot, same USB port

I have seen some kernel issue back from 2008 which is supposed to be the result of slower copy speeds on Linux when compared to Windows, but don't think it is relevant anymore.
I did googling-morning and couldn't find any solution.
Are there any ways to speed this up?

---

### Post by TheFu on 2018-07-19
How is the storage mounted?   gvfs is terribly slow.

---

### Post by garzet on 2018-07-19
> **TheFu said:**
> How is the storage mounted?   gvfs is terribly slow.

Pretty sure it's GVfs since it mounts automatically. Not sure how to use any other method - I did try [SIZE=3][FONT=courier new]umount[/FONT][/SIZE] and then [SIZE=3][FONT=courier new]mount[/FONT][/SIZE] manually, but then timed copy doesn't work. Files are copied in background, but [SIZE=3][FONT=courier new]cp[/FONT][/SIZE] returns control instantly which is strange.
This is the output:
```

$ sudo time cp -r Music/Norther/ /media/garzet/TEST/
0.00user 0.10system 0:00.70elapsed 14%CPU (0avgtext+0avgdata 2788maxresident)k
208676inputs+207384outputs (0major+179minor)pagefaults 0swaps

```

---

### Post by TheFu on 2018-07-19
Please show the exact mount command used.

Proper mounts use disk cache. To flush that, use "sync" if you can't wait for that to happen automatically. When sync returns, all data is written. Sync will be called due to umount as well.

On spinning disks, you can tweak parameters using hdparm to optimize the on-board. I doubt it is helpful for flash storage devices, but I don't know.  For USB storage, always use USB3 ports even if the storage interface is only USB2. It does help, IME, unless the storage is really slow.

---

### Post by garzet on 2018-07-19
> **TheFu said:**
> Please show the exact mount command used.

Proper mounts use disk cache. To flush that, use "sync" if you can't wait for that to happen automatically. When sync returns, all data is written. Sync will be called due to umount as well.

On spinning disks, you can tweak parameters using hdparm to optimize the on-board. I doubt it is helpful for flash storage devices, but I don't know.  For USB storage, always use USB3 ports even if the storage interface is only USB2. It does help, IME, unless the storage is really slow.

It was [FONT=courier new][/FONT][SIZE=3][FONT=courier new]sudo mount /dev/sdc1 /media/garzet/TEST/[/FONT][/SIZE]

---

### Post by missmoondog on 2018-07-19
odd, i've always found my linux computers are noticeably faster transferring stuff to usb than windows.

---

### Post by TheFu on 2018-07-19
That mount will probably work.  You can check the mount options by running **mount** without options.  Every different file system has different mount options. Some options can impact performance.

Whenever I connect my portable devices via USB to a computer to transfer files, I'm always amazed at the terrible performance and  simply transfer any files well before I need them on the device (or use a Nextcloud server).

---

### Post by HermanAB on 2018-07-19
There are recurring bugs in the USB stack for certain hardware.  It sounds like you are one of the unlucky ones.  Some of the USB problems can be fixed with 'ionice'.

---

