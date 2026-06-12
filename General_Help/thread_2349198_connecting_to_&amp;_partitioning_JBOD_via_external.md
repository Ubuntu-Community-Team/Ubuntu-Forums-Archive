---
title: "connecting to &amp; partitioning JBOD via external SCSI port"
date: 2017-01-12
forum: General Help
---

### Post by drgrumbles2 on 2017-01-12
hello everyone, i require some advise and expertise on getting connected to a JBOD via an external SCSI port + cable.

at the moment im using an IBM X346 server rack with a JBOD loaded with 16x 1TB drives which is connected via an External SCSI port with a cable,  have attempted using Gparted which does not detect the JBOD and also tried using lsscsi, lsblk as well as fdisk -l to see if it was detectable, and dont seem to have had any success at the moment from what i could see from the output but i may be wrong.

what i am trying to do is get connected and partition/setup the JBOD for file storage, i have scoured the documentation but have not found anything that is of use at the moment.

due to the age of the system it is using Ubuntu 12.04 LTS 64 bit.

if anyone could kindly give some assistance and guidance, that would be fantastic, thank you.

---

### Post by drgrumbles2 on 2017-01-16
ok, i have fiddled around with it some more, the server box see's the device, has a HCTL number, a channel and an ID, but cannot figure out how to mount it within linux, disk utility lists it as an Hosts Controller, more specifically as an Adaptec ServeRAID controller, any help please?

---

