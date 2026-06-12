---
title: "i686 kernel"
date: 2006-07-06
forum: General Help
---

### Post by anubix on 2006-07-06
ubuntu is running on my toshiba tecra 8100
p3 700mhz processor
currently i'm running the i386 kernel, i'm told i would be better off with the i686 kernel, first, am i?
and seccond, how hard is it to upgrade?


pz

---

### Post by Ubuntist on 2006-07-06
I've installed the 686 kernel.  I can't say I really notice any difference, but then I haven't tried looking for it.  But it's so easy that you might as well do it.

---

### Post by anubix on 2006-07-06
ok, how?

---

### Post by keithweddell on 2006-07-06
It's in the repos.  Try searching in Synaptic for linux-686.  If you've made any changes to your boot configuration, backup /boot/grub/menu.lst before you install because it will get overwritten.

---

### Post by hda on 2006-07-06
As mentioned before, if you select 'linux-686' in Synaptic, it will install all necessary dependencies and always make sure you have the newest supportet kernel for 686 systems.

After every kernel installation GRUB's menu.lst will be automatically updated for every kernel image installed. you can also update the menu.lst by ```
sudo  update-grub
```

_hda_

---

### Post by musicinmybrain on 2006-07-06
P.S. After you have linux-686, you can remove all the packages that start with linux-386 if you choose, but don't do it until you've rebooted into the new kernel and determined everything works properly.

---

