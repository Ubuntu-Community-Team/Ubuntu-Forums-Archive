---
title: "Install application from cdrom?"
date: 2007-08-29
forum: General Help
---

### Post by jefft113 on 2007-08-29
Hey, I am trying to install stata 10(a statistics program), I need to install it from the terminal but I dont know the path to the cd-rom, Anyone got a clue?

---

### Post by logos34 on 2007-08-29
try 

/media/cdrom0/...

---

### Post by jefft113 on 2007-08-29
All I get is bash: command not found. I am doing this in a directory I had to create to hold the program so I dont know if that is making a difference but I dont think it would be a problem.

---

### Post by logos34 on 2007-08-29
try it from /home/user dir
[B]
cd[/B]

---

### Post by jefft113 on 2007-08-29
Ok, sorry, I meant:

if i type:     /media/cdrom     i get     bash:    is a directory                    which is expected

when i type  /media/cdrom/install       which is the file i need it to grab and install      it says no file or directory

---

### Post by logos34 on 2007-08-30
sorry for the delay.

You'd better tell us exactly what program on what cd this is, and copy and paste the commands you're entering in the terminal so I or someone else can help you better.  Cd's usually mount at /media/cdrom**0** or /media/cdrom**1** if it's a second drive. 

If you're simply trying to copy a folder 'install' and all its subdirectories to a folder in your home dir or desktop, it would be somehting like this (use absolute paths):

cp -r /media/cdrom0/install /home/<user>/<whateverfolder>

---

### Post by jefft113 on 2007-08-30
I cant do that, Ill have to try again later, I accidentally deleted the wrong directory and now, the computer wont boot correctly, so i need to reinstall feisty and try it again. thanks for the help.

---

### Post by jkim9722 on 2007-09-01
try this
# umount /media/cdrom0
# sudo mount -o exec -t iso9660 /dev/cdrom /media/cdrom0
# sudo /media/cdrom0/install

And follow instructions appearing.

G.L.

---

### Post by s26c.sayan on 2007-09-01
Check your /etc/fstab file to know where your CD is mounted!

---

