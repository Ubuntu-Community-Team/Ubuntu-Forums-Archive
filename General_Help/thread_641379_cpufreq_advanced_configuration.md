---
title: "cpufreq advanced configuration"
date: 2007-12-15
forum: General Help
---

### Post by suoko on 2007-12-15
I'm using cpufreq-set to configure cpu scaling but I have two problems:

1)  available freqs are: 350 MHz, 700 MHz, 1.05 GHz, 1.40 GHz, 1.75 GHz, 2.10 GHz, 2.45 GHz, 2.80 GHz
but I'd like to limit them to  700 MHz and  2.80 GHz. How can I do it? I've only  managed to set min freq to 700 through MIN_SPEED="699982" in  /etc/init.d/cpufrequtils file 

2) I've set the ondemand option but I'd like to keep highest freq for a minimum of 5 minutes when needed otherwise it keeps going up and down continuosly causing sluggish behaviour. How can I do it?

---

### Post by suoko on 2008-01-15
I've thought that another thing would be nice:
cpufreq should go "ondemand" when I don't use the pc, while go "performance" while I use it.
It could be implemented in gnome-power-manager.

---

