---
title: "fan speed on amdgpu = Invalid argument?"
date: 2023-05-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2023-05-15
[FONT=monospace][COLOR=#000000]Kernel 5.17.13-051713-generic[/COLOR]

hwmon manual
[https://www.kernel.org/doc/html/v5.0/gpu/amdgpu.html](https://www.kernel.org/doc/html/v5.0/gpu/amdgpu.html)

[/FONT]```
[FONT=monospace][COLOR=#000000]$ ls /sys/class/drm/card0/device/hwmon/hwmon1/  [/COLOR]
[COLOR=#54ffff]**device**[/COLOR][COLOR=#000000]       fan1_target  in0_input       power1_cap          pwm1         temp1_crit [/COLOR]
fan1_enable  freq1_input  in0_label       power1_cap_default  pwm1_enable  temp1_crit_hyst 
fan1_input   freq1_label  name            power1_cap_max      pwm1_max     temp1_input 
fan1_max     freq2_input  [COLOR=#5454ff]**power**[/COLOR][COLOR=#000000]           power1_cap_min      pwm1_min     temp1_label [/COLOR]
fan1_min     freq2_label  power1_average  power1_label        [COLOR=#54ffff]**subsystem**[/COLOR][COLOR=#000000]    uevent[/COLOR][/FONT]

```[FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]fan1_enable = 0
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]fan1_max = 3700[/COLOR][/FONT][FONT=monospace][COLOR=#000000]
fan1_min[/COLOR] = 0

[/FONT]```
[FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target: Invalid argument
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input: Invalid argument
[/FONT][FONT=monospace][COLOR=#000000]$ [/COLOR][/FONT][FONT=monospace][COLOR=#000000]echo 1 | sudo tee /sys/class/drm/card0/device/hwmon/hwmon1/fan1_enable[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_enable [/COLOR]
1
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target: Invalid argument 
[COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input: Invalid argument
[/FONT]
```

i know i used to be able to see the fan RPM speed, now i can only see the pwm percentage

---

### Post by MAFoElffen on 2023-05-17
> **pqwoerituytrueiwoq said:**
> [FONT=monospace][COLOR=#000000]Kernel 5.17.13-051713-generic[/COLOR]

hwmon manual
[https://www.kernel.org/doc/html/v5.0/gpu/amdgpu.html](https://www.kernel.org/doc/html/v5.0/gpu/amdgpu.html)

[/FONT]```
[FONT=monospace][COLOR=#000000]$ ls /sys/class/drm/card0/device/hwmon/hwmon1/  [/COLOR]
[COLOR=#54ffff]**device**[/COLOR][COLOR=#000000]       fan1_target  in0_input       power1_cap          pwm1         temp1_crit [/COLOR]
fan1_enable  freq1_input  in0_label       power1_cap_default  pwm1_enable  temp1_crit_hyst 
fan1_input   freq1_label  name            power1_cap_max      pwm1_max     temp1_input 
fan1_max     freq2_input  [COLOR=#5454ff]**power**[/COLOR][COLOR=#000000]           power1_cap_min      pwm1_min     temp1_label [/COLOR]
fan1_min     freq2_label  power1_average  power1_label        [COLOR=#54ffff]**subsystem**[/COLOR][COLOR=#000000]    uevent[/COLOR][/FONT]

```[FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]fan1_enable = 0
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]fan1_max = 3700[/COLOR][/FONT][FONT=monospace][COLOR=#000000]
fan1_min[/COLOR] = 0

[/FONT]```
[FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target: Invalid argument
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input: Invalid argument
[/FONT][FONT=monospace][COLOR=#000000]$ [/COLOR][/FONT][FONT=monospace][COLOR=#000000]echo 1 | sudo tee /sys/class/drm/card0/device/hwmon/hwmon1/fan1_enable[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_enable [/COLOR]
1
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_target: Invalid argument 
[COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input  [/COLOR]
cat: /sys/class/drm/card0/device/hwmon/hwmon1/fan1_input: Invalid argument
[/FONT]
```
i know i used to be able to see the fan RPM speed, now i can only see the pwm percentage
According to this:
> 
hwmon interfaces for GPU fan:

    pwm1: pulse width modulation fan level (0-255)
    pwm1_enable: pulse width modulation fan control method (0: no fan speed control, 1: manual fan speed control using pwm interface, 2: automatic fan speed control)
    pwm1_min: pulse width modulation fan control minimum level (0)
    pwm1_max: pulse width modulation fan control maximum level (255)
    fan1_min: an minimum value Unit: revolution/min (RPM)
    fan1_max: an maxmum value Unit: revolution/max (RPM)
    fan1_input: fan speed in RPM
    fan[1-*]_target: Desired fan speed Unit: revolution/min (RPM)
    fan[1-*]_enable: Enable or disable the sensors.1: Enable 0: Disable

On fan1_enable, you set to "1", which is to enable the sensor... Shouldn't you also to set pwm1_enable to 1, then set pwm1_max to 255... then read fan1_input as the actual RPM of the fan? (As a test of that)
> 
    sysfs attributes
    ----------------

    pwm[1-5] - this file stores PWM duty cycle or DC value (fan speed) in range:
           0 (lowest speed) to 255 (full)

    pwm[1-5]_enable - this file controls mode of fan/temperature control:
        * 0 Fan control disabled (fans set to maximum speed)
        * 1 [COLOR=#ff0000]Manual mode, write to pwm[0-5] any value 0-255[/COLOR]
        * 2 "Thermal Cruise" mode
        * 3 "Fan Speed Cruise" mode
        * 4 "Smart Fan III" mode (NCT6775F only)
        * 5 "Smart Fan IV" mode

    pwm[1-5]_mode - controls if output is PWM or DC level
            * 0 DC output
            * 1 PWM output


---

### Post by pqwoerituytrueiwoq on 2023-05-18
today i noticed one of my fans was not spinning, the fan that connects to the rpm sense was unplugged
```

[FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/fan1_{enable,min,max,input} [/COLOR]
0 
0 
3700 
862
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/pwm1_{enable,min,max} [/COLOR]
2 
0 
255
[/FONT][FONT=monospace][COLOR=#000000]$ cat /sys/class/drm/card0/device/hwmon/hwmon1/pwm1 [/COLOR]
54[/FONT]
```

---

### Post by MAFoElffen on 2023-05-18
So now it looks like it is working... Good job.

---

