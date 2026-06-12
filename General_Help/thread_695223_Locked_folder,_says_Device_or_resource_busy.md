---
title: "Locked folder, says: Device or resource busy"
date: 2008-02-12
forum: General Help
---

### Post by Muscar on 2008-02-12
I've got a locked folder on my dekstop, when i do:
cd ~/Desktop; ls -al
sudo rmdir directoryname
It gives me: rmdir: directoryname: Device or resource busy

---

### Post by apetresc on 2008-02-12
Something is using the directory, possibly another shell. Do ```
sudo lsof | grep myfoldername
``` to find out exactly what.

---

