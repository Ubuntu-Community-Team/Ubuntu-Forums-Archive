---
title: "Hotplug suport sata_promise driver... no restart on jank/plug disk"
date: 2007-02-01
forum: General Help
---

### Post by thor918 on 2007-02-01
reading from this page:
[http://linux-ata.org/driver-status.html#tx2](http://linux-ata.org/driver-status.html#tx2)
"Full SATA control including hotplug and PM on all."

I got promise tx4 300, and from reading the above link, it should be possible to have hotplug capabilities using this card.
question is when and how. because it does not work at my current ubuntu server system.
and even a manual command to rescan the promise bus would be greate.
Rebooting linux every time I jank a disk or input one, is a pain, espesially becase it's a vmware server and has many many OS'es that will have to shutdown too.

looking at that page again I read "This status report applies to the latest SATA driver release, found in kernels >= 2.6.18-git5 (i.e. what will be 2.6.19)."
so what does this mean? is the promise status reflecting the vanilla kernel?
if so howcome hotplug does not work in 2.6.19.2..... (I just compiled one.. so perhaps there is some kernel config I have forgot?)

Have anyone some tips so I don't have to restart on jank/plug disk??

---

### Post by glabouni on 2007-02-01
I too, have failed to have sata hotplug working under ubuntu (edgy).

---

### Post by thor918 on 2007-02-01
@all
 I can read that module libata is used..

 root@ubuntu:~# lsmod|grep -i promise
 sata_promise           13316  2
 libata                 84112  2 ata_piix,sata_promise
 scsi_mod              146184  4 sg,sd_mod,sata_promise,libata

this is from my old kernel 2.6.15.23:
 root@ubuntu:~# dmesg | grep libata
 [42949377.120000] libata version 1.20 loaded.
 [42949383.210000] [<f8a73920>] (ata_interrupt+0x0/0x150 [libata])

 root@ubuntu:~# dmesg | grep promise
 [42949377.120000] sata_promise 0000:02:0b.0: version 1.03
 [42949377.350000] scsi0 : sata_promise
 [42949377.740000] scsi1 : sata_promise
 [42949377.950000] scsi2 : sata_promise
 [42949378.340000] scsi3 : sata_promise

checked the 2.6.19.2 kernel now:
 root@ubuntu:~# uname -a
 Linux ubuntu 2.6.19.2-p4prosessor #1 SMP Wed Jan 31 17:26:36 CET 2007 i686 GNU/Linux
 root@ubuntu:~# dmesg | grep promise
 [    1.756263] sata_promise 0000:02:0b.0: version 1.04
 [    1.779276] scsi0 : sata_promise
 [    1.998982] scsi1 : sata_promise
 [    2.439048] scsi2 : sata_promise
 [    2.658653] scsi3 : sata_promise

 root@ubuntu:~# dmesg | grep libata
 [    1.754963] libata version 2.00 loaded.


Are there anyone out there with success stories?

@glabouni
what card do you use?

---

### Post by thor918 on 2007-02-02
Bump

---

### Post by thor918 on 2007-02-03
[http://linux-ata.org/driver-status.html#matrix](http://linux-ata.org/driver-status.html#matrix)
ohh. in the driverstatus.
promise driver hotplug support is set to no, hmm strange when this
page : [http://linux-ata.org/driver-status.html#tx2](http://linux-ata.org/driver-status.html#tx2)
says it suports it. maby it's not enabled yet for end users....?

anyone know of some patches that work??

---

### Post by thor918 on 2007-03-06
progress. 
bought myself one of those cards that has full support on everything according to this page:
[http://linux-ata.org/driver-status.html#matrix](http://linux-ata.org/driver-status.html#matrix)

I can confirm hotplug works! :D (if you have newest kernel offcource)
the only thing I can put my finger on at this time is that detection takes some time(aprox 10 seconds I guess).
i havent tested everything yet, but I expect everything works.

---

### Post by JFCOOL on 2007-03-11
> **thor918 said:**
> progress. 
bought myself one of those cards that has full support on everything according to this page:
[http://linux-ata.org/driver-status.html#matrix](http://linux-ata.org/driver-status.html#matrix)

I can confirm hotplug works! :D (if you have newest kernel offcource)
the only thing I can put my finger on at this time is that detection takes some time(aprox 10 seconds I guess).
i havent tested everything yet, but I expect everything works.

Could you please tell me the exact host controller you have used. I'm looking to buy one and want to get somthing that is already proven to work. Thank you!

---

### Post by thor918 on 2007-03-11
->sata_sil24	production	 yes	yes	yes	yes

but I haven't got it working 100% in my system yet. 
because of compile problems.
to get hotplug functionality you need a bleeding edge kernel.

using 2.6.19.2 the driver is working good, but bootup gets me black screen terminal.
I haven't gotten that worked out yet. other than that it seems to work good. (as I last said. I have not tested it deeply enough to say this works perfect...  since this is a vmware server, and newer kernels did not work. but I expect the new version of vmware will solve this)

---

