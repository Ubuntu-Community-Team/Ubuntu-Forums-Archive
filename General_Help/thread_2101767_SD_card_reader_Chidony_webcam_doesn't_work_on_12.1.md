---
title: "SD card reader Chidony webcam doesn't work on 12.10 64 bits"
date: 2013-01-05
forum: General Help
---

### Post by Nicodeloin on 2013-01-05
Hi everyone, thank you for your support and your kindness sharing your knowledges.

Big trouble, need to work quickly on a project and after I uninstalled 12.10 32-bit  to install 64-bit.

The SD card reader Realtek and webcam Chidony no longer work.

Knowing that I have faced these problems a few months ago and I had solved them but now it's been a while and every thing i tried did not work.


I tried the basic thing :


[HTML]wget http://planet76.com/drivers/realtek/rts-bpp-   dkms_1.1_all.deb
               sudo apt-get install dkms
                  sudo dpkg -i rts-bpp-dkms_1.1_all.deb
[/HTML]After the last step, the answer is :
       

[HTML]        DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.5.0-21-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
[/HTML]And then, i feel like a random man who tried to conquier Linux and who failed... :)

Any ideas ?

Thanks in advance.

---

