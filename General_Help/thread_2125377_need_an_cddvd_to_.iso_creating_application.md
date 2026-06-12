---
title: "need an cd/dvd to .iso creating application"
date: 2013-03-13
forum: General Help
---

### Post by Heeter on 2013-03-13
Hi all,

What would be a good application for creating and iso file from a physical cd or dvd? This s for application cd's and dvd's, not movies or music.

Thanks

Heeter

---

### Post by SeijiSensei on 2013-03-13
K3b has that option.

I think you can actually do this with dd.  If the DVD is mounted as /dev/sr0, try "dd if=/dev/sr0 of=/path/to/file.iso" and see if that works.

---

### Post by Heeter on 2013-03-13
Thanks, SeijiSensei

Will be using k3b


Thanks again

Heeter

---

### Post by montgomeryj on 2013-03-14
dd does work and it does do what you are asking.  The down side is that with it being a command line tool you have little to no feedback on how much longer the process had to go.  If you just let it run you'll be fine, but make sure that you don't close that terminal window or you'll have to start the process all over again.

---

