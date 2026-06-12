---
title: "Adding device ID to SCSI driver"
date: 2019-01-29
forum: General Help
---

### Post by TGIK on 2019-01-29
What is the best way to add a device id to SCSI (HPT RAID) driver? I have a rebranded card that has a different device ID (same vender ID) I would like the HPT driver to work with this device -

here is the gist of the situation 

1) I have a rebranded HPT Raid card 2721 -> the original vendor and device ID are 1103 for HPT and 2721 - well my card is 1103 with a device id of 1e10 - I would like to add that device ID 

2) From reading around several ubuntu posts about the HPT driver- there is an issue getting it to work with kernel 4.15 - there is an ubuntu binary on HPT's website that 'supports kernel 4.15' but people have had to build the driver from source and apply a patch to make it work -- the patch always fails for me (missing 2 hunks) 

So I want to get a working HPT driver and insert  my RAID cards device ID into the driver


Thanks in advance, 

Derek

---

