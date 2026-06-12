---
title: "compiz segfaults after latest ubuntu update"
date: 2008-06-02
forum: General Help
---

### Post by Lerxst on 2008-06-02
I just installed a bunch of updates this morning, I didn't look through the entire update list, but compiz or X must have been updates as well.

Compiz has stopped working completely, it just segfaults if I run compiz --replace in an xterm. Tried restarting X as well as rebooting the PC, and after the latter, compiz works for a few seconds of the time before segfaulting. /var/log/messages just says:
Jun  2 10:48:33 mypc kernel: [  321.288183] compiz.real[6334]: segfault at 800000fff8 rip 7f051c19dbcb rsp 7fff2680aa50 error 4
Jun  2 10:49:14 mypc kernel: [  361.574423] compiz.real[6707]: segfault at 8000000078 rip 7f9bdd2e8bcb rsp 7fffe7957170 error 4

GFX card: Geforce 8400 GS (Nvidia drivers 169.12)
1600X1200 resolution, glxinfo just says the normal stuff, direct rendering is active.

If I launch compiz in an xterm, the following happens:
lerxst@mypc:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Segmentation fault

So, could it be that Xgl is not present or the unsupported value that's the problem?

Or something else? Anyone else experiencing the same thing?

---

### Post by Forlong on 2008-06-02
Please provide more info, particularly what version of Ubuntu and what desktop environment.

Also post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by Lerxst on 2008-06-02
> **Forlong said:**
> Please provide more info, particularly what version of Ubuntu and what desktop environment.

Also post the output of ```
dpkg -l | grep compiz
``` and use the forum's [noparse]```
[/noparse] tag please (# button)
I see:

[CODE]
Ubuntu 8.04  (x64)
Gnome 2.22.2
X.Org X Server 1.4.0.90



ii  compiz                        1:0.7.4-0ubuntu7
ii  compiz-core                   1:0.7.4-0ubuntu7
ii  compiz-fusion-plugins-extra   0.7.4-0ubuntu1
ii  compiz-fusion-plugins-main    0.7.4-0ubuntu5
ii  compiz-gnome                  1:0.7.4-0ubuntu7
ii  compiz-plugins                1:0.7.4-0ubuntu7
ii  compiz-switch                 0.4.3~ubuntu-1
ii  compizconfig-backend-gconf    0.7.4-0ubuntu1
ii  compizconfig-settings-manager 0.7.4-0ubuntu2
ii  libcompizconfig0              0.7.4-0ubuntu1                      
ii  python-compizconfig           0.7.4-0ubuntu1

```

---

### Post by Forlong on 2008-06-02
Can you show us your **/etc/apt/sources.list** please?

---

### Post by Lerxst on 2008-06-02
> **Forlong said:**
> Can you show us your **/etc/apt/sources.list** please?

I most certainly can:

```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080318.1)]/ hardy main restricted

deb http://ftp.uninett.no/ubuntu/ hardy-security main restricted
deb-src http://ftp.uninett.no/ubuntu/ hardy-security main restricted
deb http://ftp.uninett.no/ubuntu/ hardy-security universe
deb-src http://ftp.uninett.no/ubuntu/ hardy-security universe
deb http://ftp.uninett.no/ubuntu/ hardy-security multiverse
deb http://ftp.uninett.no/ubuntu/ hardy universe restricted multiverse main
deb http://ftp.uninett.no/ubuntu/ hardy-updates universe restricted multiverse main
deb http://ftp.uninett.no/ubuntu/ hardy-proposed universe restricted multiverse main
deb http://ftp.uninett.no/ubuntu/ hardy-backports universe restricted multiverse main
deb-src http://ftp.uninett.no/ubuntu/ hardy-security multiverse

```

---

### Post by Forlong on 2008-06-02
Remove hardy-backports.
Afterwards, remove any packages related to Compiz and reinstall them afterwards (make sure to reload the package information via 'sudo apt-get update' or in Synaptic first).

---

### Post by Lerxst on 2008-06-02
> **Forlong said:**
> Remove hardy-backports.
Afterwards, remove any packages related to Compiz and reinstall them afterwards (make sure to reload the package information via 'sudo apt-get update' or in Synaptic first).

That seemed to have done the trick, been toying with compiz settings for 10 minutes with no crash.

Thank you!:KS

---

