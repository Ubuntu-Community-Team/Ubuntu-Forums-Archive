---
title: "HELP! changed system files permissions"
date: 2008-06-15
forum: General Help
---

### Post by jak_sch on 2008-06-15
While changing permissions of some files I made a big, big mistake. I changed the permissions not only of the desired files, but of the folders /bin /boot /etc /dev and the half of /lib (I recognised after a few seconds and aborted by CTRL+c) to 775:

[INDENT]jakob@mir:~/Info/$ sudo chmod -R 775 /*/
chmod: Zugriff auf &#8222;/home/jakob/.gvfs&#8220; nicht möglich: Permission denied[/INDENT]

All folders after /lib seem to be unaffected. By now I can't even perform any sudo-command:

[INDENT]jakob@mir:~/$ sudo chmod 440 /etc/sudoers 
sudo: /etc/sudoers is mode 0775, should be 0440[/INDENT]

In my eyes, I got two problems:
a) Restore the permissions of the folders, which I can do via a Live CD
b) Get to know which permission for which file
For the task b) I had the idea of reading out the ext3-Journal, maybe the changes are written in there. But how can I do this. 
And maybe somebody has a better idea for task a).
I'm running 8.04 on a one-user laptop.

---

### Post by sdennie on 2008-06-15
Doing either is going to be incredibly time consuming, painful and error-prone.  To be honest, unless you re-install, I think the integrity of your system will always be in question.  The quickest way to fix your problem is probably to backup your home directory and /etc and just re-install.

---

### Post by jak_sch on 2008-06-15
Backup is on the way, anyway. I searched the Internet up and down for information about reading out the journal. And I found nothing. 
So another way would be to find out the permissions at a friends computer. Or reinstalling. Both ways will be performed tomorrow (Central european time). 
There is just one more thing: Does Grub work with these permissions? I hadn't turned my Computer off since the failure.

---

### Post by sdennie on 2008-06-15
I think grub will probably still run but, I'm not sure if the system will completely boot with those permissions (at the very least I doubt if X will start).

---

### Post by jak_sch on 2008-06-15
With a Live CD and Windows on another Partition I don't need to start the x-server anymore. But maybe I'll have to start Windows. But that should work also with the live CD.

I'll work on tomorrow. Good night in Europe and have a nice evening in Buenos Aires.

---

