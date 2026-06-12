---
title: "Question about efibootmgr"
date: 2017-12-14
forum: General Help
---

### Post by KenF on 2017-12-14
I'm running Ubuntu 14.04.  I was trying to learn about UEFI and I ran the command "sudo efibootmgr -v".   The output was:

```
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0002,0001
Boot0000* ubuntu	HD(1,800,5f000,7d265915-71e9-4eb6-85db-20da0388a6f0)File(\EFI\ubuntu\shimx64.efi)
Boot0001* Hard Drive 	BIOS(2,0,00)..GO..NO........o.C.r.u.c.i.a.l._.C.T.1.2.0.M.5.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . .4.1.3.1.C.0.D.0.5.D.A.6........BO..NO........o.W.D.C. .W.D.1.0.E.Z.R.X.-.0.0.L.4.H.B.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.4.C.2.J.2.7.4.6.5.1........BO
Boot0002* ubuntu	HD(1,800,5f000,7d265915-71e9-4eb6-85db-20da0388a6f0)File(\EFI\Ubuntu\grubx64.efi)

```

I'm confused because it looks garbled and does not seem to match my system.  I have two disks (and SSD and a HDD) ... both are partitioned with GPT.  I expected the descriptions to say GPT ... an I'm especially confused that the Boot0001 hard drive says "BIOS" ... and the string (Crucial CT120M500SSD) matches the model of SDD that matches the Boot0000 and Boot0002 UUIDs.

Why is this output garbled???

---

