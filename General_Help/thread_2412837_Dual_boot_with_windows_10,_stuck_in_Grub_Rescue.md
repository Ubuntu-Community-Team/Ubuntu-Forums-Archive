---
title: "Dual boot with windows 10, stuck in Grub Rescue"
date: 2019-02-18
forum: General Help
---

### Post by kaitlynd1405 on 2019-02-18
Hello. A while ago I dual boot installed Linux with windows 10. Today I tried to remove Linux from my system, and I forgot to fix my windows boot. I deleted the partitions and then my windows crashed and I booted into Grub rescue. I do not wish to reinstall ubuntu or Linux, I just want to get back to windows 10. When I type “ls” none of the files listed work 
ex: typing “ls (hd0,msdos2)” gives me a “error: unknown filesystem) and this does this error with all of them. After trying this I typed “set” to which I got:
” boot=(hd0,msdos2)
cmdpath=(hd0)
prefix=(hd0,msdos2)/boot/grub
root=hd0”

so so I typed “set boot=(hd0,msdos2)
set prefix=(hd0,msdos2)/boot/grub
insmod normal”

after typing insmod normal I got the error”
”unknown file system”
im not sure what I’m doing wrong, any help is greatly appreciated. I can not afford to lose my windows system right now.

---

### Post by Impavidus on 2019-02-18
Is this an UEFI system? Most Windows 10 computers are. In that case you should be able to access the UEFI menu by hitting some key before the grub rescue prompt appears. Use that menu to start Windows directly.

---

### Post by yancek on 2019-02-18
You need to look in your BIOS for an option to boot windows.  Some manufacturers will have an option to "Boot from EFI file" or similar.  Look for that.  You can't use Grub to boot anything because you deleted the partition on which the Grub files reside.  You might have a file or two on the EFI partition but that is not enough to boot Grub.

---

