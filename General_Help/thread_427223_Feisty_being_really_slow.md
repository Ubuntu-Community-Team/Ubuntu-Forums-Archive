---
title: "Feisty being really slow"
date: 2007-04-29
forum: General Help
---

### Post by super.rad on 2007-04-29
When doing certain things feisty slows down to a crawl on my computer. Music wont play properly, it takes ages to move the mouse or type anything. It seems to be doing it at random things such as copying files from one drive to another, downloading, installing, and even opening new tabs in firefox. i've looked at system monitor and most the time the cpu's running at about 10%-20% and i have rythymbox, gaim, firefox and deluge open. If anyone has any ideas on whats causing it to slow down or how to solve it that would be great. Thanks

---

### Post by super.rad on 2007-04-29
i've kept an eye on system monitor and it seems rythymbox kept jumping upto 50% cpu then going back down, i've tried using songbird and its doing the same, also firefox is using about 25-30% is this normal?
its not just these programs being slow, the whole system feels really slow and it takes a while to open programs or switch between programs.

---

### Post by super.rad on 2007-04-29
I logged into my windows partition to do a few things and when i logged back in ubuntu it was  working fine, weird as i tried resetting a few times earlier.

---

### Post by super.rad on 2007-05-01
well it's started doing it again. any ideas?

---

### Post by super.rad on 2007-05-03
anyone have any ideas? downloading and installing programs slows down the pc so much its unusable and every now and again it will do it for no reason

---

### Post by super.rad on 2007-05-04
sorry to keep posting in here myself but i've found something interesting. i looked in the system log viewer and im getting 3 messages repeated in kern.log, messages and syslog. the messages are
Kern.log
> May  4 20:25:52 jimin-ubuntu kernel: [  724.016000] hdd: dma_intr: bad DMA status (dma_stat=76)
May  4 20:25:52 jimin-ubuntu kernel: [  724.016000] hdd: dma_intr: status=0x50 { DriveReady SeekComplete }
May  4 20:25:52 jimin-ubuntu kernel: [  724.016000] ide: failed opcode was: unknown

Messages
> May  4 20:27:02 jimin-ubuntu kernel: [  794.000000] hdd: dma_intr: status=0x50 { DriveReady SeekComplete }
May  4 20:27:02 jimin-ubuntu kernel: [  794.000000] ide: failed opcode was: unknown


syslog
> May  4 20:27:52 jimin-ubuntu kernel: [  843.972000] hdd: dma_intr: bad DMA status (dma_stat=76)
May  4 20:27:52 jimin-ubuntu kernel: [  843.972000] hdd: dma_intr: status=0x50 { DriveReady SeekComplete }
May  4 20:27:52 jimin-ubuntu kernel: [  843.972000] ide: failed opcode was: unknown


can anyone tell me what these mean and how i can solve the problems?

---

### Post by super.rad on 2007-05-09
does anyone know what these errors mean? and also my cpu still constantly spikes to 100% when i do pretty much anything

---

### Post by demiurgicdaemon on 2007-08-16
I am having a similar problem.  After about 20 minutes after booting, it seems like the system is becoming really unstable.  Doing anything eats CPU.  I have already tried a number of things.  I thought that maybe it might have to do with power stepping on my core duo so I turned that off...didn't help.  I updated the kernel to 2.6.22-9, and I think it may have helped but only very slightly.  This wasn't a problem when I was running dapper even with beryl.    I hope that somebody else might have some new information or maybe a good diagnostic that I can use.  Thanks.

---

