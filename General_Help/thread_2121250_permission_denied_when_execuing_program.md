---
title: "permission denied when execuing program"
date: 2013-03-01
forum: General Help
---

### Post by aaronmarsh632 on 2013-03-01
hi, im logged into a terminal as sudo but i get permission denied when executing a program (using ./program_name)

I dont know what to do from here, I tried chmod 666 program_name if this is correct but nothing changed.

Please can anyone help?

Im using clean install of ubuntu 12.04, any more info needed just ask

Thanks

---

### Post by Impavidus on 2013-03-01
Try chmod 755 <name>

chmod 666 make the file readable and writable for all, but not executable.

---

### Post by aaronmarsh632 on 2013-03-01
Thanks for this, I just tried it but still get permission denied, I read somewhere about changing some options in the fstab file is this something I may need 2 do ?

Thanks

---

### Post by Impavidus on 2013-03-01
Is that file located on a linux partition or on a windows partition or something else? If it's in your root or /home partition you don't have to change any options in fstab.

---

