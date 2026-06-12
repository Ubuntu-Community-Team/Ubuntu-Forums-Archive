---
title: "[Q] mounting ntfs"
date: 2005-05-01
forum: General Help
---

### Post by pdk001 on 2005-05-01
this time i have a question about ntfs 
music files are in windows
i cant move /mnt dir after i typed " sudo mount -t ntfs /dev/hdc1 /mnt" it says " permission denied" so i tried as "sudo cd /mnt" "cd /mnt" and " cd /mnt" in root terminal but i cant
any help would be appreciated 
thanks in advance

---

### Post by jodef on 2005-05-01
These are the instructions from the [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs) 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

in your case you would change /dev/hda1 to /dev/hdc1.

---

### Post by pdk001 on 2005-05-01
awesome
its work as well
thanks bunch once again

park dong kyu

---

