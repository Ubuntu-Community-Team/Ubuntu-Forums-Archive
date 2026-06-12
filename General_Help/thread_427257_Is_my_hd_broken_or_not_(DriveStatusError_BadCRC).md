---
title: "Is my hd broken or not? (DriveStatusError BadCRC)"
date: 2007-04-29
forum: General Help
---

### Post by cd-r80 on 2007-04-29
Dapper stopped booting & I got these errors:
0:46 localhost kernel: [4300815.306000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
ide: failed opcode was: unknown

I booted with LiveCD & made e2fsck -cv /dev/hda7   which is my root partition:
42934 inodes used (2%)
    1617 non-contiguous inodes (3.8%)
         # of inodes with ind/dind/tind blocks: 1784/27/0
  282141 blocks used (8%)
       0 bad blocks
       0 large files

Then /dev/hda9 (/home):
Block bitmap differences:  -6468224
Fix<y>? yes
Free blocks count wrong for group #197 (32254, counted=32255).
Fix<y>? yes
2030597 blocks used (26%)
       0 bad blocks.

Then I could boot again. But no badblocks? Is My hd broken or not.
Gparted shows strange partition table. Where from those black areas came?
See attached image. What made those errors messages appear. My GF use win on same machine + hd & made hard power off but...

---

### Post by cd-r80 on 2007-04-29
One answer I found already from linuxquestions.org: Check hd cables...

---

### Post by cd-r80 on 2007-04-29
I installed smartmontools. No problems yet shown up.

---

### Post by Sladi on 2007-04-29
Use the "Ultimate Boot CD". You should probably use a diagnostic tool for your HDD brand. Otherwise use Powermax (the older version, because the newest only works with Maxtor HDDs) from Maxtor and do a low level format. You may do an extenive test too before. I did that and everything is fine now. Usually HDDs won't last long after first errors appear though.

---

