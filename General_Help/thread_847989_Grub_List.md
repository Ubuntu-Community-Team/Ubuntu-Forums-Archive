---
title: "Grub List"
date: 2008-07-03
forum: General Help
---

### Post by Uchiha_madara on 2008-07-03
Hi Nice members 

When i did the Update yesterday

the Grub List shows 3 version's of Ubuntu hardy

, their recovery mode , and Windows Xp 

i dont understand if Ubuntu is Updated or not

and how Could i Edit The List


:KS

---

### Post by lisati on 2008-07-03
Don't worry - this is normal. The update keeps older versions, "just in case" something goes wrong, so that you have something to go back to.

---

### Post by Uchiha_madara on 2008-07-03
Ok , But i need to Edit the Grub List 

Just i need a nice Look to The List

---

### Post by iaculallad on 2008-07-03
> **Uchiha_madara said:**
> Hi Nice members 

When i did the Update yesterday

the Grub List shows 3 version's of Ubuntu hardy

, their recovery mode , and Windows Xp 

i dont understand if Ubuntu is Updated or not

and how Could i Edit The List


:KS

By using Synaptics Package Manager to delete the old version of your KERNEL will automatically update your /boot/grub/menu.lst file.

-Navigate to System->Administration->Synaptic Package Manager, click on "Search" and type "linux-image" (w/o double quote). List of kernels will display and you'll have to right-click on the OLD kernel files and select "Mark for Complete Removal". Do the same with other older kernels. Once finished marking the old kernels, click on Apply.

NOTE: It would be better for you to keep the previously updated Kernel version for backup purposes if in case the new kernel version produces problems.

*/boot/grub/menu.lst file is the configuration Ubuntu uses for you Boot Menu at startup.

---

### Post by diafanos on 2008-07-03
You can just edit your grub file. Type:

```
sudo gedit /boot/grub/menu.lst
```

give your password.

Then in the file find the section begins like this:

```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bcf07c0-272e-4645-84e4-4505aef31bfa ro splash vga=0x031b
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

for every entry in you grub list, there is a similar scheme.
Just keep only the latest kernel and comment the other ones (or any entry you don't want to see in your grub menu), like this:

```

#title		Ubuntu 8.04, kernel 2.6.24-19-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bcf07c0-272e-#4645-84e4-4505aef31bfa ro splash vga=0x031b
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

```

Then just save file, and next time the grub menu will show only what you want.

---

### Post by Uchiha_madara on 2008-07-03
> **iaculallad said:**
> 
NOTE: It would be better for you to keep the previously updated Kernel version for backup purposes if in case the new kernel version produces problems.



The Question here does the Previous Kernel take Much Space
or not ????

---

