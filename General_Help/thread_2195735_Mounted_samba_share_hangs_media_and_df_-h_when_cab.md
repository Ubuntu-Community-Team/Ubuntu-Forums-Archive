---
title: "Mounted samba share hangs /media and df -h when cable disconnected"
date: 2013-12-26
forum: General Help
---

### Post by helloworld1215 on 2013-12-26
Encountered behavior:

1. Unplugging an ethernet cable on which a samba share has been mounted will cause:
a. the /media to become inaccessible.
b. df -h to hang indefinitely

1. Why does this occur on (l)unix. Is there no auto dismounting execution?
2. Is there any way to resolve automatically on event of cable disconnection, as provided by a software package, configuration or execution of commands, without having to execute a unmount before removing the cable?
3. Is there a way to resolve the inaccessibility after it has occurred other than restarting the system? (umount /media/share hang indefinitely)

---

### Post by nerdtron on 2013-12-26
You could try restarting the samba service. (not sure if it will be fixed)
Same thing happens on NFS share. I think it is always best to make sure that your should unmount a share before you unplug the network cable.

---

