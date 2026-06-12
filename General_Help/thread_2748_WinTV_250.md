---
title: "WinTV 250"
date: 2004-10-31
forum: General Help
---

### Post by schaez on 2004-10-31
Has anyone gotten a Hauppauge WinTV 250 to work?

I triied to some ivtv module, but I wasn't having any luck loading the module after compiling.  It wouldn't find using modprobe and came back w/ unkown symbol using insmod.

Thanks


update:

Here's what dmesg returns:

No module found in object
ivtv: Unknown symbol i2c_bit_add_bus
ivtv: Unknown symbol lseek
ivtv: Unknown symbol read
ivtv: Unknown symbol i2c_bit_del_bus
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release
ivtv: Unknown symbol open
ivtv: Unknown symbol close
ivtv: Unknown symbol i2c_bit_add_bus
ivtv: Unknown symbol i2c_bit_del_bus
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release
ivtv: Unknown symbol i2c_bit_add_bus
ivtv: Unknown symbol i2c_bit_del_bus
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release
ivtv: Unknown symbol i2c_bit_add_bus
ivtv: Unknown symbol i2c_bit_del_bus
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release

---

