---
title: "Brix installation"
date: 2017-03-12
forum: General Help
---

### Post by zkab on 2017-03-12
I have installed Xubuntu 16.04.2 LTS on a Gigabyte Brix.
The Brix has a wifi module that can be removed according to their documentation - I removed it.
Installation went OK but dmesg gives me two errors - what is it or can it be ignored ?

```
rajan@fe-sovis:~$ dmesg | grep -i error
[    2.196863] intel_pmc_core: probe of 0000:00:1f.2 failed with error -22
[    2.461300] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
```

---

### Post by DuckHook on 2017-03-13
Your error messages and removal of the WIFI module don't appear to be related. The first error involves the Power Management Core. No idea what is actually generating the error. The second error is video. See this: [http://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings](http://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings)

If your box is functioning well, I don't know if I would be too concerned about those errors. According to some posts in the above link, the cure may be worse than the malady.

---

### Post by zkab on 2017-03-13
OK - thanks

---

### Post by DuckHook on 2017-03-13
If you're happy with the above, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by zkab on 2017-03-14
Ok

---

