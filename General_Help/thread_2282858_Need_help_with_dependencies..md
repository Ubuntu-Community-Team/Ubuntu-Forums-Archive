---
title: "Need help with dependencies."
date: 2015-06-17
forum: General Help
---

### Post by dtree46 on 2015-06-17
Trying to install software using synaptic and getting dependency errors.

Did 'sudo apt-get update', did not help.

How is this solved?

---

### Post by slickymaster on 2015-06-17
Can you please post back here in the thread, [using code tags]("http://www.google.com/url?q=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2171721%26p%3D12776168%26viewfull%3D1%23post12776168&sa=D&sntz=1&usg=AFQjCNEl9aLbIoHVXZYLQvugZhl0WwWGFg") for the effect, the output you get when you run in a terminal window```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ajgreeny on 2015-06-17
I am not certain about this but I always use the Reload button in synaptic.  I have no reason to think that it is necessary if I have already run sudo apt-get update, but I am aware that synaptic seems to act differently sometimes if I don't Reload; no idea why but it is a safeguard anyway.

For more help tell us what package you are trying to install, what version of Ubuntu you are using, and exactly what the dependency problems and errors are.

---

### Post by Dennis N on 2015-06-17
It is certainly possible that Synaptic cannot install some software for the simple reason that it cannot locate the required dependencies using the available sources. Is the package in Synaptic's list of available packages? (Set **Origin** to **All** in the filters). Is it an older version, or newer version than listed? It must be listed there or it's a no-go from the start. Can you tell us what the package is?

---

