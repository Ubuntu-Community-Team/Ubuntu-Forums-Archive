---
title: "Crazy Temperature Readings"
date: 2008-04-27
forum: General Help
---

### Post by czechman86 on 2008-04-27
I do not whats going on here, but every time I type in sensors, i get the strangest output.

For example:
czechman86@uBox:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +6.0°C                                    
Core0 Temp:   -6.0°C                                    
Core1 Temp:   +5.0°C                                    
Core1 Temp:   -7.0°C                                    


Now I designed this computer to run cool, but -7 degrees below freezing, thats a little far fetched. My BIOS is reading temps at around 30-40. Does anyone have any ideas as to what may be going on in ubuntu? I mean -7 might be nice, but its not real. Thanks!

---

### Post by dcstar on 2008-04-27
> **czechman86 said:**
> I do not whats going on here, but every time I type in sensors, i get the strangest output.

For example:
czechman86@uBox:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +6.0°C                                    
Core0 Temp:   -6.0°C                                    
Core1 Temp:   +5.0°C                                    
Core1 Temp:   -7.0°C                                    


Now I designed this computer to run cool, but -7 degrees below freezing, thats a little far fetched. My BIOS is reading temps at around 30-40. Does anyone have any ideas as to what may be going on in ubuntu? I mean -7 might be nice, but its not real. Thanks!

You have an Athlon 64 X2 with a Brisbane core, these have a know issue with their core diode sensors.

Add 20C to the readings and they are approximately correct.

---

### Post by sloggerkhan on 2008-04-27
Yeah, I have the same issue. It's a flaw with some AMD chips. Ijust use the motherboard CPU temp sensor and ignor the internal CPU sensors.

---

### Post by czechman86 on 2008-04-27
thanks guys! that makes sense now!!!!

---

