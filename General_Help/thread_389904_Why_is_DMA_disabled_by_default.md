---
title: "Why is DMA disabled by default"
date: 2007-03-21
forum: General Help
---

### Post by umattu on 2007-03-21
I was just curious why ubuntu has DMA disabled by default. From what I have learned, DMA is a wonderful thing. I know ubuntu is even more wonderful, and figured that there must be a reason for it. I am by no way questioning the decisions of the developers, I am just curious for my own self.

---

### Post by Outrunner on 2007-03-21
> Warning: Enabling DMA can be dangerous in some cases. Usually issues are directly related to faulty hardware, poorly written drivers, or using settings that are unsupported by your system.

I found that by searching for ubuntu + dma on google. Seems to be a pretty good reason. Other than that, I don't know.

---

### Post by anaconda on 2007-03-21
I think that DMA was disabled in Dapper (6.06), but no longer in Edgy (6.10) .. i might be mistaken, but I dont think I have needed to enble DMA in Edgy or Feisty. they both have it enabled from the beginning..

---

### Post by mcduck on 2007-03-21
DMA is only disabled if the installer doesn't detect that your hardware can support it. So it's alway a case of badly supported hardware. If your hardware has good Linux drivers DMA works, and has been working in every Ubuntu version.

So in Anaconda's case Edgy probably had better support for the hardware than Dapper had and therefore DMA was enabled in Edgy while it wasn't in Dapper. For me it's been working on all my drives since the first Ubuntu version I've used (4.10).

---

### Post by umattu on 2007-03-21
well its seems that my assumption, that ubuntu defaults with DMA off was a bit off. This does make sense. I knew there had to be a reason! Thanks for sharing..

---

