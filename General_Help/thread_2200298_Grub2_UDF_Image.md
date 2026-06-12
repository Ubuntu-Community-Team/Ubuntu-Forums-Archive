---
title: "Grub2 UDF Image"
date: 2014-01-18
forum: General Help
---

### Post by Alexander_Mudrov on 2014-01-18
I have to apologize. I'm not native English speaker, so don't kill me for mistakes please :))) And I also didn't found neither similar topics nor in which forum I must ask this question. Sorry.

I want to make multiboot dvd which will contain Ubuntu LiveCD, Windows 7 installation and WinPE. The image will be about 7,5 GB (approx.), so the only FS for it is UDF.
So I want to make UDF image with Grub2 as a bootloader.

I made simple Grub2 ISO image with grub-mkrescue (with inserting UDF and MS-DOS modules during image creation), converted it to UDF with UltraISO and fulfilled it with data. I'm tried to test image in VirtualBox and in result Grub2 was unable to access UDF filesystem and dropped in grub-rescue shell.

Please help.

---

