---
title: "Temp sensor on godavari chipset"
date: 2015-08-22
forum: General Help
---

### Post by XBNCPRk on 2015-08-22
After finally getting fed up with the AMD driver debacle after 12.04, I rebuilt my HTPC a few months ago with a new mobo and Godavari chip (specifically an Asrock FM2A88M Extreme4+ paired with an AMD A10-7870K). Love the way it runs but have been unable to get any type of temp sensor to work under 14.04. In the meantime Ive had to rely on a suite of hardwired sensor probes in various places in the case to guesstimate a relative temp. 

The specs from AMD specifically state there is a temp sensor built into the chip (we'll leave the topic of its accuracy to another date), but I cant get anything like lm-sensors, psensor, etc to read and/or display temps.

Anyone have any suggestions or success with a similar setup?

---

### Post by pqwoerituytrueiwoq on 2015-08-22
when using the priopatary gpu drivers you have to get the sensor data from the vender's software
[http://askubuntu.com/questions/132433/how-can-i-see-the-gpu-temperture-of-my-ati-graphics-card](http://askubuntu.com/questions/132433/how-can-i-see-the-gpu-temperture-of-my-ati-graphics-card)

---

### Post by XBNCPRk on 2015-08-22
I wasnt aware that that applied for APUs as well. Any idea if that will display the cpu core temps as well, or just that of the gpu cores?

---

### Post by pqwoerituytrueiwoq on 2015-08-22
sensors should get the cpu if not you my need to enable some special driver like i did to get fan speeds on my z97 board

---

### Post by XBNCPRk on 2015-08-22
So, after aticonfg --inital, and then schlepping upstairs to do it in person rather than by terminal (its been one of those days), aticonfig --odgt gives me a readout that says 'Default Adapter - AMD Radeon(TM) R7 Graphics     Sensor 0: Temperature - 0.00 C' . 

Thats odd, I think to myself, I'll try it again.. 'Default Adapter - AMD Radeon(TM) R7 Graphics     Sensor 0: Temperature - 4294965.00 C' 

So, glad that it identified the sensor on the gpu side of the card (though lm-sensors doesnt pick it up still) but either theres a flaw to this, or my gpu is capable of both stopping all atomic motion, as well as being hot enough to spontaneously cause fusion... :-/ Ive looked through the asrock site to make sure I didnt miss anything there last time I checked and I see nothing in the way of *nix driver packages for sensors or other.   

Sensors for what its worth, now reads a temp from k10temp-pci-00c3 that fluctuates wildly between 0.0c and ~14c within the span of a second or two...

Any other thoughts or ideas?



*sigh*
This is what happens kids when you skip sleeping the night before. Since I was working from downstairs by a putty terminal, I had neglected to restart the system since installing the sensor suites. After doing so, sensors returns what appears to be all the correct values for temps and voltages... Ill keep an eye on it to make sure whichever step fixed it persists, and mark this thread as solved. Thanks for the guidance ladies and gents! :D

---

### Post by Yellow Pasque on 2015-08-22
What kernel are you using? If you're still using the original Trusty 3.13.x kernel, you may need to build the k10temp module as Kaveri support (which Godavari is based on) was not added until kernel 3.14 [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)
```
uname -a
```

If you're using a newer kernel , maybe you can try manually loading the k10temp module:
```
sudo modprobe -v k10temp
sensors
```

---

### Post by Yellow Pasque on 2015-08-22
You were typing while I was. How dare you!
Seriously though, k10temp is known to report inaccurate temps on this CPU (like 0C) when it's cool/idle. At least it works properly when the CPU gets warmer...

---

