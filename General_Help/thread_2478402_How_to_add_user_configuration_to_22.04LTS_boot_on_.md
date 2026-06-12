---
title: "How to add user configuration to 22.04LTS boot on RPi4"
date: 2022-08-25
forum: General Help
---

### Post by tc2020 on 2022-08-25
Hello,

I would like to know how to add user hardware configuration to Ubuntu 64-bit server 22.04LTS running on RPi4.

On 20.04LTS, /boot/firmware/config.txt file has 'include' statements at the end as below:

```

# The following settings are "defaults" expected to be overridden by the
# included configuration. The only reason they are included is, again, to
# support old firmwares which don't understand the "include" command.

enable_uart=1
cmdline=cmdline.txt

include syscfg.txt
include usercfg.txt
```

The syscfg.txt file has the following entries (defaults that come with the system):

```
enable_uart=1
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on
cmdline=cmdline.txt
```

and usercfg.txt (my hardware dependent config):

```
dtoverlay=i2c-gpio,bus=5,i2c_gpio_delay_us=1,i2c_gpio_sda=12,i2c_gpio_scl=13
dtoverlay=i2c-rtc,abx80x
dtoverlay=spi1-3cs
dtoverlay=enc28j60
```

Does 22.04LTS support 'include' statement, so I just use the same?. Or, do I simply append my entries above to the end of config.txt (which was not recommended in 20.04LTS)?.

Any help would be very much appreciated. Thanks.

---

### Post by Holger_Gehrke on 2022-08-25
The config.txt isn't read by Ubuntu but by the firmware of your pi. If 'include' worked on 20.04 then the firmware of your pi is new enough to understand it and it should work the same with 22.04.

Holger

---

### Post by tc2020 on 2022-08-25
I appended entries to config.txt and it works. I will try include later on and see.
Thanks for your quick reply.

---

