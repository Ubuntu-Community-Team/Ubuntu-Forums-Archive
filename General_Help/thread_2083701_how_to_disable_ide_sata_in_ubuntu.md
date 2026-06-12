---
title: "how to disable ide sata in ubuntu"
date: 2012-11-13
forum: General Help
---

### Post by jebi on 2012-11-13
hi
 
in the latest lts could some tell me if it is possible to disable ide and sata support? so no i could boot ubuntu off a usb hdd and and not have it see the the internal hdds?
 
i have had many problems booting off the usb hdd and it corrupting data on the internal hdds, you might say that it is unlikely , but pc works fine until i run usb ubuntu and access internal hdds next time i boot off internal hdd !!bam!! problems all over the place and corrupted files...
 
many thx
 
also is ubuntu x64 just as stable as x86?

---

### Post by dcstar on 2012-11-14
> **jebi said:**
> hi
 
in the latest lts could some tell me if it is possible to disable ide and sata support? so no i could boot ubuntu off a usb hdd and and not have it see the the internal hdds?
 
i have had many problems booting off the usb hdd and it corrupting data on the internal hdds, you might say that it is unlikely , but pc works fine until i run usb ubuntu and access internal hdds next time i boot off internal hdd !!bam!! problems all over the place and corrupted files...
 
many thx
 
also is ubuntu x64 just as stable as x86?

There are basically only two reasons that "USB Ubuntu" would corrupt files:
[LIST=1]
[*]You are accessing "Hibernated" Windows partitions;
[*]You are not correctly shutting down the Ubuntu session.
[/LIST]
There is nothing wrong with 64-bit Ubuntu, people have been using it for many years now.

There is no way to disable access to hardware components like drives (that I know of).

---

### Post by dtmbmw325i on 2012-11-14
What I would suggest is booting to the usb drive and if Ubuntu is  automatically mounting your other internal drives, I would unmount them from Nautilus. The other option would be to unmount them before rebooting or shutting down your computer. It would wait until any data is done being written or warn you about files being open before unmounting.

To disable Sata or IDE, try finding those options in your bios. That would be the complete, sure fire way to prevent them from mounting.

> **jebi said:**
> hi
 
in the latest lts could some tell me if it is possible to disable ide and sata support? so no i could boot ubuntu off a usb hdd and and not have it see the the internal hdds?
 
i have had many problems booting off the usb hdd and it corrupting data on the internal hdds, you might say that it is unlikely , but pc works fine until i run usb ubuntu and access internal hdds next time i boot off internal hdd !!bam!! problems all over the place and corrupted files...
 
many thx
 
also is ubuntu x64 just as stable as x86?

---

