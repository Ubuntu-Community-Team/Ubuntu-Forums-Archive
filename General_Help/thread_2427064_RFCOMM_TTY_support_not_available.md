---
title: "RFCOMM TTY support not available"
date: 2019-09-17
forum: General Help
---

### Post by lambyxq on 2019-09-17
Hello everyone,

These days, I tried to use "rfcomm" to read the data from the external bluetooth device to Jetson Nano (ubuntn 18.04 with the architecture of aarch64 was installed in this microcontroller). When I used this command "sudo rfcomm bind 0 00:04:3E:4B:32:40”, the error message araise which said “RFCOMM TTY support not available". I googled a lot and asked many people, but still could not solve this issue. Any suggestions will be appreciated! 

Here are some additional informationmode.

1) I found out there was no tty support in the kernel configuration file.

lamb@lamb-desktop:~$ zcat /proc/config.gz | grep RFCOM
CONFIG_BT_RFCOMM=y
CONFIG_BT_RFCOMM_TTY is not set

[SIZE=1]2) I tried to recompile the module with tty support, but error message said "kernel configuration is invalid"

sudo apt-get install linux source
[/SIZE]cd in /usr/src/linux-`uname -r`/ and give this command:
make CONFIG_BT_RFCOMM=m CONFIG_BT_RFCOMM_TTY=y M=net/bluetooth/rfcomm

3) kernel version
lamb@lamb-desktop:~$ uname -aLinux lamb-desktop 4.9.140-tegra #1 SMP PREEMPT Tue Jul 16 17:04:49 PDT 2019 aarch64 aarch64 aarch64 GNU/Linux

4) I found in the path /lib/modules/4.9.140-tegra/kernel/net/bluetooth/, only bnep.ko was available.

Best regard,
Xiaoqun Yu

---

### Post by dino99 on 2019-09-17
If it can help: relative answer  [https://askubuntu.com/questions/1025080/unable-to-create-dev-rfcomm-port](https://askubuntu.com/questions/1025080/unable-to-create-dev-rfcomm-port)

---

### Post by lambyxq on 2019-09-17
Hi dino99,

Thank you for you quick reply. Actually, I also checked this info, because in my system, rfcomm command was not supported, this answer could not work. Thank you anyway! 

Best regard,
Xiaoqun Yu

---

### Post by lambyxq on 2019-09-19
Hi,


I hope my experience could help someone who may have the same needs as me.


After so many trial and errors, I finally found out the reason is that the default kernel doesn't support RFCOMM. In order to enable RFCOMM, we have to recompile the kernel. Here is a great tutorial for recompiling the kernel ([https://blog.hypriot.com/post/nvidia-jetson-nano-build-kernel-docker-optimized/](https://blog.hypriot.com/post/nvidia-jetson-nano-build-kernel-docker-optimized/)). Just follow it, then in the menuconfig panel, enable the "RFCOMM TTY support", which is under the "Networking support/Bluetooth subsystem support".




Then enjoy!


Best regard,
Xiaoqun Yu

---

