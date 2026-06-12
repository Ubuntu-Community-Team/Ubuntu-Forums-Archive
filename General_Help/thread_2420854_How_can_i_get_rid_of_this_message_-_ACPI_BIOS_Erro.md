---
title: "How can i get rid of this message - ACPI BIOS Error (bug)"
date: 2019-06-12
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2019-06-12
I keep getting these lines after i wake from sleep mode, is there a way to make them go away?
i am assuming there is no way to fix it since i can not modify my bios to fix things there were to lazy/cheap to both with
```
[46837.460664] ACPI BIOS Error (bug): Could not resolve [\_GPE._L09.D1F0], AE_NOT_FOUND (20180531/psargs-330)
[46837.460670] ACPI Error: Method parse/execution failed \_GPE._L09, AE_NOT_FOUND (20180531/psparse-516)
[46837.460674] ACPI Error: AE_NOT_FOUND, while evaluating GPE method [_L09] (20180531/evgpe-509)
```

---

### Post by dino99 on 2019-06-12
The boot process is checking its default hardware list, and return not found chip/bios feature (warning)

This discussion brings some ways to work around these warnings:
[https://superuser.com/questions/1117992/acpi-exception-ae-not-found-while-evaluating-gpe-method-floods-syslog](https://superuser.com/questions/1117992/acpi-exception-ae-not-found-while-evaluating-gpe-method-floods-syslog)

---

### Post by pqwoerituytrueiwoq on 2019-06-13
```
root@Z97Killer:/home/chad# echo "disable" > /sys/firmware/acpi/interrupts/gpe09
bash: echo: write error: Invalid argument
root@Z97Killer:/home/chad# echo "disable" > /sys/firmware/acpi/interrupts/gpe6F
bash: /sys/firmware/acpi/interrupts/gpe6F: Permission denied
```

my board has the Z97 chipset (Released Q2 of 2014)
Ubuntu 18.04 was released April 2018, it should be aware that the Z97 chipset is a thing

---

### Post by johny-pineault-4 on 2019-06-13
it could be an hardware issue ex something that can't wake up properly or a variable in the bios setting that could interupt the process

---

