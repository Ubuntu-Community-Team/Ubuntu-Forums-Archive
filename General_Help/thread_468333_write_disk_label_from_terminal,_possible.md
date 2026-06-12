---
title: "write disk label from terminal, possible?"
date: 2007-06-08
forum: General Help
---

### Post by southernman on 2007-06-08
Please indulge me on this -

Is there a way to write a Disk Label via the terminal?

I have an old Maxtor 30gb drive, that's been out of commission for a while. The last thing I did to it was a low level format using Maxblast and since then, it's been a door stop. Booting off the Live CD, using Gparted - it can see the drive. I think, KEWL! shouldn't have thought that!

When I select the unpartioned space and select new partition, it informs me that I need to write a disk label. Ok, I let it do what it wants. A short time goes be and tells me that the drive is unwritable. dagnabbit!

I shutdown and plop in my SystemRescue CD, to run test disk on it. Testdisk can see the drive as well and tells me the structure is ok. I can't add a partition to it though.

Can anyone tell me if I am SOL, need to try using Maxblast on it again (perhaps this time, I'll get to see some fireworks at least), or how to go about manually writing a disk label on the drive?

Gawd, I know that this is showing some iggernance on my part... no need to confirm any of that for me though! Just a lending hand if possible.

P.S. I have spent most of the day googling and searching here, with no beneficial results.

Thanks,

---

### Post by CocoAUS on 2007-06-08
I'm not sure if I'm understanding exactly what the problem is, but try using tune2fs.

I believe the command would be something like tune2fs -L <label> <partition>

---

### Post by southernman on 2007-06-08
I didn't know about tune2fs until just now. Thank you, I'll have a look at it and see if it'll help fix the problem.

Which btw, the problem is not being able to make a partition on the drive at all. Gparted see's the drive correctly, but trying to create any partition tells me I need to write a disk label. When hitting ok (write the disk label), it quickly tells me it can't do such.

---

