---
title: "Installing ISO's without burning.."
date: 2005-10-19
forum: General Help
---

### Post by floyd27 on 2005-10-19
Hi...
I have a game thats 3 ISO files and no cd;s to burn them on to....
I know you can install the game with just the ISO files but im unsure how to do it..

any help..
thanx

---

### Post by floyd27 on 2005-10-19
2. To mount Image (ISO) file

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

   3. To unmount Image (ISO) file

sudo umount /media/iso/


I got this form the guide but can someone explain how to access the ISo after its mounted..
i have tried in the past and got the ISO mounted but was unable to do anything with it???
I dont really fully understand what this is doing......
thanx

---

### Post by AndersAA on 2005-10-19
mkdir = makes a directory
modprobe = loads the module "loop" (needed for mounting files)
mount file.iso /media/iso/ -t iso9660 -o loop

Mounts file file.iso to /media/iso of type iso9660 (cdrom standard) type loop (to mount a file, not a partition/device).

After you've typed that, you can go to /media/iso and your files will be there (try ls /media/iso).  And after you'r done with it unmount it (to "turn it off").

---

