---
title: "Ubuntu 7.10 + IDE Controller CSA 649U"
date: 2008-01-27
forum: General Help
---

### Post by Jester. on 2008-01-27
Hi folks,

I installed Ubuntu 7.10 server on a Compaq Proliant DL320 G1. It has a CSA 649U Ultra IDE Controller onboard. On the primary port I connected a 320GB Maxtor harddisk and installed the server without any problem.
Last week I bought a 500GB Maxtor disk and connected the drive as master to secondary IDE port.
After this I got some problems while booting ubuntu:
```

... 
disabling IRQ 19 
hdc: dma_timer_expiry: dma status == 0x24 
hda: dma_timer_expiry: dma status == 0x24 
hdc: DMA timeout error 
hdc: DMA timeout error: status = 0x50 {DriveReadySeekComplete} 
ide: failed opcode was unknown 
hda: lost interrupt 
hdc: lost interrupt 
...

```
Ubuntu doesn't start. When I disconnect the 500GB disk, Ubuntu starts again without problems. When I reconnect the disk, starting fails.
I've got another DL320 though G2 with the same errors. Here I installed Ubuntu 8.04 and it runs without problems.
It seems to be some problems of the 7.10 kernel with this IDE controller. Because the G1 is my friend's server, I don't expect him to use an Alpha version of Ubuntu.
Any suggestions how to solve the problem on 7.10?

Jester

---

### Post by Jester. on 2008-01-30
Too bad, it seems to be that no solution is available.
goin back to windows...  :-?

---

