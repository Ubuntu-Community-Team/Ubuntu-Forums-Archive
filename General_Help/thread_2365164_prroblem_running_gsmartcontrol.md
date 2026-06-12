---
title: "prroblem running gsmartcontrol"
date: 2017-07-03
forum: General Help
---

### Post by bjlockie on 2017-07-03
$ gsmartcontrol
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.

Any idea what the error is?

---

### Post by CatKiller on 2017-07-03
smartctl needs to be run as root, and you need to specify a device.

I don't know for sure that gsmartcontrol does too but, given that it's simply a front-end for smartctl, it seems extremely likely that it does.

---

### Post by bjlockie on 2017-07-03
Running with sudo worked.
Is there a way to enable any user to run it?

---

### Post by CatKiller on 2017-07-03
> **bjlockie said:**
> Running with sudo worked.
Is there a way to enable any user to run it?

Probably, but you wouldn't want to. Information can be read by userland  tools (I use conky for it) but you don't want normal users to be messing  around with the hardware parameters of your hard drives.

Also,  you shouldn't use sudo for graphical tools that need root. Use gksudo  for those instead, and use sudo only for command-line tools.

---

