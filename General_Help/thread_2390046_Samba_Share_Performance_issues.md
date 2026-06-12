---
title: "Samba Share Performance issues"
date: 2018-04-24
forum: General Help
---

### Post by mindaa on 2018-04-24
I have a remote computer running Ubuntu 17.10 with Samba version 4.6.7 running.  8 gigs of ram.  It sits basically idle and has next to nothing running on it. 


I have two external USB hard drives connected via USB 3.0.  Both are mounted automatically in fstab.  Both are then shared via Samba.  My old drive called "usb" works great with normal transfer rates.  My newer drive called "media" has performance issues.  When I try to transfer files to it, it hangs and causes network errors. It is also slow to browse in Nautilus or Windows Explorer.  Both are configured the same.  I however stream media from it without issues. 


I have swapped USB socket locations as well as swapped the USB cables themselves.  I have tried different Samba configurations and tried different sized files.  I am at a loss for what to try next.  I have searched google, stack and here and need some help.  I have pasted what I feel are the relvant commands.  Please let me know if you need anything else.


For reference:  Western Digital Technologies(/home/dylan/usb) is the old drive and Seagate(/home/dylan/media) is the new drive that isn't working perfectly. 

```

    dylan@AhDaBooj:~$ cat /etc/samba/smb.conf
    [global]
    workgroup = WORKGROUP
    server string = Samba Server %v
    netbios name = AhDaBooj
    security = user
    map to guest = bad user
    name resolve order = bcast host
    dns proxy = no
    bind interfaces only = yes
    socket options = TCP_NODELAY
    # add to the end
    [Media]
       path = /home/dylan/usb
       writable = yes
       guest ok = no
       read only = no
       browsable = yes
       create mode = 0777
       directory mode = 0777
       valid users = @dylan
    
    [NewMedia]
       path = /home/dylan/media
       writable = yes
       guest ok = no
       read only = no
       browsable = yes
       create mode = 0777
       directory mode = 0777
       valid users = @dylan
```







```

    dylan@AhDaBooj:~$ cat /etc/fstab
    # /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system>                              <mount point>                 <type>       <options>             <dump>   <pass>
    # / was on /dev/sdb1 during installation
    UUID=928365ae-4bee-4344-a2cd-0da3b7f17f3e          /                        ext4         errors=remount-ro      0         1
    
    /swapfile                                          none                     swap         sw                     0         0
    
    UUID=4E1AEA7B1AEA6007                              /home/dylan/usb          auto         auto,user,sync         0         2
    
    UUID=90C89524C8950A1C                              /home/dylan/media        auto         auto,user,sync         0         2
    
    /dev/sr0                                           /home/dylan/cdrom        iso9660      ro,noauto              0         2
```






    ```
dylan@AhDaBooj:~$ lsusb
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 009 Device 003: ID 1058:083a Western Digital Technologies, Inc.
    Bus 009 Device 002: ID 0bc2:2322 Seagate RSS LLC
    Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```








  ```
  dylan@AhDaBooj:~$ sudo lsusb -vvv |grep -i -B5 -A5 bDeviceProtocol
      bLength                18
      bDescriptorType         1
      bcdUSB               2.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0002 2.0 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ehci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               1.10
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0001 1.1 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ohci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               1.10
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0001 1.1 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ohci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               2.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0002 2.0 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ehci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               1.10
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0001 1.1 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ohci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               2.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0002 2.0 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ehci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               1.10
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         0 Full speed (or root) hub
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0001 1.1 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic ohci_hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               3.00
      bDeviceClass            0 (Defined at Interface level)
      bDeviceSubClass         0
      bDeviceProtocol         0
      bMaxPacketSize0         9
      idVendor           0x1058 Western Digital Technologies, Inc.
      idProduct          0x083a
      bcdDevice           10.65
      iManufacturer           2 Western Digital
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               3.00
      bDeviceClass            0 (Defined at Interface level)
      bDeviceSubClass         0
      bDeviceProtocol         0
      bMaxPacketSize0         9
      idVendor           0x0bc2 Seagate RSS LLC
      idProduct          0x2322
      bcdDevice            1.00
      iManufacturer           2 Seagate
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               3.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         3
      bMaxPacketSize0         9
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0003 3.0 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic xhci-hcd
    --
      bLength                18
      bDescriptorType         1
      bcdUSB               2.00
      bDeviceClass            9 Hub
      bDeviceSubClass         0 Unused
      bDeviceProtocol         1 Single TT
      bMaxPacketSize0        64
      idVendor           0x1d6b Linux Foundation
      idProduct          0x0002 2.0 root hub
      bcdDevice            4.13
      iManufacturer           3 Linux 4.13.0-38-generic xhci-hcd
```

---

### Post by Morbius1 on 2018-04-24
I don't have an answer so these are just random observations.

Since these are NTFS filesystems you might want to look at the**  Why is the driver slow? **section of this page: [https://www.tuxera.com/community/ntfs-3g-faq/](https://www.tuxera.com/community/ntfs-3g-faq/)

What prompted me to look there was your use of the option **sync **in fstab since I have never seen it used with NTFS and the link talks about that specifically.

More of an FYI since I don't think it will slow anything down much but the create mode / directory mode options in your share definitions are irrelevant since you can't change mode on an NTFS partition - well - not without remounting it with different settings.

---

### Post by mindaa on 2018-04-25
My old drive "usb" is NTFS, my new disk "media" was originally NTFS and I thought the file size limit and format may be an issue.  The new drive "media" was slow when it was formatted as NTFS. So I wiped it and formatted as ext4.  It is actually slower now.  So slow I took it out and plugged both drives into my windows laptop.  I was getting 35ish MBPS on both drives.  So the drive works.  There is something internal to linux that is going on. 

To help isolate issues I made a directory called "temp" in my home directory on my internal SSD.  I copied a TB to it from the old drive.  Then went from the "temp" dir to the new drive.  Same slow speeds.  So I have isolated the issue to this drive specifically.  

I am averaging 1.5mbps on write speeds for the new drive. 

Thanks for the heads up, I will read through that thread and see if it helps point me in the right direction.

---

### Post by HermanAB on 2018-04-25
"Seagate" -  There is your problem.

Seagate drives like to take these interminable 'power naps', which messes up the network protocols when things time out unexpectedly.  You need to somehow disable this power saving frustration.

---

### Post by mindaa on 2018-04-25
I have also attempted to use the mv command to move files from a local SSD to the Seagate usb disk.  There are no network protocols involved in this function.  I just verified with strace. I feel something else is going on

---

