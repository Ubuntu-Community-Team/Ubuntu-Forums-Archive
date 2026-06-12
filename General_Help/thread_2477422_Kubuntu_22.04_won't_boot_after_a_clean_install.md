---
title: "Kubuntu 22.04 won't boot after a clean install"
date: 2022-07-24
forum: General Help
---

### Post by stefanmarkic on 2022-07-24
**EDIT: Fixed**

On the Grub menu, I pressed 'e' on my keyboard and replaced 'quiet splash' with 'nomodeset'.
---



After a clean install of Kubuntu 22.04, I get these messages and computer just hangs infinitely:

 ```
[0.149135] x86/cpu: SGX disabled by BIOS
[5.427817] usb 1-6: 1:1: cannot get freq at ep 0x81
[5.440863] usb 1-6: 2:1: cannot get freq at ep 0x1
[5.464184] usb 1-6: 4:1: cannot get freq at ep 0x2

```


[LIST]
[*]ASUS Prime Z270-P 
[*]Intel i7-7700 
[*]Nvidia GTX 1070 
[*]Partition style: GPT 
[*]BIOS Mode: UEFI 
[*]I used Ventoy to create a bootable USB flash drive 
[*]Fast Startup disabled on Widows 10, which is installed on a separate SSD device 
[*]Linux Mint LMDE 4 used to work just fine for over 2 years on the same SDD device where I'm now trying to run Kubuntu 22.04 
[/LIST]
 
The only thing that works is Ctrl+Alt+Delete, which restarts machine.

---

