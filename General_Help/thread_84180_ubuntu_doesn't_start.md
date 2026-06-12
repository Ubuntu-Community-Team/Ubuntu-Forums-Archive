---
title: "ubuntu doesn't start"
date: 2005-10-30
forum: General Help
---

### Post by noobgr on 2005-10-30
i have a problem. the ubuntu doesn't start. when i open my pc and i choose to start ubuntu, the moment before it asked me my username i have black screen. after 30seconds i take this message:

"i cannot start the X server (your graphical interface). it is likely that it is not set up corrently. would you like to view the X server outout t&#959; diagnose the problem?"

the last program that i install was the gkrellm.

what to do?

---

### Post by Xian on 2005-10-30
Check your X log to try and determine the cause of this problem.
At the command prompt:

```
$ nano /var/log/Xorg.0.log
```

---

### Post by noobgr on 2005-10-30
it is empty

---

### Post by noobgr on 2005-11-01
because i didn't find a sollution for the problem i did format and reinstall the ubuntu but i had the same problem again. i didn't install a program yet. i didn't install the nvidia drivers.

what to do?

---

### Post by eyebrowman92 on 2005-11-01
i had the same problem but i just reinstalled ubuntu without formatting then i upgraded to breezy using a terminal and it was fine.

---

### Post by noobgr on 2005-11-02
i take these errors:

(&#917;&#917;) Nvidia(0): Failed to initalize the Nvidia kernel module! please ensure
(&#917;&#917;) Nvidia(0): that there is a supported Nvidia GRU in the system amd
(&#917;&#917;) Nvidia(0): that the Nvidia device files have been created properly
(&#917;&#917;) Nvidia(0): please consult the Nvidia README for detailes
(&#917;&#917;) Nvidia(0): ***ABORTING***
(EE)Screen(s) found, but none have a usage configuration

fatal server error: no screens found

---

### Post by Casey on 2005-11-02
" i didn't install the nvidia drivers."

It is certainly looking for them, so you must have added a line to your xorg.conf file telling it to try to load them. 

To get a gui, just type:
```
sudo nano /etc/X11/xorg.conf
```

look for this line:
```
	Driver		"nvidia"
```

and change it to 
```
	Driver		"nv"
```

Reboot and the GUI should now start.

Go to synaptic and see if linux-restricted-modules is installed for your kernel.

---

