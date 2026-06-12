---
title: "fancontrol in lm-sensors"
date: 2005-04-20
forum: General Help
---

### Post by garfield on 2005-04-20
Hi,
I have just install lm-sensors [here](http://ubuntuforums.org/showthread.php?t=2780) everything works fine, but I cant run fancontrol. I get error that fancontrol is not configured, but when I try to conf them using sudo pwmconfig i get:
[INDENT]This program will search your sensors for pulse width modulation (pwm) controls, and test each one to see if it controls a fan on your motherboard. Note that many motherboards do not have pwm circuitry installed, even if your sensor chip supports pwm.  We will attempt to briefly stop each fan using the pwm controls. The program will attempt to restore each fan to full speed after testing. However, it is ** very important ** that you physically verify that the fans have been to full speed after the program has completed.  /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed[/INDENT]

What should I do? Everything works fine under warty. Sth missing? Help!  ](*,) 

btw Sorry for bad english :(

---

### Post by pfp on 2005-05-23
[QUOTE=garfield]Hi,
I have just install lm-sensors [here](http://ubuntuforums.org/showthread.php?t=2780) everything works fine, but I cant run fancontrol. I get error that fancontrol is not configured, but when I try to conf them using sudo pwmconfig i get:

[INDENT] ....
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed[/INDENT]

What should I do? Everything works fine under warty. Sth missing? Help!  ](*,) ([/QUOTE]
Same here. I setup lm-sensors and fancontrol under warty. After upgrading to hoary, I can still read data (eg. with 'xsensors'), but fancontrol gives exactly the same error message. This is quite annoying since I have to sleep next to that thing!  :roll: 

I'll test with warty's kernel (2.6.8\) soon; currently running 2.6.10-5-k7.

Edit: Confirmed: under kernel 2.6.8.1-3-k7, fancontrol from lm-sensors 2.8.8-7ubuntu2 works. Under 2.6.10-5-k7, it doesn't.

From /usr/share/doc/linux-image-2.6.10-5-k7/changelog.Debian.gz:
```

    - [SECURITY] Fix a very hard to exploit buffer overflow in the i2c-viapro
      driver (Andres Salomon):
      . Add patch stolen-from-head_119-i2c_viapro_i2cdump_overflow.dpatch.

```

FYI, here's the relevant from /etc/modules
```
# From sensors-detect:
#  - I2C adapter drivers
i2c-viapro
i2c-isa
#  - I2C chip drivers
eeprom
w83627hf

```


BTW Garfield, what motherboard are you using? This is MSI K7T 266 Pro2, with VIA KT266 chips obviously.

---

