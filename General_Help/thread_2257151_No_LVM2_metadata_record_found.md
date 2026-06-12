---
title: "No LVM2 metadata record found"
date: 2014-12-17
forum: General Help
---

### Post by marxlv2 on 2014-12-17
Hello,

I have a question about LVM2 metadata record. Considering ouput from following commands:
[FONT=lucida console]user@host:~$ sudo pvs
  PV         VG     Fmt  Attr PSize   PFree
  /dev/dm-2  vgdata lvm2 a-     2.73t     0
  /dev/dm-3  vgdata lvm2 a-     1.82t     0
  /dev/dm-4  vgdata lvm2 a-     1.82t     0
  /dev/sda5  host-vg lvm2 a-   297.85g 16.00m
user@host:~$ sudo vgs
  VG     #PV #LV #SN Attr   VSize   VFree
  host-vg   1   2   0 wz--n- 297.85g 16.00m
  vgdata   3   1   0 wz--n-   6.37t     0
user@host:~$ sudo lvs
  LV     VG     Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root   host-vg -wi-ao 289.84g
  swap_1 host-vg -wi-ao   8.00g
  lvdata vgdata -wi-a-   6.37t
user@host:~$ sudo pvck -v /dev/dm-2
    Scanning /dev/dm-2
  Found label on /dev/dm-2, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=1044480
user@host:~$ sudo pvck -v /dev/dm-3
    Scanning /dev/dm-3
  Found label on /dev/dm-3, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=258048
    Found LVM2 metadata record at offset=7168, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=5632, size=1536, offset2=0 size2=0
user@host:~$ sudo pvck -v /dev/dm-4
    Scanning /dev/dm-4
  Found label on /dev/dm-4, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=258048
    Found LVM2 metadata record at offset=7168, size=1536, offset2=0 size2=0
    Found LVM2 metadata record at offset=5632, size=1536, offset2=0 size2=0[/FONT]
As you can see running "sudo pvck -v /dev/dm-4" and "sudo pvck -v /dev/dm-3" gives messages like "Found LVM2 metadata record at offset=", but running "sudo pvck -v /dev/dm-2" gives no message about LVM2 metadata being found. Running "sudo pvck -d -v /dev/dm-2" also provides same result as "sudo pvck -d -v /dev/dm-2".
My question is if this is behavior "as one can expect" or should something be done (repairing pv, etc)?

I am running KUbuntu 12.04 64bit with latest updates.

--
Marks.

---

