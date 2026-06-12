---
title: "Getting fan sensors to work"
date: 2013-03-06
forum: General Help
---

### Post by Ryaniskira on 2013-03-06
I have Gnome 3 and I installed the sys moniter addon and I noticed I can moniter the RPM of my system fans. I oppened the config to set that up but is said i needed to install lm-sensors. well I installed it via terminal:
sudo apt-get install lm-sensors
and It installed succesfully but the sys moniter add-on config still asks me to install lm-sensors and I just installed it.
I included a screenshot of a successful install and the config dialog.

---

### Post by dcstar on 2013-03-07
> **Ryaniskira said:**
> I have Gnome 3 and I installed the sys moniter addon and I noticed I can moniter the RPM of my system fans. I oppened the config to set that up but is said i needed to install lm-sensors. well I installed it via terminal:
sudo apt-get install lm-sensors
and It installed succesfully but the sys moniter add-on config still asks me to install lm-sensors and I just installed it.
I included a screenshot of a successful install and the config dialog.

Did you then run sensors-detect?

---

### Post by Ryaniskira on 2013-03-08
will i have to do the Modprobe command? I did the comand then I had to do another one and it didnt work the i put Sudo in and this occured (2nd pic)

---

### Post by dcstar on 2013-03-08
> **Ryaniskira said:**
> will i have to do the Modprobe command?

Please tell us if it is now working or not.

---

### Post by Ryaniskira on 2013-03-08
It is not. After I entered the 2nd command 
sudo service module-init-tools start

It said Stop/waiting

I turned off the addon then turned it back on it still asks me to install LM-sensors

---

