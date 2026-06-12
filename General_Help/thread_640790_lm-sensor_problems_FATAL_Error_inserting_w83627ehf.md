---
title: "lm-sensor problems: FATAL: Error inserting w83627ehf"
date: 2007-12-14
forum: General Help
---

### Post by Chris Murphy on 2007-12-14
Hi,

I'm new to the forums but not to linux.

I'm running mint 3.1(based on fiesty) on a core2 duo e6550, asus p5k board, 2 gigs ram, 8500gt, etc.  My chipset (ICH9) is listed as supported on the lm-sensors site

I'm trying to get lm-sensors to work but am having a problem, I've searched around but can't come up with a solution.  

sensors-detect runs fine, and outputs:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom
w83627ehf
#----cut here----

I've modified my /etc/modules to contain the appropriate drivers.  
Thats all gone off without a hitch, the problem is when i try to load them.  Using sudo modprobe i can load i2c-i801 and eeprom, but w83627ehf yields this error:

FATAL: Error inserting w83627ehf (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device

After that trying to run sensors gives:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

I'm sure this is something simple, to me it seems like the driver is missing?  I just don't know how to correct this problem.  Thank you for any help you can give me!

---

### Post by linuxwizard on 2007-12-14
Did you reboot your computer ?

---

### Post by Chris Murphy on 2007-12-14
Yes I did, after getting the error, made no difference.  My computer is now sticking partway through startup as well, unfortunately  there is no output as to what process it is starting like there where on older linux distro's so i have no idea what is hanging it up, I'm assuming something related to lm-sensors as its the only change i've made.

---

### Post by Chris Murphy on 2007-12-14
I just found a bug report (#90265) about people with ICH8 based boards upgrading to Kernel version 2.6.21 or higher fixing the problem.  Anyone know if this would work with ICH9 boards?

---

