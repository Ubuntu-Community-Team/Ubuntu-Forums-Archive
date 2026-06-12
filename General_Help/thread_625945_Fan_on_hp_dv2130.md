---
title: "Fan on hp dv2130"
date: 2007-11-28
forum: General Help
---

### Post by olavjunior on 2007-11-28
I followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29")
to detect my sensors. But it only returned this:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +51°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48°C  (high =   +85°C)   
```

So the temperatures aren't very high, but my fan keeps on going (not much though, but still annoying cause they go all the time..)

Is there a way to control the fan? The guide didn't work because
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

The load is minimal, so I don't see the reason it should go all the time. The temp could be a bit higher..

---

