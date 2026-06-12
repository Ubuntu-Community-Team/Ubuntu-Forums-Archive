---
title: "Ubuntu 19.10 -&gt; Ubuntu 20.04 low battery life"
date: 2020-05-13
forum: General Help
---

### Post by moromete on 2020-05-13
Hello,

Clean install of Ubuntu 20.04 on my laptop
After install battery life decrease drastic.
Ubuntu 19.10 4-5 hours.
Ubuntu 20.04 1+1/2 hours.
Using powertop discovered

367 mW mysqld
302 mW tick_sched_timer

$inxi -Fx
System:    Host: romeo-atom Kernel: 5.4.0-29-generic x86_64 bits: 64  compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Detachable System: LENOVO product: 80XF v: Lenovo MIIX  320-10ICR serial: <superuser/root required> 
           Mobo: LENOVO model: LNVNB161216 v: SDK0J91196WIN serial:  <superuser/root required> UEFI: LENOVO v: 5HCN39WW 
           date: 05/11/2018 
Battery:   ID-1: BAPM charge: 29.3 Wh condition: 33.3/33.3 Wh (100%)  model: Bitland AXP288 status: Discharging 
CPU:       Topology: Quad Core model: Intel Atom x5-Z8350 bits: 64 type:  MCP arch: Airmont rev: 4 L2 cache: 1024 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx  bogomips: 11520 
           Speed: 480 MHz min/max: 480/1920 MHz Core speeds (MHz): 1:  480 2: 480 3: 480 4: 480


I don't know what can i do.
Returning to 19.10 is not an option.

Any help ?

---

### Post by monkeybrain20122 on 2020-05-13
Battery life has to do with kernel I think. You can either wait for kernel update to solve your problem or try grab and install a different one from[ here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/").
Choose your kernel version,  download these packages and put them in one folder, say linux.

linux-headers all.deb
linux-headers generic amd64.deb
linux unsigned image generic amd64.deb
linux modules generic amd64.deb

I assume you are using 64-bit

Open the terminal
```
cd /path/to/the/folder/where/you/put/packages #for example cd linux if your packages are in a folder called linux in your home

sudo dpkg -i *.deb
```

reboot, press ESC to choose the kernel to boot into (or it will automatically boot into the new kernel if it is higher than your current version)  If it solves your problem, keep it, if it doesn't or if it creates other problems, boot into your current kernel to delete the packages you just installed. It is easy to manage packages with synaptic  so if you haven't installed it yet
```

sudo apt install synaptic
```

---

### Post by moromete on 2020-05-13
Thank you, i will try your solution this afternoon

---

### Post by daniewicz on 2020-05-13
Uninstall mysql?

 [COLOR=#242729][FONT=Arial][FONT=Consolas]sudo apt purge mysql-*[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=Consolas]sudo apt autoremove[/FONT][/FONT][/COLOR]

---

### Post by moromete on 2020-05-18
> **daniewicz said:**
> Uninstall mysql?

 [COLOR=#242729][FONT=Arial][FONT=Consolas]sudo apt purge mysql-*[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=Consolas]sudo apt autoremove[/FONT][/FONT][/COLOR]

No, i need MySQL for developing.
$systemctl stop mysql
$systemctl disable mysql

and starting only when i needed.
An more, installed kernel 5.7.0-999-generic.
Now is fine with battery.
Need more tests to see if is viable soultion.
Thanks to                                                                                      [COLOR=#000000]monkeybrain20122[/COLOR] and daniewicz !

---

### Post by moromete on 2020-05-19
Yes, is working, again 4-5 hours of life.
Ubuntu rocks !

---

