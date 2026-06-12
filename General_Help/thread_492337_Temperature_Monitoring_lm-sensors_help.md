---
title: "Temperature Monitoring: lm-sensors help"
date: 2007-07-04
forum: General Help
---

### Post by rscott5 on 2007-07-04
Hi all,

I would like to be able to monitor the temperature of my CPU in my new computer. In my older Ubuntu machine, I installed lm-sensors from the Ubuntu Repository and followed this guide:
[HTML]http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors[/HTML]
and it worked perfectly. However, when I do that on my new machine I follow the exact same instructions yet if i run the sensors command it says:
```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```
The sensors that are found when I run sensors-detect are: i2c-i801, ds1621, and eeprom.

Does anyone know why this might not be working for me?

In case needed, I am running Ubuntu 7.04 on a Dell XPS 410, Intel Core 2 Duo 2.4GHz, 3Gb of RAM. Let me know if you need any more information.

Thanks for your help!

---

### Post by dabl on 2007-07-04
Some setting in your BIOS maybe?  Do you/did you have Windows on this machine -- did sensors show up there?

---

### Post by rscott5 on 2007-07-05
It came pre-installed with Windows, but all I did was boot it to make sure everything was working and then immediately wiped it and installed Feisty. I'll check the BIOS though.

---

### Post by rscott5 on 2007-07-05
I scoured the BIOS, but couldn't find anything. I guess the lm-sensors and my motherboard just don't support each other? Kind of a bummer, but oh well I guess.

---

