---
title: "Intermittent shutdown errors"
date: 2021-06-13
forum: General Help
---

### Post by MaccyDG on 2021-06-13
Hello,

OS: Ubuntu 20.04
System: Dell Latitude 5580 with Kingston A2000 NVMe PCIe SSD

Problem: issuing shutdown or restart commands sometimes leads to errors and a failure to shut down properly. Example below:
[https://ibb.co/ZYRdMJ9](https://ibb.co/ZYRdMJ9)
[https://ibb.co/582dVBg](https://ibb.co/582dVBg)
NB: photos are not searchable, so if this issue is resolved, I would appreciate if someone could instruct me as to how to extract this information in text form for the benefit of future users. I can't see it using journalctl.

**More info**
The one time I allowed the command to run until its conclusion, the machine did restart, but then it displayed the message, "no boot device found". I went into the BIOS, didn't make any changes and exited again. It rebooted and went straight to the GRUB boot menu. Booting then proceeded as expected. The machine is being dual-booted with Windows and I get no such issues in Windows, so I believe it is software-related.

Any help gratefully received.

---

### Post by tea for one on 2021-06-13
Some Kingston SSD NVME drives need a little tweak in grub - added in blue below:-
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]nvme_core.default_ps_max_latency_us=0[/COLOR]"
GRUB_CMDLINE_LINUX=""
```

Don't forget to update grub after editing:-
```
sudo update-grub
```
[https://tekbyte.net/2020/fixing-nvme...lems-on-linux/](https://tekbyte.net/2020/fixing-nvme...lems-on-linux/)

Fingers crossed

---

### Post by MaccyDG on 2021-06-13
Tea for one, many thanks. I am posting the full link, as it seems to have been shortened in your post: [https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/).

After 10 restarts and a /home backup (which up until now had always crashed before completing), all seems good. After ~10 years using Ubuntu as my main OS, I had spent so many hours on this problem that I was considering switching to Windows. I'm really grateful that you made the effort to point me to a solution.

---

### Post by tea for one on 2021-06-13
Sorry about the link - I copied and pasted it from a previous thread but forget to double-check its direction.

Anyway, I'm pleased that it helped.

I have a Kingston A2000 250Gb nvme drive and it gave me some grief for a few weeks until I found the grub parameter.

To be honest, I'm not sure exactly what the parameter does but since implementing the alteration to grub over 6 months ago, I've not had a problem.

It is a pity that Kingston is not a member of LVFS [https://fwupd.org/](https://fwupd.org/)

---

