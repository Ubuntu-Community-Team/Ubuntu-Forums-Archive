---
title: "Cannot sleep/suspend after installation NVIDIA drivers"
date: 2018-09-25
forum: General Help
---

### Post by bertar on 2018-09-25
I installed the NVIDIA binary driver 340.107 (from the [PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=xenial"), indicates "[COLOR=#333333][FONT=monospace]For G9x use `nvidia-340`[/FONT][/COLOR]) to have dual monitor support for my GeForce 9600 GT graphics card
However the driver causes issues when trying to get to sleep/suspend
Sometimes I get 
```
GDBus.Error:org.freedesktop.login1.OperationInProgress: There's already a shutdown or sleep operation in progress
```
and I'm unable to get to use the sleep/suspend function.
Also sometimes when getting from sleep/suspend the network connection is gone.
I am on Lubuntu Ubuntu 16.04.5 
Any ideas how to solve this problem?

---

