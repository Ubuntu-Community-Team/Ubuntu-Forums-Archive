---
title: "Capture with grep only numbers between the following rule"
date: 2016-09-10
forum: General Help
---

### Post by sed_faster on 2016-09-10
hello,

I need pick up only this value "137216" from this output
```

Disk 2016-05-27-raspbian-jessie.img: 3,8 GiB, 4019191808 bytes, 7849984 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x14c20151

Device                          Boot  Start     End Sectors  Size Id Type
2016-05-27-raspbian-jessie.img1        8192  137215  129024   63M  c W95 FAT32 (LBA)
2016-05-27-raspbian-jessie.img2      137216 7849983 7712768  3,7G 83 Linux

```

I use this command "fdisk -l 2016-05-27-raspbian-jessie.img | grep img2", but I receive entire line: 2016-05-27-raspbian-jessie.img2      137216 7849983 7712768  3,7G 83 Linux

How can I create the following rule: grep all numbers between img2 and second block numbers, in this case "7849983"?
Thanks

---

### Post by &amp;KyT$0P# on 2016-09-10
Does this do what you're looking for?
```
fdisk -l 2016-05-27-raspbian-jessie.img | grep -o -i -P 'img2\s+[0-9]+[^0-9]' | sed -r -e 's/img2 +//g'
```

---

### Post by steeldriver on 2016-09-10
FYI it's often easier and more natural to do this kind of thing with `awk` e.g.

```

fdisk -l 2016-05-27-raspbian-jessie.img | awk '/img2/ {print $2}'

```

---

### Post by sed_faster on 2016-09-11
Hello,

Every answers works, thanks folks! :)
I share with you my script, if you have any suggestion be sure to communicate: [https://github.com/EdgarOliveira/scriptlinux/blob/master/qemu_choose_vm.sh](https://github.com/EdgarOliveira/scriptlinux/blob/master/qemu_choose_vm.sh)

---

### Post by &amp;KyT$0P# on 2016-09-11
You're welcome! :KS

---

