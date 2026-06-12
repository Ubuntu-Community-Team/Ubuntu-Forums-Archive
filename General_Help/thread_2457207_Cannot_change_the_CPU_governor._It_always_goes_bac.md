---
title: "Cannot change the CPU governor. It always goes back to “ondemand” after reboot"
date: 2021-01-27
forum: General Help
---

### Post by marcesdan on 2021-01-27
[COLOR=#242729][FONT=Arial]Hi! I'm running Xubuntu 20.10. I'm trying to change the CPU scaling governor to "conservative". But it always goes back to "ondemand" after reboot.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have a Ryzen 7 4800H. So, my CPU scaling driver is acpi-cpufreq. The kernel is 5.8.0-40-generic

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I tried with:[/FONT][/COLOR]
# sudo cpupower frequency-set --governor conservative

# for GOVERNOR in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; \  &#9472;&#9583;
do \
    echo "conservative" | sudo tee $GOVERNOR; \
done

# sudo cpufreq-set -c 0 -g conservative 
[COLOR=#242729][FONT=Arial]Without success in any case. That's very hot...

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Do anybody knows what happen?[/FONT][/COLOR]

---

### Post by marcesdan on 2021-01-27
Finally, I solved editing the file ```
/etc/init.d/cpufrequtils
```


And setting the variable ```
GOVERNOR="conservative"
```


Note: Maybe you need to install ```
cpufrequtils
``` first

---

