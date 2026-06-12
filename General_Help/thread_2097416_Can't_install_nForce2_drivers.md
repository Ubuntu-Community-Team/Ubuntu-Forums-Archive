---
title: "Can't install nForce2 drivers"
date: 2012-12-23
forum: General Help
---

### Post by liufegi on 2012-12-23
Hi, I have installed Lubuntu on old system for a while and there is one problem with it :-\ There is no sound and no internet throught DSL :-\ There is drivers for Suse, Fendora and RedHat in this site: [http://www.nvidia.com/object/linux_nforce_1.25.html](http://www.nvidia.com/object/linux_nforce_1.25.html) . Maybe I could install any of those drivers on Lubuntu? And if I can, can you describe how, becaus I I'm very green on Linux installations. 

Have a nice day :-)

---

### Post by Yellow Pasque on 2012-12-23
The driver package you linked to contains extremely outdated files. All of those files are included in modern versions of the Linux kernel.

Can you post alsa info?: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by liufegi on 2012-12-23
So I don't need to install any nForce2 drivers? I believe that ethernet and audio drivers could be Realtek, not only nForce :-\ Maybe there is some software or command that automatically detects all hardware and update drivers?

---

### Post by Yellow Pasque on 2012-12-23
> So I don't need to install any nForce2 drivers? 
No. They're all included in the kernel. For example, even if your audio uses Realtek codec, it will still use snd-intel8x0 driver, which is included in kernel. Post your alsa info as I instructed previously.

---

### Post by liufegi on 2012-12-23
[http://www.alsa-project.org/db/?f=fe5cfe93e627dad04cd50872a013d20a0de8f445](http://www.alsa-project.org/db/?f=fe5cfe93e627dad04cd50872a013d20a0de8f445)

Here is the link

---

