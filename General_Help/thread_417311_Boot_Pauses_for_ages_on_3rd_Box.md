---
title: "Boot Pauses for ages on 3rd Box"
date: 2007-04-21
forum: General Help
---

### Post by lynxus on 2007-04-21
Hi guys, Question :

When i boot, On the 3rd box it seems to wait with no disk activity for about 2 minutes. It will then after 2mins carry on and boot fairly fast 10seconds or so..


Any ideas whats causing this ?



i suppose the normal boot screen  (  name    [ok] ) thing would be good but cant see that :(


Anyone else getting thois hang ?

The network is connected so i cant see it hanging for ages waiting for an IP.



Cheers
G

---

### Post by RedSquirrel on 2007-04-21
I would check if something is failing during boot:

```
dmesg | grep -i failed
```

---

### Post by lynxus on 2007-04-21
Oh gawd,

Crist knows....


gsmart@broken-trumpet:~$ dmesg | grep -i failed
[    8.448000] PM: Resume from disk failed.
[   59.764000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[   90.432000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  121.100000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
gsmart@broken-trumpet:~$

---

### Post by lynxus on 2007-04-21
AH ha.

Thx for the heads up..

The disk / ata bit made me think..

Forgot i had a cisco pcmcia flash card in the laptop slot.

Seems to boot ok with it removed now :)

Ty :)

---

### Post by RedSquirrel on 2007-04-21
No problem. Glad you got it sorted out. :)

---

