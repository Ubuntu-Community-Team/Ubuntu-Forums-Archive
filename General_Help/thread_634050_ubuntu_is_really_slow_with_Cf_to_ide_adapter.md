---
title: "ubuntu is really slow with Cf to ide adapter"
date: 2007-12-07
forum: General Help
---

### Post by markp1989 on 2007-12-07
i have installed ubuntu server on to a 1gb CF card, with a CF to ide adapter, and it is way slow, it takes ages to boot up, it hangs in 2 places, on about DMA and the other is when "preparing restricted drivers"  also anything else that i do, is very slow, including apt-get, and any other thing i do that requires alot of access to the hard drive.  i think that disabling DMA would help, is there a way to disable DMA to stop it hanging on boot, and is there any other way i could speed up this machine?

---

### Post by eagleliu on 2008-04-01
Most CF to IDE adapters support DMA mode and PIO mode, all motherboard support PIO mode,but some can't support DMA mode,because their bios is old.So you should buy hight speed CF card  and confirm your mother board support DMA mode ,then booting up will be fast.


----------------------------------------------------------------------------------------
eagle 
[http://www.shopsintech.com]("http://www.shopsintech.com")

---

### Post by kerry_s on 2008-04-01
add> ide=nodma
to your boot line in /boot/grub/menu.lst

---

