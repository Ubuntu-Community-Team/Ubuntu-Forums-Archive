---
title: "Need help with /etc/fstab"
date: 2015-08-30
forum: General Help
---

### Post by samolnes on 2015-08-30
Hi, 


I am unable to mountmy second harddrive using /etc/fstab. It used to work, but afterupgrading to Ubuntu 15.04 it doesn't. 


I found the UUID ofthe disk, and are able to mount it in /mnt/Lager via /etc/fstab:
UUID="41cd095d-48a0-4c16-bb74-209cad30d389"/mnt/Lager ext4 nosuid,nodev,nofail 0 0
or
UUID=41cd095d-48a0-4c16-bb74-209cad30d389/mnt/Lager ext4 nosuid,nodev,nofail 0 0


But if I change thepath to mye homefolder (/home/sam/Lager) it doesn't turn up. My usercan do changes on the files in /mnt/Lager, so I dont think it is apermission problem. 


I also tried to add:
/mnt/Lager/home/sam/Lager none defaults,bind 0 0
in /etc/fstab but itdoesn't work for me. 


Any suggestion ? 


Regards,

---

### Post by dino99 on 2015-08-30
why are you trying to disturb the ubuntu default system settings : 
if mount a partition other than the one booted, ubuntu mount it on /media/youruser/yourmountedpartition
so it will not understand your path

---

### Post by sudodus on 2015-08-30
Welcome to the Ubuntu Forums :-)

I think it is a better idea to mount the second hard disk drive in **/mnt/Lager** and not in a subdirectory in your home partition. If that works, fine. You can use a ***symbolic link*** to get there easily from you home directory

```
ln -s /mnt/Lager /home/sam/Lager
```

---

### Post by samolnes on 2015-08-30
Thank you both for your answers! 

/mnt/Lager works with /etc/fstab 

The symbolic link doesn't work for me. When I run ls -s /mnt/Lager /home/sam/Lager I only get the message:
/home/sam/Lager
total 0 

/mnt/Lager
total 96 
Then it lists all my folders, but /home/sam/Lager is still empty. 

Output of ls -l is: drwxrwxr-x 2 sam sam  4096 aug.  23 22:14 Lager

I am able to mount the disk manually in the terminal. 

Hope you have more suggestions for me :-)

---

### Post by yetimon_64 on 2015-08-30
> When I run ls -s /mnt/Lager /home/sam/Lager I only get the message:
/home/sam/Lager
total 0 .ls lists what you ask it to. You need to use "ln" to link to the directory. Edit: just noted you likely copy/pasted from sudodus' code box :-)

---

### Post by samolnes on 2015-08-30
Now it worked - thank you all for your help ! 

I changed /mnt/Lager to /media/Lager, and used symbolic link to make the folder appear in my home folder. 

Have a nice day :-)

---

