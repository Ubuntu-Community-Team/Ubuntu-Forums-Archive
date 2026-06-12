---
title: "Cannot Install Wacom Driver."
date: 2014-01-20
forum: General Help
---

### Post by dyndase on 2014-01-20
I have problem to configure Wacom Tablet Driver on Xubuntu (Chromebook Acer C720) because I can't find the right Kernel for the system.

```

sudo apt-get install linux-headers-$(uname -r)Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.8.11
E: Couldn't find any package by regex 'linux-headers-3.8.11'
(saucy)XXXXXX@localhost:~/Downloads/input-wacom-0.20.0$ 

```

Please help me :<

---

### Post by ajgreeny on 2014-01-20
linux-headers-3.8.0-19 is the nearest version I can find in the repos for my 12.04 Xubuntu.  Which version are you using on the chromebook?

There is certainly no 3.8.11 kernel available anywhere as far as I'm aware.  What kernel are you really using according to the **uname -r** output.

---

### Post by payton2 on 2014-02-06
[IMG]https://www.dropbox.com/s/jpuq0dqs0t3bpsl/snapshot1.png[/IMG]This is what I got. [https://www.dropbox.com/s/jpuq0dqs0t3bpsl/snapshot1.png](https://www.dropbox.com/s/jpuq0dqs0t3bpsl/snapshot1.png)

---

