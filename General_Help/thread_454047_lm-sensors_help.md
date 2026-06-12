---
title: "lm-sensors help"
date: 2007-05-25
forum: General Help
---

### Post by evanrees on 2007-05-25
Hi,


I am looking to control fan speed with pwmconfig. The output of sensors is:

```
k8temp-pci-00c3
Adapter: PCI adapter

[COLOR="Red"]Core0 Temp:
             +18°C
Core1 Temp:
             +20°C[/COLOR]
it8716-isa-0290
Adapter: ISA adapter
VCore:     +1.12 V  (min =  +0.00 V, max =  +4.08 V)    
VDDR:      +1.84 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +3.31 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.95 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +12.16 V  (min =  +0.00 V, max = +16.32 V)    
in5:       +0.88 V  (min =  +0.00 V, max =  +4.08 V)   
in6:       +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:      +4.97 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.02 V
fan1:     3199 RPM  (min =    0 RPM)                    
fan2:        0 RPM  (min =    0 RPM)                   
fan3:        0 RPM  (min =    0 RPM)                   
temp1:       +30°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor   
temp2:       -53°C  (low  =  +127°C, high =  +127°C)   sensor = thermistor    
temp3:       +13°C  (low  =  +127°C, high =  +127°C)   sensor = diode   
vid:      +1.100 V
```


my problem is that when I run pwmconfig there is no option to monitor the temp at the top in red. I only have the option to monitor the three at the bottom. Is there any way I can have cpu fan speed controlled in relation to the cpu temp at the top?

Thanks.

---

### Post by bradmayne on 2007-05-26
im running a toshiba sateillite a135 s4527.  I can't get lm-sensors up and running. when i run pwmconfig this is the output:


d# pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


would someone be kind enough to walk a n00bie through this i know there's another HOW TO but thats not working.  Can someone tell me what directory the make file is in or whatever i need to do to "make" the module and insert the module?

---

### Post by fragos on 2007-05-26
Try buying this manual control [http://www.endpcnoise.com/cgi-bin/e/std/sku=fanmate2](http://www.endpcnoise.com/cgi-bin/e/std/sku=fanmate2) its inexpensive and easily installed.

---

