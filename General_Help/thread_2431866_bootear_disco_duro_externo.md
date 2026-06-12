---
title: "bootear disco duro externo"
date: 2019-11-23
forum: General Help
---

### Post by emil152 on 2019-11-23
hola buenas tardes: 
 Estoy intentando bootear un disco duro esterior pero no me funciona del todo alguien puede corregir? 

sudo su    me identifico como superuser 

mount  /dev/sda2  /mnt           monto el subdirectorio en el directorio de archivos del sistema 
mkdir /boot  
mkdir   /boot/efi          creo dos subdirectorios dentro del sistema de arranque efi 
mount /dev/sda1 /mnt/boot/efi        monto los subdirectorios en el sistema de arranque efi 


mount --bind /dev /mnt/dev     
mount --bind /proc /mnt/proc       relaciono tres archivos 
mont --bind /sys /mnt/sys  


chroot /mnt/bin/bas 

grub-install -d /usr/lib/grub/     intento que me de el nombre del archivo, pero no me funciona 

grub-install -de /usr/lib/grub/x86_64-efi --efi-directory=/boot/efi/ --removable /dev/sda 

upgrade-grub 


una ver realizado esto debería poder arracar el disco duro desde cualquier ordenador, ya que tengo configurado grub. 


pero no me va ..... cual es el error

---

### Post by sudodus on 2019-11-23
Please translate to English or ask in a national forum.

---

