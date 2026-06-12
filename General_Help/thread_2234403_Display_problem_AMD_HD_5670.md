---
title: "Display problem AMD HD 5670"
date: 2014-07-14
forum: General Help
---

### Post by bizhat on 2014-07-14
Hi,


I am using Ubuntu 14.04 64 bit.


My Graphics card is AMD HD 5670.


--------------
me@mypc:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 5670
OpenGL version string: 4.4.12967 Compatibility Profile Context 13.35.1005


me@mypc:~$ 
--------------


When i take graphics heavy page like humblebundle, runescape, etc.., my display get distrorted like this.


[[IMG]http://i.imgur.com/OSQ9Kkdl.png[/IMG]](http://imgur.com/OSQ9Kkd)


I tried opensource driver, the default fglrx driver provided by ubuntu and the latest from AMD site. Currently using latest driver from AMD.


Is there anyway to fix this issue ?


Thanks,


Boby

---

### Post by QIII on 2014-07-14
Hello!

When you installed the fglrx driver by various methods, did you first uninstall the one you had installed before trying the next?

I'm not sure what you have there is a graphics driver issue as much as, perhaps, a Flash/browser issue.  It appears that only the contents of the browser are garbled. If it were a graphics driver issue, everything else would probably be a mess.

---

### Post by bizhat on 2014-07-15
In the screenshot it is only content of the browser grabled. But really it was whole browser, including all tabs, title bar etc.. When i take screenshot,i only got that much.

I seen this in firefox and chrome. I will try other application and see if it happens.

When i switched graphics drivers, i just selected the check box in Ubuntu Software & Updates > Additional driver. Before installing AMD catalyst from AMD site, i don't remember if i uninstalled other as it done it few months back.

> 
me@mypc# dpkg -l | grep fglrx
ii  fglrx                                                 2:14.200-0ubuntu1                                   amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                        2:14.200-0ubuntu1                                   amd64        Catalyst Control Center for the AMD graphics accelerators
rc  fglrx-updates                                         2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  xvba-va-driver                                        0.7.8-1ubuntu3                                      amd64        XvBA-based backend for VA API (AMD fglrx implementation)
me@mypc# 


So i have to remove these and install Catalyst again ? When i remove all graphics driver, will i still get display ?

---

