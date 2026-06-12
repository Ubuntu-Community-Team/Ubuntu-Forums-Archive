---
title: "iphone 6"
date: 2021-02-21
forum: General Help
---

### Post by cmcanulty on 2021-02-21
Since I upgraded to 20.04 my ipad and iphone 6 won't mount. I already installed 
libimobiledevice6 libimobiledevice-utils
and ifuse
I once got the trust dialog and said allow but they never show up in file manager at all. Before I upgraded from 18.04 all worked fine. Is there anything else to try?
I do get output with grep but can't get it to mount. It is attached by usb but grep thinks it's attached with ethernet
```

cmcanulty@Dell660s:~$ sudo dmesg | grep ipheth
[  208.517807] usbcore: registered new interface driver ipheth
[  776.423912] ipheth 1-1.4:4.2: Apple iPhone USB Ethernet device attached
[  776.497930] ipheth 1-1.4:4.2 enx2aa02b4359a5: renamed from eth0
[  789.457239] ipheth 1-1.4:4.2: Apple iPhone USB Ethernet now disconnected
[  916.578341] ipheth 1-1.4:4.2: Apple iPhone USB Ethernet device attached
[  916.621217] ipheth 1-1.4:4.2 enx2aa02b4359a5: renamed from eth0
[ 2127.642707] ipheth 1-1.4:4.2: Apple iPhone USB Ethernet now disconnected
```

---

