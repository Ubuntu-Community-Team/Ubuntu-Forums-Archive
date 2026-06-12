---
title: "cpufreq ondemand up_threshold"
date: 2007-05-04
forum: General Help
---

### Post by GoalieCa on 2007-05-04
I have this nasty nagging problem that i can't seem to troubleshoot.

i am using the ondemand cpufreq governor. It works great but I feel the up_threshold is too low (currently being at 31). Despite my best googling and attempts to hunt through init / conf scripts i have not found out where it gets set. Also an attempt to sudo echo 60 > $path/up_threshold receives a dreaded permission denied. 

Any help is appreciated!

---

### Post by moles on 2007-08-14
The 'permission denied' is because the command is run as root but the output redirection is carried out using your user.
To make it work you need to run the whole line using sudo. This can be done for example by doing this:

```
sudo bash -c  "echo 60 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold"
```

From what I can tell, no startup scripts set this parameter, but Ubuntu uses the default value.
Does anyone know a good way to set this parameter at boot so you don't need to reset it manually?

---

### Post by gmatht on 2008-02-03
Alternatively, you can do 
```
echo 60 | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
```

---

