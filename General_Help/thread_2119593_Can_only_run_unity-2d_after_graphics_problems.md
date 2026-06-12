---
title: "Can only run unity-2d after graphics problems"
date: 2013-02-24
forum: General Help
---

### Post by dougleduck on 2013-02-24
Earlier I found when I turned my computer on it kept trying to start in low graphics mode, and I couldn't get it to actually start (sorry, no particularly useful info on why). I did notice a disk usage warning before I'd shut down, and so dropping to the console I freed up some space on my home partition, and also started using a failsafe xorg.cong. I'd tried some previous kernels, running fsck and suddenly nn the nth time ubuntu started, and I could login...

...but to unity-2d! The additional drivers list my amd driver as running (manually installed previously using there [instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.3"). These were installed ages ago and I've not had problems since.

However this is what fglrxinfo reported

```
 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

Running the following gave me
lspci -knn | grep VGA -A2
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Dell Device [1028:04cd]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] [1002:6741]
	Subsystem: Dell Device [1028:04cd]
	Kernel driver in use: fglrx_pci

```

And for anyone still reading I get this when trying to start AMD catalyst control

```
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.
```

Thanks for any help

---

### Post by dougleduck on 2013-02-24
So running 

[INDENT]sudo aticonfig --initial[/INDENT]

fixed the problem.

---

