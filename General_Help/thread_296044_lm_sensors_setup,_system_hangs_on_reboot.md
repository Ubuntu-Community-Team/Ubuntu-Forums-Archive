---
title: "lm_sensors setup, system hangs on reboot"
date: 2006-11-09
forum: General Help
---

### Post by dad311 on 2006-11-09
Im trying to setup lm_sensors on my edge machine.  

sensors-detect gives me the following info:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-nforce2
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----

If I do a modprobe manually it works great and the sensors work.  However, when I past this into my /etc/moduels my system hangs on reboot.  Anyone know how to work around this?

Thanks

---

### Post by aidanr on 2006-11-09
comment them out one by one untill you find the one that causing you trouble, start with eeprom, it didn't like the 9625 nvidia drivers for me, i don't know if it's been fixed with the 9629 drivers but it turns out i didn't need the eeprom module for my sensors to work anyway

---

### Post by dad311 on 2006-11-09
Thanks, I removed the eeprom and that fixed the problem.

---

