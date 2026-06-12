---
title: "cannot free space on /boot file"
date: 2015-05-05
forum: General Help
---

### Post by okkie2 on 2015-05-05
sudo apt-get clean cannot free space on /boot file.
I get the following message: "The upgrade needs a total of 63,2 M free space on disk '/boot'. Please free at least an additional 51,1 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."
My trash is empty.
/boot file is very crowded but I cannot or rather do not know how to remome the old stuff other than sudo apt-get clean which does not react.
Any help will be appreciated. Thanks

---

### Post by dino99 on 2015-05-05
i suspect /boot been locked while active; so try in recovery mode.
and you can try resizing the partition when unmounted

note: using /boot is not the standard installation scheme; so except special needs, avoid such partitioning

---

### Post by SeijiSensei on 2015-05-05
Try running "sudo apt-get autoremove".  If you have a bunch of stale kernels in /boot, it will remove them gracefully.

---

### Post by okkie2 on 2015-05-05
Thanks for your quick reply. I used a install disc from the start and did not do any partitioning myself that I can remember as I do not have the knowledge. I am also not sure how to boot in recovery mode or how to resise the /boot partition. can you refer me somewhere  or assist please.

---

### Post by SeijiSensei on 2015-05-05
You don't need anything extra to run autoremove.  Just open a terminal and type "sudo apt-get autoremove" and let it work its magic.

---

### Post by okkie2 on 2015-05-05
I have also tried autoremove with no luck

---

### Post by SeijiSensei on 2015-05-05
Please post the results of "ls /boot" in [noparse]```

```[/noparse] tags.  Here's what I have on a Kubuntu 14.04 machine:
```

abi-3.16.0-33-generic         memtest86+.bin                vmlinuz-3.16.0-33-generic
config-3.16.0-33-generic      memtest86+.elf                vmlinuz-3.16.0-33-generic.efi.signed
grub                          memtest86+_multiboot.bin
initrd.img-3.16.0-33-generic  System.map-3.16.0-33-generic

```
The grub subdirectory is just 4 MB.  The files with the "-generic" endings are the kernel and support files used during boot.  The rest is the utility memtest86+.

All told /boot on my machine totals less than 50 MB.

---

### Post by okkie2 on 2015-05-06
Here is the result of ls/boot:okkie@okkie-MS-7788:~$ ls /boot
abi-3.13.0-43-generic         initrd.img-3.13.0-49-generic
abi-3.13.0-44-generic         initrd.img-3.13.0-51-generic
abi-3.13.0-45-generic         lost+found
abi-3.13.0-46-generic         memtest86+.bin
abi-3.13.0-48-generic         memtest86+.elf
abi-3.13.0-49-generic         memtest86+_multiboot.bin
abi-3.13.0-51-generic         System.map-3.13.0-43-generic
config-3.13.0-43-generic      System.map-3.13.0-44-generic
config-3.13.0-44-generic      System.map-3.13.0-45-generic
config-3.13.0-45-generic      System.map-3.13.0-46-generic
config-3.13.0-46-generic      System.map-3.13.0-48-generic
config-3.13.0-48-generic      System.map-3.13.0-49-generic
config-3.13.0-49-generic      System.map-3.13.0-51-generic
config-3.13.0-51-generic      vmlinuz-3.13.0-43-generic
grub                          vmlinuz-3.13.0-44-generic
initrd.img-3.13.0-43-generic  vmlinuz-3.13.0-45-generic
initrd.img-3.13.0-44-generic  vmlinuz-3.13.0-46-generic
initrd.img-3.13.0-45-generic  vmlinuz-3.13.0-48-generic
initrd.img-3.13.0-46-generic  vmlinuz-3.13.0-49-generic
initrd.img-3.13.0-48-generic  vmlinuz-3.13.0-51-generic
okkie@okkie-MS-7788:~$ 

Thanks

---

### Post by SeijiSensei on 2015-05-06
Ubuntu uses only the last two kernels, so you can safely delete anything with -48 or before.  You can do this quickly with this command:
```

cd /boot
sudo rm -f *-4[3-8]*
```
Before running that you should make sure those are the files you want to delete with
```

cd /boot
ls *-4[3-8]*
```
That should match all the files except those ending in -49 or -51.

You can verify which kernels are available at boot by running the command:
```
grep splash /boot/grub/grub.cfg
```
You'll see entries like this:
```
linux   /boot/vmlinuz-3.16.0-33-generic root=UUID=d5b782fb-49d1-438c-b1e4-e521b571ef69 ro  quiet splash $vt_handoff
```
The UUID will be different, but what matters are the version numbers of the active kernels.

You can see what kernel is in use with the command "uname -r".  In your case it should be 3.13.0-51-generic.

Once you delete the old stuff, any future kernel updates will keep the current kernel and delete the one preceding that.

---

### Post by steve_tirrell on 2015-05-06
same issue with mine, also unresolved

---

### Post by SeijiSensei on 2015-05-07
Did you read my response in the posting right above yours?  Just apply the same logic to your own machine's /boot.

---

