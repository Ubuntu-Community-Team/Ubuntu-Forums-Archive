---
title: "Mounting iso file"
date: 2006-11-22
forum: General Help
---

### Post by Jonas_Henricsson on 2006-11-22
I'm trying to run a program, a chinese learning tool, which is made for Windows and Mac. I was able to install the program, and the program seems to run nicely. However the program can't find the lessons which are located in an .iso file. This is exactly what happens in Windows if I don't mount the .iso file. 
I mounted the file in ubuntu using:

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop

I can see the mounted .iso on my desktop. However the program still does not find the lessons. Any ideas what the problem might be?

I've also tried "xine dvd://media/iso".

Thanks in advance!

/Jonas

---

### Post by mayonaise15 on 2006-11-22
Sounds to me like you are running the program with wine?

if so:

hit Alt+F2 and type winecfg into the box and hit run.
Go to the Drives tab, type /media/iso into the box, and click add.
Apply the settings before you close it.

Best of luck

---

### Post by Jonas_Henricsson on 2006-11-23
Tried it, didn't work. Any other ideas?

How can I tell for sure if I use wine to run the program?

Thanks for any help!

/Jonas

---

