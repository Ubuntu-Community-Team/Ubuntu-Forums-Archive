---
title: "How to not load an unwanted/unneeded kernel module?"
date: 2006-07-03
forum: General Help
---

### Post by bjmg on 2006-07-03
Hello!

I have a question about kernel modules. I want to unload some unwanted/unneeded modules. The best would be to not load those modules at all.
I want to remove the following modules:
ieee1394 and ohci1394 (since I don't have any firewire devices)
sony_acpi (since I don't own a Sony notebook)
tc1100_wmi (since I don't have such a device)
serio_raw (sinve I don't see any advantange in that module - for my setup)

I already know that I am able to unload all those modules using "modprobe -r module_name". But this does not save but cost some time - and also memory.

Maybe someone of you can help me - at least I hope so.

Thank you

Bernhard

---

### Post by christhemonkey on 2006-07-03
They shouldnt be loaded if you do not have those devices....

Pardon me if im wrong, but i thought the modules loaded was determined by the hardware at boot time / hardware inserted after.

---

### Post by bjmg on 2006-07-03
Hi,

thank you for your answer.
I have an firewire port but I don't use it. Therefore I don't want to waste memory and battery (Notebook) with it. The other modules are not needed in my setup but are loaded anyways - I just don't know why.
bzw. the notebook in question is a MSI S260.

Bernhard

---

### Post by christhemonkey on 2006-07-03
Fair enough.
To stop modules being loaded, add blacklist and then the module name to the end of the file /etc/modprobe.d/blacklist, on a seperate line for each module.

For example:
```
blacklist ieee1394 
blacklist ohci1394
```

And then reboot, this will prevent these modules being loaded on boot.

---

### Post by bjmg on 2006-07-03
Well, I just tried that. But the modules are loaded anyway.
I also searched for ieee1394 or ohci1394 in /etc. It seems that there is no call of "modprobe ieee1394" or "modprobe ohci1394". But I found out the there are some lines about those devices in the "udev" directory.

It seems to be harder then I thought. But it must work because I worked well on othere distributions (Mandriva 2006).

Bernhard

---

### Post by mlind on 2006-07-03
edit:

I'll try blacklisting my firewire too, see if it works.

---

### Post by bjmg on 2006-07-03
Did you had some success?

Bernhard

---

