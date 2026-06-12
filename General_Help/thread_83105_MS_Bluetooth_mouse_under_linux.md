---
title: "MS Bluetooth mouse under linux?"
date: 2005-10-27
forum: General Help
---

### Post by matva on 2005-10-27
I'm wondering... is it possible to get a ms bluetooth mouse working under ubuntu? Anyone care to explain it in a newbie friendly manner?

---

### Post by aysiu on 2005-10-28
I don't know much about Bluetooth, but I think there's Bluetooth support available through some programs in Synaptic. For more info on how to use Synaptic, see the second link in my sig.

---

### Post by joebloggs on 2005-10-29
You should already have the correct Bluetooth modules installed, you just need to activate the bluez-utils mouse recognition.

Type this:
sudo cp /etc/default/blues-utils /etc/default/bluez-utils.bak
sudo gedit /etc/default/bluez-utils

Find these lines...

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=0

make the 0 into a 1 and save the file. (If you're using Breezy, you don't need the patch)

Then type:
sudo /etc/init.d/bluez-utils restart

You may need to hit the connect button on your mouse to re-sync.

*Note
If for some reason you don't have Bluez-utils installed, use the synaptic package manager to add them. (Under System, Administration)

Cheers,
Joe

---

### Post by matva on 2005-10-29
welp, i did what you said and its still not working. in kde there is a bluetooth manager app... is there such thing in gnome? Is there a way to check if bluetooth services are running?

---

