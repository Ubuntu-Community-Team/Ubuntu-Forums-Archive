---
title: "Can We Determine CPU Temp in Ubuntu?"
date: 2014-12-18
forum: General Help
---

### Post by Rick St. George on 2014-12-18
Looking for a way to determine CPU Core temp in Ubuntu, running v14+ on AMD FX8320 CPU.

Without shutting down and going into BIOS, is there a way or some software to find this critical information?

Just asking ...
Thanks!
Rick

---

### Post by nerdtron on 2014-12-18
Hmm. I remember before installing "sudo apt-get install lm-sensors".
Then running the command "sensors" on the terminal.

---

### Post by QIII on 2014-12-18
You can use lm-sensors, indeed.

BUT:  the temperature reported by AMD is not an actual temperature, but some sort of arbitrary figure in degrees relative to the max temperature at which the HSF needs to run at full speed to keep from burning up the processor.

In effect, the temperature reported is lower than the actual physical temperature and can be wildly inaccurate.

---

### Post by Rick St. George on 2014-12-18
Hmmm, this is what I get when attempting to retrieve.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lm-sensors is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lm-sensors' has no installation candidate

```

Seems it is no longer available. Just as well ... I don't want arbitrary numbers.
So  I guess the answer is .... NO !

Thanks
Rick

---

### Post by CantankRus on 2014-12-18
Check you have the universe repo enabled in software sources.

---

### Post by Rick St. George on 2014-12-18
OK, downloaded and ran "sensors", received this readout.

```

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       57.37 W  (crit = 125.02 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +23.4°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)


```

Does this look right?  and do I have to open Terminal and run "sensors" to see this info?
And this info is not correct - Right?

Curious,
Rick

---

### Post by QIII on 2014-12-18
The reading under k10temp is your CPU.  That is the same value you would see in BIOS, or perhaps a degree or two different because of the load just running your OS puts on the processor.  It's the same value you would see in Windows.

Room temperature is roughly 20 degrees Celsius.  Your reading is a few degrees higher than that.  This is the arbitrariness at play.  Sometimes people get readings that are sub-ambient, which is impossible without liquid nitrogen or a phase change cooler.

The actual physical temperature is likely 6 to 10 degrees higher than that.  When I add the k10temp readout to my conky, I add 10 degrees. I run a Noctua NH-D14 cooler on mine and I see sub-ambient temperatures at idle otherwise.  It is still useful as a relative indicator.

---

### Post by CantankRus on 2014-12-18
I can't see it now but I thought I saw ubuntu-studio in the thread title.
If you are using ubuntu studio which I think now uses the xfce DE, you can install **xfce4-sensors-plugin** (uses lm-sensors)
and then add this applet to the panel.

---

### Post by Yellow Pasque on 2014-12-19
> **QIII said:**
> The actual physical temperature is likely 6 to 10 degrees higher than that.
Yeah, that's been my experience on my Phenom II. I have another sensor readout through ACPI, which is usually 5-10 degrees higher than the k10temp readout.

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +30.0°C  (crit = +65.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +21.6°C  (high = +70.0°C)   (crit = +90.0°C, hyst = +88.0°C)
```

> That is the same value you would see in BIOS, or perhaps a degree or two different because of the load just running your OS puts on the processor.

It's going to be lower than the BIOS because of undervolting/clocking at idle (i.e. "Cool'n'Quiet"), unless the CPU is under heavy load.

---

