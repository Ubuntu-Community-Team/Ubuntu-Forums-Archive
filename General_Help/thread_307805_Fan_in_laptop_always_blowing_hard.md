---
title: "Fan in laptop always blowing hard"
date: 2006-11-27
forum: General Help
---

### Post by Masterslave on 2006-11-27
Hi guys,

First of all I like the Ubuntuforums, it has helped me with several problem.

Ok my problem is this:
I've installed Ubuntu Edgy Eft on my laptop, everthing went great!
But when Ubuntu is running then my laptop fan is blowing the whole time, and it's very loud...:(
In Windows, this never happen.

When I boot up Ubuntu from GRUB and the bar is full, then the fan is blowing like crazy.
So I think when GDM and X are loaded it triggers the fan to blow like crazy.

Who has a solution for this.
Thanks.

---

### Post by leech on 2006-11-27
Sounds to me like you need the cpufreq stuff loaded.  Install a package called 'emifreq-applet'.  Then you can right click on the Gnome-panel, select Add to Panel and CpuFreq Monitor.  It was at the very bottom on my Add to Panel dialog, under Utility and has no icon.

After this you can configure it how you want, but it should allow you to either have your laptop on Automatic, Powersaving, Fixed Power, etc.  

Hope this fixes it, if not, we can dig a little deeper and see why your acpi stuff is not being loaded.

Leech

---

### Post by shin on 2006-11-27
Also check if your processor temperature is detected by acpi.
To do that:
```
acpi -V
```

If it's not, you may need to recompile kernel with some different options or custom DSDT.

---

### Post by Masterslave on 2006-11-28
@leech:
I've installed 'emifreq-applet' my degree is 29C and it is set at 'Automatic Mangagement'.
And what am I supposed to do now?

@shin:
```

patrick@komkommer:~$ acpi -V
Battery 1: charging, 57%, 00:21:47 until charged
Thermal 1: ok, 29.0 degrees C
AC Adapter 1: on-line

```

Looks good isn't it guys?

---

### Post by mike984 on 2006-11-28
Will these tools help a friend of mine who has a desktop that has a fan that never powers down during non-use?  His computer runs a lot quieter in Windows.

---

### Post by shin on 2006-11-29
Try changing some settings for emifreq-applet - just to see if anything will be different. Also check:
```
dmesg | grep -i cpu
```

to see if there are any errors for that.

Unfortunately, in my opinion you may need to restart every time you change some settings that may affect your fan. That was in my case.

---

### Post by Masterslave on 2006-11-30
```

patrick@komkommer:~$ dmesg | grep -i cpu
[17179569.184000] Initializing CPU#0
[17179571.000000] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000 00000001
[17179571.000000] CPU: After vendor identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000000 00000000 00000001
[17179571.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.000000] CPU: L2 Cache: 128K (64 bytes/line)
[17179571.000000] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000000 00000000 00000001
[17179571.540000] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 00
[17179571.684000] Brought up 1 CPUs
[17179604.528000] cpu_init done, current fid 0xa, vid 0x4


```
I've tried some settings for emifreq-applet and then reboot, but that doesn't help because when GNOME is loading it set it default at 'Automatic Management'.

I've enabled in my BIOS the 'Cool 'n Quiet' technology, which clocks the CPU down to 800HMZ and when he needs preformence then my CPU clocks to 1.8GHZ.
This technology is OS independent isn't it?

Anyone how have other suggestions?

---

