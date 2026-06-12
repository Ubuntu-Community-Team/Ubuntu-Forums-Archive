---
title: "Display problem with DVI-to-VGA adapter"
date: 2018-02-28
forum: General Help
---

### Post by prvnrk on 2018-02-28
Hello friends,
I have machine with dual boot (Windows 10 & Ubuntu 17.10 Server)

```
root@ubuntu1950x:~# uname -a
Linux ubuntu1950x 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
root@ubuntu1950x:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 17.10
Release:        17.10
Codename:       artful
root@ubuntu1950x:~#
root@ubuntu1950x:~# lspci | grep -i VGA
06:00.0 VGA compatible controller: NVIDIA Corporation NV41GL [Quadro FX 1400] (rev a2)
root@ubuntu1950x:~#

```

As my machine has graphics card with DVI connectors and had to use DVI-to-VGA adapter to connect a monitor with VGA-VGA cable. I'm able to see BIOS messages but no display while ubuntu is being booted (after booting also). But no problems at all with Windows 10. If I don't use the adapter (instead use DVI cable) then there's no problem with Ubuntu as well. I also don't have X components installed on Ubuntu (no GUI) but I can't even see the text console (instead monitor just keeps blinking - as if no signal). I am able to SSH to my machine without any problems.

Please advise on how can I fix this issue.

regards,

---

### Post by Autodave on 2018-02-28
Did you install an Nvidia driver?  If so, which one and where did you get the driver from?

---

### Post by prvnrk on 2018-02-28
Thanks for the reply.

I did not install any drivers. It is perfectly working fine if I don't use the adapter.

---

