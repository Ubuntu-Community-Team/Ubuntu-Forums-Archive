---
title: "making CPU frequency adjustment permanent"
date: 2007-02-26
forum: General Help
---

### Post by Billy McCann on 2007-02-26
Hello Everyone.  

I've been able to scale my CPU using the cpufrequtils and sysfsutils packages, along with the p4_clockmod driver. 

The frequency steps that are allowed, though, drop way too low.  I'm able to set the minimum in the terminal with 
```
sudo cpufreq-set --cpu 0 --min 2.0GHz
sudo cpufreq-set --cpu 1 --min 2.0GHz
```

But I have to redo this on every startup, though.  Is there a way to make this permanent, i.e. it'll be the same after I reboot?


Thanks. 

billy

---

### Post by energiya on 2007-02-26
Try using a startup script. That way you can control what happens on every boot.

---

### Post by Billy McCann on 2007-02-26
That's an idea, energiya.  

How would I go about doing that? :)

---

### Post by energiya on 2007-02-26
> **Billy McCann said:**
> That's an idea, energiya.  

How would I go about doing that? :)

try reading this [link]("http://www.ubuntuforums.org/showthread.php?t=364103&highlight=how+to+script+boot"). It manages another application, but you will get the idea. Just put stuff in rc.local to suit your needs.
You could also put the command to start when Gnome starts (but I use XFCE so I couldn't be of much use).

---

### Post by Billy McCann on 2007-02-26
> **energiya said:**
> try reading this [link]("http://www.ubuntuforums.org/showthread.php?t=364103&highlight=how+to+script+boot"). It manages another application, but you will get the idea. Just put stuff in rc.local to suit your needs.
You could also put the command to start when Gnome starts (but I use XFCE so I couldn't be of much use).
I'll try that and see how it works.  

thank you.

---

### Post by Billy McCann on 2007-02-26
Worked!  

Thanks a bazillion, energiya.  

As a note to others who might use this, I didn't place a "sudo" before the commands, as I would in the terminal.

---

### Post by energiya on 2007-02-26
> **Billy McCann said:**
> 
Thanks a bazillion, energiya.  


Glad to help !

---

