---
title: "msi laptop not shutting down, rebooting or suspending"
date: 2018-07-17
forum: General Help
---

### Post by unjokk on 2018-07-17
I've got msi gp62 7rex leopard pro laptop. It has ubuntu 18.04 installed. The problem is that one day it just stopped shutting down, rebooting and suspending. It shows this when shutting down or rebooting: [https://imgur.com/AthA1Pu](https://imgur.com/AthA1Pu) And this when suspending: [https://imgur.com/5otDEz5](https://imgur.com/5otDEz5) . What i tried       
[list]      
[*] reinstalling system    
[*] resetting bios settings       
[*] removing 'quite splash' from /etc/default/grub       
[*] adding 'acpi=force' or 'acpi=off' or 'apm=power_off' to /etc/default/grub       
[*] shutting down with 'shutdown now', 'systemctl shutdown', 'halt', 'poweroff -f', 'init 0'       
[*] unplugging everything from the laptop when shutting down    
[*] stopping display manager before shutting down       
[*] unloading kvm module before shutting down       
[*] shutting down in software render mode       
[*] shutting down on integrated graphics       
[*] go into recovery mode and run fsck     
[/list]
     What could it be? Is my laptop haunted? Do updates have bugs (if so, how do i downgrade all packages for like 2 months old?)? Maybe it's hardware failure? How do i fix it, at least temporary (considering installing other distro or rolling back to 16.04 is not the option)?

---

