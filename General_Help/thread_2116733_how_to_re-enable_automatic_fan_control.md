---
title: "how to re-enable automatic fan control?"
date: 2013-02-16
forum: General Help
---

### Post by vanagon on 2013-02-16
When you run pwmconfig, it asks you questions like:
```

hwmon2/device/pwm2 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control?

```
Suppose you answer yes to this question.  How can you reverse this decision?  I.e., how can you restore the fan to the "automatic speed control setting"?

Running pwmconfig again seems to be no help.

---

### Post by schragge on 2013-02-16
```

sudo rm /etc/fancontrol

``` then re-run *pwmconfig*.

If that doesn't help you can try to change the setting manually. What *pwmconfig* does to enable manual control is writing **1** into *hwmon2/device/pwm2_enable*. Where that file is located depends on your system. Try to *find /sys/devices -name pwm2_enable*, or look for it either in */sys/class/hwmon* or under /sys/bus/i2c/devices/*-*/. Then do
```

echo 2 | sudo tee [color=green]/sys/class/hwmon/[/color]hwmon2/device/pwm2_enable

``` Adjust the [color=green]green[/color] part of the path appropriately.

---

### Post by vanagon on 2013-02-16
> **schragge said:**
> ```

sudo rm /etc/fancontrol

``` then re-run *pwmconfig*.

If that doesn't help you can try to change the setting manually. What *pwmconfig* does to enable manual control is writing **1** into *hwmon2/device/pwm2_enable*. Where that file is located depends on your system. Try *find /sys/devices -name pwm2_enable*.

This doesn't work.  The fans are still set to automatic control after I delete the /etc/fancontrol file, and pwmconfig does not ask the question the second time I run it.

EDIT:  Just to clarify, I did find the pwmX_enable files and set them to zero, but still, running pwmconfig again doesn't result in the question about automatic control.

---

### Post by schragge on 2013-02-16
Sorry, I was wrong. **0** usually means no control (fan at full speed), **1** - manual control, **2**+ - automatic control (depending on your chipset). So, the right command looks like
```

echo 2 | sudo tee /sys/class/hwmon/hwmon2/device/pwm2_enable

```

**Values of *pwm*_enable* for some chipsets** (see [Linux kernel documentation]("http://www.kernel.org/doc/Documentation/hwmon"))
[list]
[*]Texas Instruments AMC6821: 1=open loop, 2=fan controlled by remote temperature, 3=fan controlled by combination of the on-chip temperature and remote-sensor temperature
[*]Andigilog aSC7621/aSC7621a: 0=fan off, 1=manual control, 2,3=automatic control (two modes), 255=fan on full
[*]Fintek F8000: 1=manual mode, 2=normal auto mode, 3=thermostat mode
[*]Winbond W83792D: 0=disabled, 1=manual mode, 2=Smart Fan II, 3=Thermal Cruise
[/list]

---

### Post by vanagon on 2013-02-16
Yes, this was the solution!
Thanks!

> **schragge said:**
> Sorry, I was wrong. **0** usually means no control (fan at full speed), **1** - manual control, **2**+ - automatic control (depending on your chipset). So, the right command looks like
```

echo 2 | sudo tee /sys/class/hwmon/hwmon2/device/pwm2_enable

```**Values of *pwm*_enable* for some chipsets** (see [Linux kernel documentation]("http://www.kernel.org/doc/Documentation/hwmon"))
[LIST]
[*]Texas Instruments AMC6821: 1=open loop, 2=fan controlled by remote temperature, 3=fan controlled by combination of the on-chip temperature and remote-sensor temperature
[*]Andigilog aSC7621/aSC7621a: 0=fan off, 1=manual control, 2,3=automatic control (two modes), 255=fan on full
[*]Fintek F8000: 1=manual mode, 2=normal auto mode, 3=thermostat mode
[*]Winbond W83792D: 0=disabled, 1=manual mode, 2=Smart Fan II, 3=Thermal Cruise
[/LIST]


---

