---
title: "lm-sensors config file"
date: 2016-07-16
forum: General Help
---

### Post by 4kh3RAm on 2016-07-16
lm-sensors shows the wrong temp for my AMD system.

I did a search, but could not find the config file that it uses.

If I could find it, I could apply a correction to get at least a halfway accurate temp.

```
temp + 90 degrees = actual temp
```

---

### Post by DuckHook on 2016-07-16
Changes to lm-sensors is not done in its general config file (which is located at /etc/sensors3.conf) but rather, by creating and configuring a device-specific file in the directory: /etc/sensors.d/

The usual convention is to name the file after the module that lm-sensors loads for your specific device. So, in my case, I called it: /etc/sensors.d/nct6776-isa-0290 with the following content:```
# nct6776 values for Asus p9x79 pro
# Added by DuckHook 2015-12-27 to complete/ignore lm-sensors values

chip "nct6775-*" "nct6776-*"
    
    set fan1_min 600
    set fan2_min 800
    set fan3_min 3600
    ignore fan4
    ignore fan5

    label in1 "+12V"
    compute in1 @ * 12, @ / 12
    set in1_min  12 * 0.95
    set in1_max  12 * 1.1

    label in4 "+5V"
    compute in4 @ * 5, @ / 5
    set in4_min  5 * 0.95
    set in4_max  5 * 1.1

    ignore in5

    label in6 "CPU VCC"
    set in6_max  1.744

    set temp1_max  80
    set temp1_max_hyst  75

    ignore temp2
    ignore temp8
    ignore temp9
    ignore temp10

    ignore intrusion0
    ignore intrusion1
```Do not use my file or my values. You must define your own based on your own specific HW. In my case, these changes were necessary because many values were wonky after running:```
sudo sensors-detect
```...and had to be filled in with names, multipliers and ranges, or else had to be ignored. The following links might also prove useful to you:

[https://lvogdt.wordpress.com/2013/02/19/short-lm_sensors-howto/](https://lvogdt.wordpress.com/2013/02/19/short-lm_sensors-howto/)
[http://ubuntuforums.org/showthread.php?t=1675550&page=6](http://ubuntuforums.org/showthread.php?t=1675550&page=6)
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#WhydomytwoLM75sreport-48degrees](http://www.lm-sensors.org/wiki/FAQ/Chapter3#WhydomytwoLM75sreport-48degrees)
[https://github.com/groeck/nct6775](https://github.com/groeck/nct6775)

---

### Post by 4kh3RAm on 2016-07-16
This gets the temp sensors shows to within +/- 2 degrees C. :-)

# k10temp-pci-00c3
# Temp adjustment factor for amd cpu temperature chip
#
chip "k10temp-pci-00c3"
label temp1 
compute temp1 @+34,@+34

---

### Post by DuckHook on 2016-07-16
Excellent! Happy you found solution.

---

### Post by 4kh3RAm on 2016-07-16
I feel than Ubuntu is an excellent product.

Support is great and folks responding seem very happy to help out.

Thanks for all your hard work.

It is very stable with a wide variety of programs.

And it is most excellent in supporting so much hardware. :-)

Andy

---

### Post by gordintoronto on 2016-07-17
What is your CPU? I have an AMD Phenom II X2 550, and I'm confident that Sensors shows the correct CPU temperature, after installing the module suggested by sensors-detect.

---

### Post by 4kh3RAm on 2016-07-17
Model name:            AMD A8-7600 Radeon R7, 10 Compute Cores 4C+6G
Stepping:              1
CPU MHz:               3100.000
CPU max MHz:           3100.0000
CPU min MHz:           1400.0000

---

