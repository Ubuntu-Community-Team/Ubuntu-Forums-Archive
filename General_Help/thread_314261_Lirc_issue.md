---
title: "Lirc issue"
date: 2006-12-07
forum: General Help
---

### Post by xomnia on 2006-12-07
After installing and configuring lirc according to the guide here:

[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)

following the steps, except I selected new mce receiver instead of tv card -> Hauppauge, i get this error when I try to run  sudo modprobe lirc_mceusb2:

[17244032.212000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17244823.744000] lirc_mceusb2: Unknown symbol lirc_get_pdata

Any idea?

Thanks

---

### Post by xomnia on 2006-12-07
ignore the first line of the bash output, that is form and older command (i just noticed the huge time difference) so the error is:

[17244823.744000] lirc_mceusb2: Unknown symbol lirc_get_pdata

---

