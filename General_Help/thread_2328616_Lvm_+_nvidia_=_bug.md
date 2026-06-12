---
title: "Lvm + nvidia = bug"
date: 2016-06-22
forum: General Help
---

### Post by oleg18 on 2016-06-22
*Hello Dear Friends!*

*I have a little cute problem*:

I installed Ubuntu 16.04 encrypted LVM and installed proprietary Nvidia driver.
After that, Ubuntu stopped running.

I see static screen: brown background with little password field. 
I press a keys on the keyboard (enter the password), but on the screen nothing changes and operation system  does not start.

---

### Post by ventrical on 2016-06-22
Is this a newer machine, older machine?
Are there any specs you can share as to what version you tried to install?

regards..

---

### Post by oleg18 on 2016-06-22
New machine, UEFI, Nvidia 780 gtx.

---

### Post by ventrical on 2016-06-22
if you can get to a terminal (ctrl+alt+f1) I would log in and remove nVidia.

```

sudo apt-get remove nVidia*

```

then
```

sudo apt-get install nouveau

```

then
```

sudo service ligthdm restart

```

regards..

---

### Post by oleg18 on 2016-06-23
It not work and I need normal nvidia driver and not nouveau.

---

