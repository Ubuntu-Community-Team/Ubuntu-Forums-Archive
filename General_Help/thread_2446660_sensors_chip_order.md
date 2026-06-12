---
title: "sensors chip order"
date: 2020-07-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-07-04
Is there a way to define a order to sensors
```

~$ sensors
drivetemp-scsi-3-0
Adapter: SCSI adapter
temp1:        +34.0°C  (low  =  +0.0°C, high = +60.0°C)
                       (crit low = -41.0°C, crit = +85.0°C)
                       (lowest = +34.0°C, highest = +34.0°C)

drivetemp-scsi-1-0
Adapter: SCSI adapter
temp1:        +38.0°C  (low  =  +0.0°C, high = +60.0°C)
                       (crit low = -41.0°C, crit = +85.0°C)
                       (lowest = +38.0°C, highest = +39.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
Vcore:       931.00 mV 
Vsoc:          1.08 V  
Tctl:         +38.5°C  
Tdie:         +38.5°C  
Tccd1:        +38.0°C  
Icore:         6.00 A  
Isoc:          7.50 A  

nvme-pci-0100
Adapter: PCI adapter
Composite:    +62.9°C  (low  = -273.1°C, high = +109.8°C)
                       (crit = +129.8°C)
Sensor 2:     +78.8°C  (low  = -273.1°C, high = -273.1°C)

drivetemp-scsi-2-0
Adapter: SCSI adapter
temp1:        +30.0°C  (lowest = +30.0°C, highest = +30.0°C)

amdgpu-pci-2700
Adapter: PCI adapter
vddgfx:      750.00 mV 
fan1:        1704 RPM  (min =    0 RPM, max = 3700 RPM)
edge:         +29.0°C  (crit = +85.0°C, hyst = -273.1°C)
power1:       30.22 W  (cap = 145.00 W)

nct6795-isa-0a20
Adapter: ISA adapter
Vcore:                        928.00 mV (min =  +0.00 V, max =  +1.74 V)
+5.00V:                         5.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:                           3.36 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:                          3.36 V  (min =  +2.98 V, max =  +3.63 V)
+12V:                          12.38 V  (min = +11.42 V, max = +12.58 V)
???:                          152.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN4:                         752.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:                           3.36 V  (min =  +2.98 V, max =  +3.63 V)
3BAT:                           3.25 V  (min =  +2.70 V, max =  +3.63 V)
CPU +1.8V:                      1.83 V  (min =  +2.04 V, max =  +2.04 V)  ALARM
???:                            0.00 V  (min =  +0.00 V, max =  +0.00 V)
VIN6:                         648.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
SOC:                            1.10 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
DIMM:                           1.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN7:                           1.51 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
PUMP Fan 1 Speed (Rear):       533 RPM  (min =    0 RPM)
CPU Fan 1 Speed:               362 RPM  (min =    0 RPM)
Chassis Fan 1 Speed (VRM):       0 RPM  (min =    0 RPM)
Chassis Fan 2 Speed (Bottom):  408 RPM  (min =    0 RPM)
Chassis Fan 3 Speed (Front):   590 RPM  (min =    0 RPM)
Chassis Fan 4 Speed (Front):   597 RPM  (min =    0 RPM)
SYSTIN:                        +35.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                        +34.0°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                       +40.0°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:                      -128.0°C    sensor = thermistor
AUXTIN2:                       +46.0°C    sensor = thermistor
AUXTIN3:                        -1.0°C    sensor = thermistor
SMBUSMASTER 0:                 +38.5°C  
PCH_CHIP_CPU_MAX_TEMP:          +0.0°C  
PCH_CHIP_TEMP:                  +0.0°C  
PCH_CPU_TEMP:                   +0.0°C  
intrusion0:                   ALARM
intrusion1:                   ALARM
beep_enable:                  disabled

```
** if anyone sees this and is wondering how i got ssd in this nvme will appear with the 5.5 kernel and the 5.6 kernel adds sata, but you have to [FONT=courier new]modprobe drivetemp[/FONT] for sata

---

