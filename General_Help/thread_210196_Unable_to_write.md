---
title: "Unable to write"
date: 2006-07-06
forum: General Help
---

### Post by Skia_42 on 2006-07-06
Hello, I have been trying to copy folders files onto my iPod manually through the terminal using the "mv" and "cp" commands. When I perform these commands as root I am told that it is a read only file system. When I view the flie system that I am trying to write to (/media/ipod) I see that root is the owner and that it has all privledges. How do I write to this file system?

> 
skye@ubuntu:~$ cd Desktop
skye@ubuntu:~/Desktop$ sudo su
root@ubuntu:/home/skye/Desktop# mv Desktop /media/ipod
mv: cannot create directory `/media/ipod/Desktop': Read-only file system
root@ubuntu:/home/skye/Desktop# mv small_clone_2.MP3 /media/ipod
mv: cannot create regular file `/media/ipod/small_clone_2.MP3': Read-only file system
root@ubuntu:/home/skye/Desktop# cp  Desktop /media/ipod
cp: omitting directory `Desktop'
root@ubuntu:/home/skye/Desktop# cp  small_clone_2.MP3 /media/ipod
cp: cannot create regular file `/media/ipod/small_clone_2.MP3': Read-only file system


---

### Post by adwait on 2006-07-06
I don't think you can just transfer files like that to the ipod..not sure though. As far as I know u need to go through some interface...

---

### Post by sbassett on 2006-07-06
You should be able to drop files into the ipod (you can utilize notes and calendars this way). Make sure you check synaptic, apt-get or aptitude and have the libgpod packages intalled. I would also eject the ipod, reboot the machine and log in with your normal account, then plug the ipod back in.
Please let us know how this turns out.

---

### Post by IYY on 2006-07-06
When the iPod is automatically mounted, I think it's done as read only. A command like this should work...

mount -t vfat /dev/sda2 /media/ipod

/media/ipod is your mount directory
/dev/sda2 is your ipod (it could be sda or sda1, or even something else)
vfat is the filesystem on the ipod

---

### Post by Skia_42 on 2006-07-06
sbassett: I already have libgpod installed so that is not the problem. Thanks though.

IYY: My iPod is mac formatted. The command you gave me did not work but I am assuming the command is not the same for macs. The mount directory is correct. I found 5 special device blocks (sda, sda1, sda2, sda3, sda4) any idea as to how I can find out which one is my iPod? I am not sure if vfat is the filesystem. (is vfat fat32 formatting?)

---

