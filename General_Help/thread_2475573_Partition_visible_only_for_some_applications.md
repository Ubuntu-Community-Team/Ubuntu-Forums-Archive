---
title: "Partition visible only for some applications?"
date: 2022-06-01
forum: General Help
---

### Post by harry5552 on 2022-06-01
Using Ubuntu 22.04 fully updated


I have a 2TB hard drive that I've created a ext4 (tried fat32 & ntfs as well but no different), partition on using gparted and mounted using disks (using session defaults) to /mnt/test-ext4-1


from a terminal logged in as "ade" (admin)-

mount | grep test-ext4-1
# shows "/dev/sdc11 on /mnt/test-ext4-1 type ext4 (rw,nosuid,nodev,relatime,x-gvfs-show)"

sudo chown $USER:$USER /mnt/test-ext4-1
ls -lah
# shows "drwxr-xr-x  3 ade  ade  4.0K Jun  1 14:03 test-ext4-1"

touch /mnt/test-ext4-1/test.txt
# create the file fine

using Nautilus to copy a folder to it works fine also, now the problem
opening the test.txt file in sublime works fine but trying to open a jpg in the folder in GIMP or Pinta, I can't even see the test-ext4-1 partition (attached)!


Any ideas, this is doing my head in, what have I missed? it's as though those programs aren't being run as the logged in user ade (an administrator)


Thanks in advance

---

### Post by Holger_Gehrke on 2022-06-01
Have you perhaps installed GIMP or Pinta as snaps ? Applications installed that way are confined using AppArmour so that they can't see anything except the $HOME of the user starting them and that user's subdirectory in /media/. To find out whether that's your problem run 'snap list'. If the programs in question are on that list, then that's most likely your problem.

Holger

---

### Post by harry5552 on 2022-06-01
OMG, they are, had absolutely no idea that was the case, wasted days trying to sort it - thanks very much for you help

EDIT: just one more thing, sublime is installed via snap but it can see that partition?

---

### Post by Holger_Gehrke on 2022-06-01
According to 'snap info sublime-text' that snap is installed in 'classic' mode, which means it's not confined. And no, you can't switch the confinement mode for a snap, that is fixed when the program is packaged.

Holger

---

