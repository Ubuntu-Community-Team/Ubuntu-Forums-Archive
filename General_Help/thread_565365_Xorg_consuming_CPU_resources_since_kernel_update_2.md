---
title: "Xorg consuming CPU resources since kernel update 2.6.15-28 to 29"
date: 2007-10-02
forum: General Help
---

### Post by JSP on 2007-10-02
Hi,

Since the last kernel update (2.6.15-28 to 29), the dvd playback on my dapper became choppy. I found out that with rev .29, Xorg was consuming the rest of the cpu ressource; causing the playback being choppy - I also have the same problem when I play back a .ogg video. (Whilst with kernel revision .28, for a video playback, Xorg consumes less than 1% of the cpu ressource). I compared dmesg on a .28 and .29 startup. The main difference is that on .29  a new section appears towards the end :
---------------------------------------------------------------------------------------------
 [17179603.524000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179603.524000] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
[17179603.524000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179603.556000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179605.208000] [fglrx] total      GART = 67108864
[17179605.208000] [fglrx] free       GART = 51118080
[17179605.208000] [fglrx] max single GART = 51118080
[17179605.208000] [fglrx] total      LFB  = 127954944
[17179605.208000] [fglrx] free       LFB  = 119762944
[17179605.208000] [fglrx] max single LFB  = 119762944
[17179605.208000] [fglrx] total      Inv  = 0
[17179605.208000] [fglrx] free       Inv  = 0
[17179605.208000] [fglrx] max single Inv  = 0
[17179605.208000] [fglrx] total      TIM  = 0
--------------------------------------------------------------------------------------------
My xorg.conf has not been recently changed. I have been using the fglrx very happily so far.
I am not too sure how I should continue to investigate this problem - for the moment I am just using the .28 kernel revision.

Thanks for any help on this.

---

