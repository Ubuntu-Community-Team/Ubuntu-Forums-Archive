---
title: "hardware info crashes!!!???"
date: 2008-05-21
forum: General Help
---

### Post by Ashrael on 2008-05-21
I tried opening hardware information in the system>preferences menu, it crashes right after opening... so tried starting it from cli and got:

hal-device-manager 

<gtk.Menu object at 0xb6847eb4 (GtkMenu at 0x83aa5a8)>
Traceback (most recent call last):
  File "/usr/share/hal/device-manager/DeviceManager.py", line 132, in on_device_tree_selection_changed
    self.update_device_notebook(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'
Traceback (most recent call last):
  File "/usr/bin/hal-device-manager", line 20, in <module>
    DeviceManager()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 97, in __init__
    self.update_device_list()
  File "/usr/share/hal/device-manager/DeviceManager.py", line 247, in update_device_list
    self.update_device_notebook(self.virtual_root.children[0])
  File "/usr/share/hal/device-manager/DeviceManager.py", line 508, in update_device_notebook
    self.update_tab_device(device)
  File "/usr/share/hal/device-manager/DeviceManager.py", line 316, in update_tab_device
    d = self.udi_to_device(d.properties["info.parent"])
KeyError: 'info.parent'


using gutsy, compiz... any ideas?

---

### Post by ibuclaw on 2008-05-21
Have you recently had an Upgrade?

If you can, try downgrading the package to it's previous version.

Regards
Iain

---

### Post by Ashrael on 2008-05-26
Hmm, just came back here and saw your reply:
1) I wouldn't know how to downgrade (yet) never tried it..
2) Wouldn't it be fixed after the next update? It is not all that important, since all my harware works... 

;)

thanks for your suggestion.

---

