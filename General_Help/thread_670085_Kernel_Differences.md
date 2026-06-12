---
title: "Kernel Differences?"
date: 2008-01-17
forum: General Help
---

### Post by halw on 2008-01-17
Have an old Toshiba laptop running Edgy (upgraded from Dapper). I switched pcmcia wireless cards and now have a d-link dwl-g680 card in system.

When trying to boot using the 2.6.17-12-386 kernel the card will not function due to irq11 being disabled during boot. When I use the 2.6.15-29-386 kernel the card is brought up during boot and works perfectly fine.

Obviously something has changed between kernel versions but, what & why?

FYI, when using the ...17-12-386 kernel a boot message says to use "irqpoll" as a boot parameter. However, when irqpoll is used I get a "soft boot failure" and the system does not come up.

System specs: Toshiba Satellite 2545xcdt w/AMD K6-3d cpu 333MHz, 192 MB memory, 30 GB hd, cdr drive.

---

### Post by halw on 2008-01-17
I found a [link]("http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html") that explains, at least partially, my issues between the kerenels mentioned in the OP.

---

