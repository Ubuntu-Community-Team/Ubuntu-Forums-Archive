---
title: "Frequent freezing on GB-BXBT 1900 Rev 1.0"
date: 2015-10-02
forum: General Help
---

### Post by SuperFreak on 2015-10-02
Running a new Celeron Brix NUC with Intel Bay Trail Graphics, Ubuntu 14.04.3. I updated to kernel 4.2.1 in a futile attempt to solve this to no avail and I don't know how/or if I should return to an earlier kernel.
Anyway I loaded Kodi onto the PC and am now experiencing frequent freezing. As I intended to use this almost solely for Kodi I have not tried much else other than light web surfing (no problems there so far. I have attached a snippet of my system log[ATTACH]264795[/ATTACH]


EDIT: I was just trying to copy the KODI log file when the sytem froze again even though Kodi was not running, so I don't think the problem lies with Kodi

---

### Post by SuperFreak on 2015-10-03
Fingers crossed, downgrading the kernel to 3.16.3 appears to have stopped the freezing. Found reference to this kernel on a developers thread for Kodi [https://github.com/OpenELEC/OpenELEC.tv/issues/3726]("https://github.com/OpenELEC/OpenELEC.tv/issues/3726")

---

### Post by nakanut on 2016-07-29
Made one of these recently with Mint 18 (kernel 4.4).  There is something in the BIOS that these later kernels do not like.
  
However disabling some of the default enabled BIOS settings have proved fruitful, namely:-

Intel Virtualization 
Intel Speedstep technology
Turbo mode
Smart connect
Smart fan control

Microcode has been enabled.

System uptime now 3 days with no hangs.  Runs really well with 4GB ram and 120GB SSD.

Can't comment on downgrading the kernel but others have said it could be the way to go?

---

