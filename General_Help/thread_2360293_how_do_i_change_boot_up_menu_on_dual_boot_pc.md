---
title: "how do i change boot up menu on dual boot pc"
date: 2017-05-03
forum: General Help
---

### Post by Nailhac on 2017-05-03
I currently have the following configuration for booting os

ubuntu
advanced options for ubuntu
*memory test (memtest+86)
memory test (memtest+86, serial console)
windows 10 (loader) (on/dev/sdd1)

how do i change the configuration so that win 10 starts as default instead of ubuntu 16.04
thanks

---

### Post by JonPaul on 2017-05-03
sudo gedit /etc/default/grub

change line GRUB_DEFAULT=0 to GRUB_DEFAULT=4 

sudo update-grub

Next reboot should default to windows

*the numbering begins from 0 so windows will be 4 according to your list.

---

### Post by again? on 2017-05-03
You can also use the exact boot menu which will still work if your boot menu order changes.
This command will show your boot entries.
```
grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' | nl --starting-line-number=0
```

Then edit grub.
```
sudo -H gedit /etc/default/grub
```

and copy and paste in the entry you wish to be default.
Will look something like below. (enclose entry in double quotes)
> GRUB_DEFAULT="windows 10 (loader) (on/dev/sdd1)"

Update grub.
```
sudo update-grub
```

---

