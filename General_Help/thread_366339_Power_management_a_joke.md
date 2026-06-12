---
title: "Power management a joke?"
date: 2007-02-20
forum: General Help
---

### Post by telovoyagarcar on 2007-02-20
Ok... there is this ¨Power management preferences¨ icon up there next to the clock and sound options. It allows me to choose what to do  when laptop lid is closed and when laptop power critical.... so i set it to hibernate when there is no more power and suspend when i close the lid.

none of them work.

searching the forum i found that i could open gconf-editor >Apps>gnome-power-manager so in the right i have action_battery_button_lid , action_battery_critical, among others...

1.st: Why are the options set different between the power management preferences panel and the configuration editor?? Shouldn´t  both places be the same when changing anything in one of them?

2nd: Why the laptop does nothing if i close the lid? I set it to suspend - hibernate - shutdown and none of them work. i close the lid and the screen just stays ON ... 
One day i was alerted that i had like 5 minutes left in the battery and i just ignored it and keep working with the peace of mind that the laptop was going to hibernate before the battery die, so i wouldn´t lose any of the work i was doing.... Guess what.... the laptop just died .... hibernation my *** .... Ubuntu is doing nothing about the battery, the options i choose or when i close the lid.

Am i stuck like that or do i have any more options to fix this?

The laptop is fine... windows does the right thing about the options i set in power management.

Thanks guys

---

### Post by maxamillion on 2007-02-20
I can't vouch for PC laptops but when I ran Xubuntu on my iBookG4 it not only averaged about 30 minutes more battery life then with OS X but it also performed all the functions that you described flawlessly .... there might be something else going on here, possibly a configuration you missed.

---

### Post by jamesjtucker on 2007-02-20
telovoyagarcar: it would be helpful to know what version of ubuntu you are running and what kernel you are using.

---

### Post by telovoyagarcar on 2007-02-20
> **jamesjtucker said:**
> telovoyagarcar: it would be helpful to know what version of ubuntu you are running and what kernel you are using.


Here: Linux ubuntu 2.6.17-11-generic 

Edgy

Thanks

---

### Post by telovoyagarcar on 2007-02-22
So no clue at all huh? :confused:

---

### Post by grogger13 on 2007-04-03
im pretty shocked about the person saying they get better battery life in ubuntu, i get about 45 minutes on ubuntu compared to 2h30min on windows. is there anything that you can do to increase it

---

### Post by KIAaze on 2007-04-03
I also have some problems configuring powersaving and lid-close features on my PC.
But I have them with windows XP and Ubuntu.

For Windows, I think it has something to do with some missing drivers since I didn't have those problems until I reinstalled Windows from the windows CD instead of the horrible "Compaq system restore CD with bunch of programs I don't want".

Under Linux, I'm guessing it has something to do with modules that are not loaded (ACPI support).
I remember having to recompile my kernel to get cpufreq to work (allows me to change the CPU frequency).
And while trying to get it to work I came across a lot of ACPI related stuff.

I'm not a linux guru, but from what I understood, if the ACPI modules are not loaded in the kernel, power-saving features don't work.

---

