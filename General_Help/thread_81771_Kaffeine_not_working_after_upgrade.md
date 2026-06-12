---
title: "Kaffeine not working after upgrade"
date: 2005-10-25
forum: General Help
---

### Post by pepster on 2005-10-25
I upgraded to breezy. I am not enjoying the experience.

Kaffeine was working before the upgrade. Now it gives me 

'Loading of player part 'gstreamer_part' failed.'
Details: gstreamer_part.desktop not found in search path.

I searched on the internet. I found two others with the same problem - they suggested deleting kaffeinerc and downloading the gstreamer plugins.

I did both to no effect. I tried to reconfigure the packages. (I can't remove kaffeine because (horror) kubuntu-desktop depends on it).

Can someone help????

---

### Post by mostwanted on 2005-10-25
You can easily remove packages that kubuntu-desktop depends on. Kubuntu desktop is just a meta package for easyily installing a full Kubuntu system, you don't *have* to have every single app installed for it to work.

---

### Post by pepster on 2005-10-25
As expected, reinstalltion did not help.

I see this message as well,

kaffeine: WizardDialog: cp /usr/share/applnk/Multimedia/kaffeine.desktop /home/joseph/Desktop/kaffeine.desktop
cp: cannot stat `/usr/share/applnk/Multimedia/kaffeine.desktop': No such file or directory

---

### Post by daller on 2005-10-26
Install "kaffeine-xine"

...and then choose it under "Settings -> Engine -> Kaffeine"

Gstreamer is GREAT! - just not finished yet! (For audio, it rocks!)

---

### Post by pepster on 2005-10-27
I have kaffeine-xine installed. always has. But how can I select another engine when kaffeine fails to start up!

-Joseph

---

### Post by daller on 2005-10-27
[QUOTE=pepster]I have kaffeine-xine installed. always has. But how can I select another engine when kaffeine fails to start up!

-Joseph[/QUOTE]

Have you tried opening kaffeine from the console? (without a file to open)

What is the output?

---

