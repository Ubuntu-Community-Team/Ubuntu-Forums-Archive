---
title: "Case Fan Control"
date: 2014-05-22
forum: General Help
---

### Post by magikarp2 on 2014-05-22
So I have an intake, exhaust and of course CPU fan. The former two are connected via three pin headers. The exhaust always runs around 1850 RPM. Even when my computer is idle and doesn't really need it on at all (or at least on a very low RPM) while the intake always runs at around 1000 all the time. I've been trying to use fancontrol and pwmconfig to create the config file but I can't seem to get it to work. When I run pwmconfig the only fan I can see stopping is the CPU fan which I would obviously like to keep automatic. It never stops, the more troublesome, exhaust fan. Here is the output of sensors.

```
fan1:        1184 RPM  (min =    0 RPM)//*cpu
fan3:        1859 RPM  (min =    0 RPM)//*exhaust
fan5:        1192 RPM  (min =    0 RPM)//*intake
```

How can I setup fancontrol for just the exhaust and intake fans?


**I attached pwmconfig's output.
```
Testing pwm control hwmon0/device/pwm3 ...  hwmon0/device/fan1_input ... speed was 1132 now 725
    It appears that fan hwmon0/device/fan1_input
    is controlled by pwm hwmon0/device/pwm3
Would you like to generate a detailed correlation (y)? 
Note: If you had gnuplot installed, I could generate a graphical plot.
    PWM 255 FAN 601
    PWM 240 FAN 620
    PWM 225 FAN 796 (probably incorrect)
    PWM 210 FAN 942 (probably incorrect)
    PWM 195 FAN 918 (probably incorrect)
    PWM 180 FAN 874 (probably incorrect)
    PWM 165 FAN 828 (probably incorrect)
    PWM 150 FAN 783 (probably incorrect)
    PWM 135 FAN 739
    PWM 120 FAN 695
    PWM 105 FAN 640
    PWM 90 FAN 579
    PWM 75 FAN 548
    PWM 60 FAN 510
    PWM 45 FAN 466
    PWM 30 FAN 422
    PWM 28 FAN 401
    PWM 26 FAN 380
    PWM 24 FAN 372
    PWM 22 FAN 365
    PWM 20 FAN 360
    PWM 18 FAN 353
    PWM 16 FAN 356
    PWM 14 FAN 343
    PWM 12 FAN 333
    PWM 10 FAN 331
    PWM 8 FAN 335
    PWM 6 FAN 329
    PWM 4 FAN 324
    PWM 2 FAN 317
    PWM 0 FAN 294


  hwmon0/device/fan3_input ... speed was 1849 now 1849
    no correlation
  hwmon0/device/fan5_input ... speed was 1186 now 1182
    no correlation


Testing is complete.
Please verify that all fans have returned to their normal speed.


The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)?
```

I presume you need a fan controller to adjust their speed then?

---

