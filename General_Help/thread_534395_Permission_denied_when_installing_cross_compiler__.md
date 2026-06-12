---
title: "Permission denied when installing cross compiler / etc sw-development package"
date: 2007-08-25
forum: General Help
---

### Post by juhhi on 2007-08-25
Hello!

I am starting to learn linux / embedded linux and therefore installed ubuntu and bought a kit (ELLK from intellimetrix). Kit includes cross-compilers etc. sw, but I have to admit that I am having troubles with installation...

Manual says:

1. Insert and mount cdrom 
    
 As far as I can see this happens automatically to /media/cdrom?

2. Make sure you have write access to the directories /usr/local and /usr/src

Done. 'sudo chmod 777 <directories>'. Confirmed with 'ls -l <directories>'.

3. cd to your home directory

Done. 'cd /home/juhhi'. 

4. execute /mnt/cdrom/install.

Switched this to 'sudo /media/cdrom/install'.

And I get 'permission denied'...

I am very disappointed to myself that I can develop embedded software, but I am not capable of solving this one...please help...

---

### Post by solar george on 2007-08-25
The cdrom is probably mounted with the noexec option which prevents programs from being run from the cdrom.

Try

```
sudo mount -o remount,exec /media/cdrom
```

---

### Post by juhhi on 2007-08-25
Solved, THANK YOU!

---

