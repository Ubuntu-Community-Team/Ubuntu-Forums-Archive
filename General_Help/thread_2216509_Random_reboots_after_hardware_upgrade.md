---
title: "Random reboots after hardware upgrade"
date: 2014-04-12
forum: General Help
---

### Post by fatt-o on 2014-04-12
I am running Ubuntu 12.04 and recently upgraded my motherboard, CPU and memory. I am having an issue with random reboots and have assumed it's related to the new hardware. When the reboot occurs, I do get quite a bit of info in the kern.log and dmesg. Can someone help me decipher what's in the log to determine what the cause of the reboot is?

[http://pastebin.com/XYHznxw9](http://pastebin.com/XYHznxw9)

Thanks,
Matt

---

### Post by kwasek2 on 2014-04-12
Cpu can have too big temp and reboot but there should be some message. I bet it's ram problem. Can you tell what type, freq, and size of ram blocks you have?(in order)

---

### Post by fatt-o on 2014-04-12
RAM is 1 DIMM - Adata 8GB DDR3 1600 - Not sure how to tell size of blocks

I don't think it's a CPU temp issue. I am not actively using the computer when it reboots. This is the current output of sensors:
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +105.0°C)
temp2:        +29.8°C  (crit = +105.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +36.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:         +36.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:         +33.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:         +35.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:         +35.0°C  (high = +80.0°C, crit = +100.0°C)

---

### Post by kwasek2 on 2014-04-12
1018 line on log to 1041 and lines on end shows some errors, so it's software issue i guess but i don't know unix systems well.

---

