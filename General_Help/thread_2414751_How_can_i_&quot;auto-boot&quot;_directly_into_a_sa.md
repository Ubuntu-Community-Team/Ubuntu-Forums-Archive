---
title: "How can i &quot;auto-boot&quot; directly into a safe mode kernel and choose it from liveusb?"
date: 2019-03-14
forum: General Help
---

### Post by usernamoi on 2019-03-14
what i want to try to do is to choose a different kernel to load from a liveusb, and that it also autostarts in safe mode the next time i try to start my os (ubuntu-studio 16.04, mixed with with kubuntu files ie desktop +  dolphin file manager). As long as im able to reach the login screen and boot again, i will be able to backup my files at /home/user and reinstall the system (which im currently unable to mount since i forgot to write, or where i left the login passphrase, and i ignore if theres a way to mount encrypted home flder with my user name and password from a liveusb).

Im unable to choose manually any alternative kernels in grub, and thanks to another user i tried booting directly without it after following this command:

```
efibootmgr -c -d /dev/sda -p 1 -L ubuntu_new -l /EFI/ubuntu/shimx64.efi
```

This didnt solved my problem, but at least now i know its unrelated to grub. My problem started when i tried to reinstall a kernel, but somehow it became duplicated and maybe overwrote improperly some files. whatever it did, or however it happened, what matters is that im unable to reach login screen, and that when i was using grub if i tried to open "advanced options" a terminal screen began to load a lot of information and became stuck in a "initramfs" thing.

This is how it looked (before previous command; it currently just attempts to load kernel and remains stuck as the last clip):

turning on pc (laptop)
[https://streamable.com/6mmg0](https://streamable.com/6mmg0)

what happened when i tried to use "advanced options"
[https://streamable.com/39wau](https://streamable.com/39wau)

stuck and unable to do anything
[https://streamable.com/j3g07](https://streamable.com/j3g07)


Also, why i have two ubuntu shimx64.efi files? can this be related to the duplicated kernel problem?
sda1: __________________________________________________________________________

    ```
File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /Boot/bootx64.efi 
                       [FONT=arial black]**/ubuntu/shimx64.efi** /EFI/Boot/bootx64.efi[/FONT] 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi [FONT=arial black]**/EFI/ubuntu/shimx64.efi **[/FONT]
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /boot-repair/log/20180616_072944/sda1/bootx64.efi
```

---