### Post by kneutron on 2020-07-04
--What are you trying to accomplish?  The only way I can think of (since it's not in the man page) would be to pipe sensors output repeatedly to grep, or awk, to a temporary file; and then cat/display that file.  Or you can just grep out what matters to you.  I have a monitor script that greps sensors and uses sed to change the sensor name to something meaningful.

This is for a 2008 iMac:

```
watch -n 61 "sensors -f |/bin/egrep 'RPM|°F' |/bin/sed 's/Tp0P:/PwrSply:/;s/TA0P:/RmTemp :/;s/TC0D:/CPU0Die:/;s/TG0P:/GPUTemp:/' 2>/dev/null"
```

---

### Post by pqwoerituytrueiwoq on 2020-07-04
I was just wondering if there was a better way than doing this:
```

$ sensors k10temp-* amdgpu-* nct6795-* nvme-* drivetemp-*
k10temp-pci-00c3
Adapter: PCI adapter
Vcore:       931.00 mV 
Vsoc:          1.09 V  
Tctl:         +38.2°C  
Tdie:         +38.2°C  
Tccd1:        +37.8°C  
Icore:         6.00 A  
Isoc:          7.50 A  

amdgpu-pci-2700
Adapter: PCI adapter
vddgfx:      750.00 mV 
fan1:        1697 RPM  (min =    0 RPM, max = 3700 RPM)
edge:         +28.0°C  (crit = +85.0°C, hyst = -273.1°C)
power1:       30.11 W  (cap = 145.00 W)

nct6795-isa-0a20
Adapter: ISA adapter
Vcore:                        936.00 mV (min =  +0.00 V, max =  +1.74 V)
+5.00V:                         5.04 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:                           3.38 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:                          3.38 V  (min =  +2.98 V, max =  +3.63 V)
+12V:                          12.38 V  (min = +11.42 V, max = +12.58 V)
???:                          152.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN4:                         752.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:                           3.36 V  (min =  +2.98 V, max =  +3.63 V)
3BAT:                           3.25 V  (min =  +2.70 V, max =  +3.63 V)
CPU +1.8V:                      1.83 V  (min =  +2.04 V, max =  +2.04 V)  ALARM
???:                            0.00 V  (min =  +0.00 V, max =  +0.00 V)
VIN6:                         656.00 mV (min =  +0.00 V, max =  +0.00 V)  ALARM
SOC:                            1.10 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
DIMM:                           1.36 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
VIN7:                           1.51 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
PUMP Fan 1 Speed (Rear):       535 RPM  (min =    0 RPM)
CPU Fan 1 Speed:               357 RPM  (min =    0 RPM)
Chassis Fan 1 Speed (VRM):       0 RPM  (min =    0 RPM)
Chassis Fan 2 Speed (Bottom):  401 RPM  (min =    0 RPM)
Chassis Fan 3 Speed (Front):   585 RPM  (min =    0 RPM)
Chassis Fan 4 Speed (Front):   598 RPM  (min =    0 RPM)
SYSTIN:                        +35.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = CPU diode
CPUTIN:                        +33.0°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN0:                       +39.5°C  (high = +110.0°C, hyst = +90.0°C)  sensor = thermistor
AUXTIN1:                      -128.0°C    sensor = thermistor
AUXTIN2:                       +45.0°C    sensor = thermistor
AUXTIN3:                        -1.0°C    sensor = thermistor
SMBUSMASTER 0:                 +38.0°C  
PCH_CHIP_CPU_MAX_TEMP:          +0.0°C  
PCH_CHIP_TEMP:                  +0.0°C  
PCH_CPU_TEMP:                   +0.0°C  
intrusion0:                   ALARM
intrusion1:                   ALARM
beep_enable:                  disabled

nvme-pci-0100
Adapter: PCI adapter
Composite:    +62.9°C  (low  = -273.1°C, high = +109.8°C)
                       (crit = +129.8°C)
Sensor 2:     +78.8°C  (low  = -273.1°C, high = -273.1°C)

drivetemp-scsi-3-0
Adapter: SCSI adapter
temp1:        +34.0°C  (low  =  +0.0°C, high = +60.0°C)
                       (crit low = -41.0°C, crit = +85.0°C)
                       (lowest = +34.0°C, highest = +34.0°C)

drivetemp-scsi-1-0
Adapter: SCSI adapter
temp1:        +37.0°C  (low  =  +0.0°C, high = +60.0°C)
                       (crit low = -41.0°C, crit = +85.0°C)
                       (lowest = +37.0°C, highest = +39.0°C)

drivetemp-scsi-2-0
Adapter: SCSI adapter
temp1:        +30.0°C  (lowest = +30.0°C, highest = +30.0°C)

```

---

### Post by Yellow Pasque on 2020-07-04
Wouldn't a simple alias work well here?:
```
alias sns='sensors k10temp-* amdgpu-* nct6795-* nvme-* drivetemp-*'            #Make a new command 'sns'
sns         #Verify it works
echo "alias sns='sensors k10temp-* amdgpu-* nct6795-* nvme-* drivetemp-*'" | tee -a ~/.bashrc           #Make it permanent
source ~/.bashrc       #Reload bashrc to apply change
sns          #One more test

```
Call it a day and drink beer or iced tea or whatever.

---

### Post by dragonfly41 on 2020-07-04
Can you perhaps configure GkrellM System Monitor (popup) to your requirements?

---

### Post by pqwoerituytrueiwoq on 2020-07-04
> **Yellow Pasque said:**
> Wouldn't a simple alias work well here?:
```
alias sns='sensors k10temp-* amdgpu-* nct6795-* nvme-* drivetemp-*'            #Make a new command 'sns'
sns         #Verify it works
echo "alias sns='sensors k10temp-* amdgpu-* nct6795-* nvme-* drivetemp-*'" | tee -a ~/.bashrc           #Make it permanent
source ~/.bashrc       #Reload bashrc to apply change
sns          #One more test

```
Call it a day and drink beer or iced tea or whatever.

that is probably the best way

---

