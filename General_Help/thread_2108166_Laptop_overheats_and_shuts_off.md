---
title: "Laptop overheats and shuts off"
date: 2013-01-23
forum: General Help
---

### Post by cclloyd9785 on 2013-01-23
My laptop keeps shutting off randomly after about 10-20 minutes of usage.  I suspect it's from overheating because the fan area seems very hot and the fan not as loud as windows.  How can I up the fan speed so it doesn't keep overheating.

---

### Post by fdrake on 2013-01-23
> **cclloyd9785 said:**
> My laptop keeps shutting off randomly after about 10-20 minutes of usage.  I suspect it's from overheating because the fan area seems very hot and the fan not as loud as windows.  How can I up the fan speed so it doesn't keep overheating.

check the bios settings. Also what kind of pc do you have ? model brand?

also install sensors and post its output and the output of dmesg:
```

sudo apt-get install lm-sensors
sensors
dmesg

```

also try a live cd and see if you can work with it for more then 30min/1 hour.

---

### Post by elgordodude on 2013-01-23
This would probably be best handled from the bios, for example switch auto to on

Also you might want to consider a good cleaning, especially if you smoke, have a cat, or the laptop is just old. Generally you remove the keyboard and blast the fan area out with compressed air. Instructions vary by laptop...

---

### Post by tgalati4 on 2013-01-23
If the above doesn't work, then open it up and remove the heat sink and replace the heat paste.  Look for a disassembly video on youtube for your laptop model.

---

### Post by sidzen on 2013-01-23
+1 check BIOS 

and look into a [*laptop cooler*]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834994787")

---

