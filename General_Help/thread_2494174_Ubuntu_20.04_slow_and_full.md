---
title: "Ubuntu 20.04 slow and full /"
date: 2024-01-07
forum: General Help
---

### Post by sofasurfer on 2024-01-07
I have Ubuntu 20.04 with 1gig drive.  /home on a seperate part and / on its own 53.91 gig with 43.67 gig used. Computer runs slow. I start it and when the desktop loads I see the icons jump out to the desktop. Other functions are slow also. I went into /boot/grml and deleted a 22.04 iso and a 20.04 iso. The amount of used space did not change. Why not? What else should I be looking for that will cause the slow down? 
I have 8gig of memory.

---

### Post by oldfred on 2024-01-07
What brand/model system? What video card/chip. 
Using SSD?
Is firmware on system & SSD most recent available from vendor?

Post these in code tags:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
cat /etc/fstab
systemd-analyze

did you empty trash?

---

### Post by sofasurfer on 2024-01-09
I found the trash folder in admin:///root/.local/share. That was the location of my trouble.

---

### Post by ajgreeny on 2024-01-09
> **sofasurfer said:**
> I found the trash folder in admin:///root/.local/share. That was the location of my trouble.
Interesting!

How did you manage to get so much in the trash of /root which on my systems has always remained empty or nearly so?
It sounds as if you are using a GUI for removing files/folders from the root system.

---

### Post by TheFu on 2024-01-09
sudo abuse.  

In general, don't run sudo with GUI programs, especially file managers. There are other reasons, but trash is one minor reason of many.

---

