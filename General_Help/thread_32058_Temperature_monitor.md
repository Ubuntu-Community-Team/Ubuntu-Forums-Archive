---
title: "Temperature monitor"
date: 2005-05-05
forum: General Help
---

### Post by DutchLau on 2005-05-05
Hello Ubuntu community,

What can I use, or rather, what command/program can I use to monitor my CPU and MB temperatures? 

Thanks,

DutchLau

---

### Post by jodef on 2005-05-05
You might be looking for something like gkrellm you can install via synaptic or apt-get.

---

### Post by DutchLau on 2005-05-05
Nice program,

Thanks, but it says that "no sensors detected" although I'm sure my mobo has sensors. I can see in the Bios what the temp is, why not in Ubuntu? Any other suggestions?

DutchLau

---

### Post by jodef on 2005-05-06
Have a look at this tutorial on : [LM-sensors and gkrellm](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=265) that should be able to point you in the right direction.

---

### Post by Professor X on 2005-05-06
```
cat /proc/acpi/thermal_zone/THRM/temperature
```.  This won't work on all hardware though (your kernel needs acpi support, but the ubuntu default does so good).  There's a gdesklet that displays this with some useless eyecandy.  Here's a cool way of doing it using the underground 'watch' command:

```
watch cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by DutchLau on 2005-05-06
@ Professor X

What's this?

> 
                                                                               cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
                                                                               cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory 
                                                                               
I tried both of your suggestions but they don't really work withe me, I'm going to try that grekklm (spelling) thing so see if that works. 

Cheers though,

DutchLau

---

### Post by Professor X on 2005-05-06
> @ Professor X

What's this?

Quote:
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory


I tried both of your suggestions but they don't really work withe me, I'm going to try that grekklm (spelling) thing so see if that works.

Cheers though,

DutchLau

It probably means your motherboard isn't supported.  lm-sensors is the only other method I know of that lets you get the CPU temp.

Good luck.

---

### Post by DutchLau on 2005-05-06
I just followed Bruno's guide on that other website, but all to no avail. It says that there are no sensors built into my Mobo, when obviously there are.

I guess I'll just have to live with the sensor my Computer box has on the front of it :(

Cheers,

DutchLau

---

