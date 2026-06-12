---
title: "Hardy - ATA / IDE hard drives recognised as SCSI?"
date: 2008-05-19
forum: General Help
---

### Post by Scruffynerf on 2008-05-19
Just a quick question from a new Hardy install..

I've 2 old IDE hard drives. Feisty recognized them as hda & hdb.,

Hardy recognized the drives as sda and sdb, and I'm experiencing poweroff issues with the hard drives only spinning down after power to the computer is turned off.

I've filed a bug report about the power issue at: [https://bugs.launchpad.net/ubuntu/+bug/231539](https://bugs.launchpad.net/ubuntu/+bug/231539)

I'm wondering if this is related. Does anyone have any ideas as to this?

Edit:

```
lsmod |grep sd_mod
```
yields :
"sd_mod                 30720  7 
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata"

From googling around, it appears that libata has a bug that doesn't park heads prior to shutting down hard drives. 

Apparently the issue is being discussed over at Gmane at [http://thread.gmane.org/gmane.linux.ide/18485](http://thread.gmane.org/gmane.linux.ide/18485), yet I haven't figured out how to apply it.

---

