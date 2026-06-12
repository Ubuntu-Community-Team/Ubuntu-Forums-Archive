---
title: "Mounting windows share during boot time"
date: 2007-12-26
forum: General Help
---

### Post by amitst on 2007-12-26
I am able to mount a Windows share through command prompt. I am also able to mount the share using "sudo mount -a" command (so I have put the correct entry in /etc/fstab).

I assume that the /etc/fstab is automatically mounted during the boot time, But I noticed that the windows share mount entry in this file is not getting mounted during boot. Other entries like NTFS partitions on the same disk are getting mounted during boot. Is there any way to mount windows share during boot?

---

### Post by Craigus on 2007-12-26
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by amitst on 2007-12-26
I think I have tried the things mentioned in this link. The entry is present in /etc/fstab and the "sudo mount -a" command mounts all the windows shares properly. The issue is that the windows share entries are not mounted at boot time (other entries are mounted at boot time).

Am I missing anything in this link? May be my network card is not properly initialized while mounting these areas at boot time and because of this it may not be mounting these shares?

---

### Post by amitst on 2007-12-27
I put "mount -a" command in the /etc/rc.local file and the windows shares started mounting automatically after reboot. I know this is a dirty way but at least it is working now.

---

