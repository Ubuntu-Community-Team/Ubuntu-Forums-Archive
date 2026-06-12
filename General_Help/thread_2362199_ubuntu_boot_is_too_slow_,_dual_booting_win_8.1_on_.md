---
title: "ubuntu boot is too slow , dual booting win 8.1 on a separate hard disk"
date: 2017-05-25
forum: General Help
---

### Post by frojin on 2017-05-25
I have no clue what I am doing,
 so...here's the systemd-analyze blame
 ```
 26.810s dev-sda1.device
         22.009s apparmor.service
         21.292s apt-daily.service
         14.949s systemd-tmpfiles-setup.service
         14.921s console-setup.service
         14.570s dev-loop0.device
         14.228s dev-loop2.device
         13.996s snap-atom-3.mount
         13.568s plymouth-start.service
          8.579s NetworkManager-wait-online.service
          4.453s vmware.service
          4.121s NetworkManager.service
          3.896s winbind.service
          3.876s nmbd.service
          3.196s samba-ad-dc.service
          2.723s lightdm.service
          2.661s accounts-daemon.service
          2.439s ModemManager.service
          2.071s thermald.service
          2.014s vmware-USBArbitrator.service
          1.747s binfmt-support.service
          1.728s gpu-manager.service
          1.634s dev-loop1.device



```

and here's dmesg [https://pastebin.com/Rk8a17KS](https://pastebin.com/Rk8a17KS)

---

### Post by pruda on 2017-05-25
I have looked into your dmesg and it looks like you have faulty sdb hard drive. Run ```
sudo smartctl -a /dev/sdb
``` and maybe even perform surface test ```
sudo badblocks -v /dev/sdb
``` and post output here. If smartctl does not work, install smartmontools with ```
sudo apt install smartmontools
```.

---

### Post by frojin on 2017-05-26
sudo smartctl -a /dev/sdb```
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-78-generic] (local build)Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               /0:0:1:0
Product:              
Compliance:           SPC-5
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.



```

Because it is too big and redundant here's the last line of [COLOR=#000000][FONT=&quot]sudo badblocks -v /dev/sdb[/FONT][/COLOR]
```
Pass completed, 976762584 ,bad blocks found. (976762584/0/0 errors)


```

also worth mentioning, the windows doesn't boot anymore, gives "unexpected I/O error."

---

