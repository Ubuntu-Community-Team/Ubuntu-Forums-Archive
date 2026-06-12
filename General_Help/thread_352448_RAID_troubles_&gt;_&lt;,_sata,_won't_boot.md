---
title: "RAID troubles &gt;_&lt;, sata, won't boot"
date: 2007-02-03
forum: General Help
---

### Post by nullstring on 2007-02-03
first off, I am a linux newbie. I install dapper on my server a few months ago... and I have learned alot, but I do not know alot of things that experianced users might know

alright, I installed 6 sata HDD's, on three different controllers
a via, a promise, and a silicon image. 
two of the controllers are on my motherboard
one of them is a PCI controller (silicon image)

the drives seemed to be working, so, after looking around on how to do software RAID for a while, and so I did one of these-

sudo mdadm /dev/md0 --create --level=5 --raid-devices=6 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf


I then rebooted the computer and it was complaining about an I/O error on sdc and eventually said it would run in faulty mode (5 HDD's, one spare).
and then it gets stuck on starting Enterprise Volume Management System... and just sits there
I thought the fact that they might be running in SATAII without the controller supporting it might be a problem, so I put jumpers in, and since then I haven't seen a message like this: 
ata2: translated ATA stat/err 0x51/0c to SCI SK/ASC/ASCQ 0xb/00/00
also, happened with ata1:

btw.. I noticed ata3: disabling port on boot.. (O_o)

I am gonna let the starting enterprise volume managemnet system sit there for a while right now.. see if it gets passed w/e tf is wrong eventually..

I can get passed it if I unplug the drives btw..

hopefully you guys can help..
I am kinda freaking out over here.. I just dropped so much money on these drives..

thank you,
nullstring

---

