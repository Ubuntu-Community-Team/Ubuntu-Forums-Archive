---
title: "help me, i cant get out of grub rescue..."
date: 2014-08-27
forum: General Help
---

### Post by brandon_maceri on 2014-08-27
so i bought a laptop with windows 8 installed on it but i wanted to put ubuntu on it instead. so i did a fresh install of ubuntu on the laptop which got rid of windows 8. i installed it on UEFI not legacy.

today i wanted to reinstall windows on my laptop and get rid of ubuntu and just run VMware on my desktop with ubuntu just for command line practice.

for some reason i had a lapse of judgment, went into my bios and switched the boot from UEFI to legacy mode. don't ask me why i did this i am still learning. 
now when i turn on my laptop it stays in grub rescue>            the partition my ubuntu is on is (hd0,gpt2)   
i tried set prefix=(hd0,gpt2)/boot/grub
set root=(hd0,gpt2)
then when i do insmod normal  i get      error:  file /boot/grub/i386-pc/normal.mod not found     

i tried many commands and nothing works. 

i attached a picture of    ls (hd0,gpt2)/boot      and    ls (hd0,gpt2)/boot/grub
it shows an x86_64-efi  not    i386-pc  im guessing that's because i put it in legacy mode.

thank you for your help.

---

