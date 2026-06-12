---
title: "i realy need help"
date: 2008-01-15
forum: General Help
---

### Post by Max_rulez on 2008-01-15
ok ive been using ubuntu for a while now

well since last time windows screwed up

i now have broken windows aagain but this time without doing a proper shutdown

and now my ubuntu (7.10) wont allow me to access (or mount) my windows partition

im not sure if im doing it wrong but when i try using "sudo mount -a"

it comes up with
 
"Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hdb1 /media/hdb1 ntfs-3g defaults,force 0 0"

ive tried to force but it tells me "mount: can't find force in /etc/fstab or /etc/mtab"

any help would be great thx

---

### Post by TidusBlade on 2008-01-15
Why not just boot into Windows and do a clean shutdown?

---

### Post by Max_rulez on 2008-01-16
thats the problem wen i boot windows i get blue screen before i even get to login screen

---

### Post by Sef on 2008-01-16
> thats the problem wen i boot windows i get blue screen before i even get to login screen

Can you get into recovery mode?  Press F8 when booting into Windows.

---

### Post by Max_rulez on 2008-01-17
nope ive tried everything there is no way to access windows

---

### Post by sumguy231 on 2008-01-17
```
mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
```
Try putting the force option before the device name:
```
mount -t ntfs-3g -o force /dev/hdb1 /media/hdb1
```

---

### Post by Max_rulez on 2008-01-20
root@max-desktop:~# mount -t ntfs-3g -o force /dev/hdb1 /media/hdb1
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.


thats wat i got

---

### Post by Max_rulez on 2008-01-20
oh and my computer is now even more stuffed then ever my CD drive now doesn't want to boot on startup

(i may add on no fault of anyone here)

---

### Post by aflog on 2008-01-20
Maybe you should put in your windows cd (if you have it) and boot from that, then use it to repair your windows installation. Then try booting into windows again then a clean shutdown... well at least thats what i would do :D

---

### Post by Max_rulez on 2008-01-20
oh yes and the drive is mounted so thanks sumguy

but has anyone got anything on my nonbooting cd drive

---

### Post by Max_rulez on 2008-01-20
> **aflog said:**
> Maybe you should put in your windows cd (if you have it) and boot from that, then use it to repair your windows installation. Then try booting into windows again then a clean shutdown... well at least thats what i would do :D

thx neway but the drive is now mounted do you have anything on m y cd drive plz

---

### Post by aflog on 2008-01-20
Np... about ur cd drive... ermmm... i wouldnt have a clue to be honest xD

---

### Post by Max_rulez on 2008-01-20
k thx neway

---

