---
title: "[SOLVED] Cannot delete/move to trash files (Hardy)"
date: 2008-04-26
forum: General Help
---

### Post by fullmetalgerbil on 2008-04-26
I cant seem to move to trash or delete files. I keep getting "Unable to trash: permission denied"

---

### Post by rgutierrez on 2008-04-26
I wonder what the permissions of your trash directory are.

```
ls -ld ~/local/share/Trash/files
```

---

### Post by fullmetalgerbil on 2008-04-26
I entered the command and this is what I got:
david@david-desktop:~$ ls -ld ~/local/share/Trash/files
ls: cannot access /home/david/local/share/Trash/files: No such file or directory

---

### Post by fullmetalgerbil on 2008-04-26
I've been having problems all day with bash recognizing commands and /or finding directories. I'm wondering if its a Hardy bug

---

### Post by rgutierrez on 2008-04-26
Is this a new install or an upgrade?

What happens when you try "sudo ls -ld..."

---

### Post by fullmetalgerbil on 2008-04-26
Same thing happens.

---

### Post by rgutierrez on 2008-04-26
Sorry, that should have been:

```
ls -ld ~/.local/share/Trash/files
```

---

### Post by lovecrime on 2008-04-27
> **rgutierrez said:**
> Sorry, that should have been:

```
ls -ld ~/.local/share/Trash/files
```

this solved the problen in the root and home partition
but the other ntfs partitions still have the problem

---

### Post by fullmetalgerbil on 2008-04-27
I ran ls -ld ~/.local/share/Trash/files
And got: drwx------ 2 david david 4096 2008-04-26 23:03 /home/david/.local/share/Trash/files

---

### Post by fullmetalgerbil on 2008-04-27
bump

---

### Post by fullmetalgerbil on 2008-04-27
Screw this new release I'm just reinstalling Gutsy.

---

### Post by fullmetalgerbil on 2008-04-27
Scratch that. I don't want to downgrade quite yet. 
The problem is that I cant delete files. On a lark, I decided to install kubuntu-desktop thinking maybe a different file manager might do the trick. Still no joy.
Anyone have any ideas?:sad:

---

### Post by fullmetalgerbil on 2008-04-27
Ok, since noone was getting back to me I tried: gksu nautilus&
and got: david@david-desktop:~$ gksu nautilus&
[1] 5826
david@david-desktop:~$ Initializing nautilus-share extension

** (nautilus:5827): WARNING **: Unable to add monitor: Not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


However, Nautilus opened and showed Desktop as my only folder under root.
Somehow, I get the feeling that I'm not going to get anywhere with this as I'm just sitting here posting to myself.

---

### Post by Eazy© on 2008-04-27
I had the problem that I could not empty trash. I could delete but not empty as the "empty trash" (translated from Swedish) was grayed out. The problem was that /home/eazy/.kde/share/config/trashrc was owned by root. I simply deleted the file. then I tried to delete a file and I was able to empty it. dunno if that helps you, but it's worth a try.

---

### Post by Dubbayoo on 2008-04-27
I have the same problem after an upgrade. 

[IMG]http://www.dubbayoo.net/files/pics/screenshots/trash.jpg[/IMG]

---

### Post by adlisyahmi on 2008-06-02
yeah, i had the same problem too:(

---

### Post by ironwolfe on 2008-10-27
I just found this thread while searching on google.  I found the way to solve it is to use the trusty old sudo rm -r command -   be careful to type it in exactly as I am providing or you will delete something you don't want to.

```
sudo -r ~/.local/share/Trash/*
```

that should solve your mysterious file deletion problems.

---

### Post by fullmetalgerbil on 2008-10-27
It was ages ago I started this thread. Turned out the problem wasn't with the trash function or directory at all, it was about the permissions on the files I was attempting to send to the trash *doh*. Or at least looking back that must have been it because now I don't have that problem.

---

### Post by alienprdkt on 2008-10-27
> **Dubbayoo said:**
> I have the same problem after an upgrade. 

[IMG]http://www.dubbayoo.net/files/pics/screenshots/trash.jpg[/IMG]

here you go I have your solution :D

#sudo bash
#rm -rf ~/.local/share/Trash/files

(external drive)

#sudo bash
#rm -rf /media/disk/.Trash-1000/files

---

### Post by kri_vijay on 2009-01-12
This post was helpful. I just wanted to add:
To enable thrash function, u need to add a folder
.Thrash-x (x is ur user_id_numerber -- probably 1000) in the topmost folder in the mounted directory.
ie if u mount a partion or an ext3 external drive at /mnt/folder, & /mnt/folder is write protected, u need to add /mnt/folder/.Thrash-x  & make it writable by u.
(do the same for all user or I guess /mnt/folder should be writable to everybody)

Then u should be able to delete files

K

---

