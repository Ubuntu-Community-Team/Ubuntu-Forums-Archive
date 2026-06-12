---
title: "hibernate problem"
date: 2006-11-15
forum: General Help
---

### Post by redbluemangle on 2006-11-15
When I hibernate my computer it goes into hibernation but then comes back on and I get a log in prompt. The first few times I did it the computer would shut off completely but my sessions would be restored upon reboot. 

The option to shut down has mysteriously vanished so really I have no way to initiate a soft shut down aside from the console which had some weird results  for me.

---

### Post by redbluemangle on 2006-11-15
bump. anyone know how to make hibernate work properly, or is it working properly now and the functionality it had before was wrong?

---

### Post by PartickThistle on 2006-11-16
You should give us more than 10 minutes before bumping :)

This may or may not work.  It worked for me though.


Ensure your swap space is in use.
```
cat /proc/swaps
```
If not, re-create it. Change /dev/hdXX to whatever your swap partition is.
```
sudo mkswap -c /dev/hdXX
```
Activate your swap.
```
sudo swapon /dev/hdXX
```
Ensure your resume partition is set properly.
```
sudo nano -w /etc/initramfs-tools/conf.d/resume
```
Change this to /dev/hdXX then regenerate your initrd.
```
sudo update-initramfs -u
```
Reboot then test. 

Good luck.

---

### Post by aprogram on 2007-01-22
I have the same problem. Following your instructions did not fix this bug for me.

---

### Post by simpsonsfan74 on 2007-02-21
It worked for me!  I was using an encrypted swap partition.  If I turn off encrypted swap and follow the instructions above, problems fixed! (Both hibernate and standby work fine now.)

---

### Post by wgw on 2008-07-22
Worked for me! (Can't seem to find the thank you button, but thanks PatrickThistle.)

---

