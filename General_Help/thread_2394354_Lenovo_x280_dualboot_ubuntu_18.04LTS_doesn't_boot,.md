---
title: "Lenovo x280 dualboot ubuntu 18.04LTS doesn't boot, grub 2.02. THX 4reading, any idea?"
date: 2018-06-15
forum: General Help
---

### Post by herrmeier on 2018-06-15
Hi all,

thx for reading and perhaps your thoughts on this grub2-problem:

I am having problems to boot with grub2. The auto-configuration during installation of kubuntu 18.04 LTS seems to need a little improvement, even though the Lenovo x280 is certified for ubuntu-pre-installation, (ok, only for ubuntu 16.04 LTS ;-)),  => [https://certification.ubuntu.com/hardware/201801-26057/](https://certification.ubuntu.com/hardware/201801-26057/)

Right now I can only boot if I boot from usb using multiboot (yumi) and supergrub2.
Perhaps you have an idea how I could update my grub2-configuration in a way that allows me to boot without the usb stick.

Here some Systeminfo:
inxi
$ inxi -Fxxxz --no-host | pastebinit
[http://paste.ubuntu.com/p/mJZ4Gzcxvm/](http://paste.ubuntu.com/p/mJZ4Gzcxvm/)

blkid
$ sudo blkid -o list -w /dev/null
 [https://paste.ubuntu.com/p/kkc4VCmcRS/](https://paste.ubuntu.com/p/kkc4VCmcRS/)

MBR
$ sudo hexdump -s0 -n512 -C /dev/nvme0n1
[https://paste.ubuntu.com/p/nT5CqZZkd4/](https://paste.ubuntu.com/p/nT5CqZZkd4/)

GPT
$ sudo hexdump -s1 -n512 -C /dev/nvme0n1
[https://paste.ubuntu.com/p/G7wj3VdnCg/](https://paste.ubuntu.com/p/G7wj3VdnCg/)

bootinfoscript 0.76
[https://github.com/arvidjaar/bootinfoscript/blob/master/bootinfoscript](https://github.com/arvidjaar/bootinfoscript/blob/master/bootinfoscript)
$ sudo bootinfoscript
[https://paste.ubuntu.com/p/SRk9Dxrjdz/](https://paste.ubuntu.com/p/SRk9Dxrjdz/)


grub.cfg
cat /boot/grub/grub.cfg|pastebinit
[http://paste.ubuntu.com/p/FfQ9fXVhg6/](http://paste.ubuntu.com/p/FfQ9fXVhg6/)

$ sudo file -s -N -F';' /dev/nv*|egrep 'GR|ID=0xee|data$'| tr -s ';' '\n' | pastebinit 
[http://paste.ubuntu.com/p/y8BKzYkV6J/](http://paste.ubuntu.com/p/y8BKzYkV6J/)

Many thanks for reading all of the above. I'd be very grateful for your posts of any helping ideas.

---

### Post by dixonstalbert on 2018-06-15
Have you seen this?

[https://askubuntu.com/questions/696999/unable-to-install-grub-in-dev-nvme](https://askubuntu.com/questions/696999/unable-to-install-grub-in-dev-nvme)

---

### Post by oldfred on 2018-06-16
Boot-Repair uses bootinfoscript as part of its output, but with NVMe drives bootinfoscript does not show much. I have a request to add NVMe drive parse with bootinfoscript, but he needs someone with a NVMe drive to test it.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)  
    You do not need to edit out UUID, GUIDs as those are unique to you, but not used externally (as far as I know).

You could try in Boot-Repair the advanced option of total reinstall of grub. Be sure to boot in UEFI boot mode and choose install and NVMe drive, but not partition.

Some Lenovo's have modified UEFI to only boot UEFI by description which violates UEFI standard. And of course only valid description is "Windows Boot Manager". Multiple work around, some better and depending on configuration. See link in my signature.

---

