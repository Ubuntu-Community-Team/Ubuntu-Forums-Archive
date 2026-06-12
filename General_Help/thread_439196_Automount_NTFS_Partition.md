---
title: "Automount NTFS Partition"
date: 2007-05-10
forum: General Help
---

### Post by nuahs on 2007-05-10
I am fairly new to the whole Linux scene. Only been using it for about a week now, tried Fedora Core 6 for a while, and figured I would switch to Ubuntu and give it a shot for a while now :D

There are a couple things I'm having issues with so I'll start with my first one and start working down my list ;)

First issues to solve, probably something simple but, I can' figure it out; search didn't get the results I wanted. I have Ubuntu installed on a SATA drive and I also have two windows NTFS partitions on this drive that I would like to retreive some files from now and then. If I got to 'computer' from within Ubuntu the drives show up in there fine and when I double click them it ask for my root password then I can access them and I have the shortcuts on the desktop.

Now when I restart the shortcuts are gone from the desktop? I have to go to 'computer' again and enter my root password to get them to mount again. Is there a way to automate this proccess so when I log-in the drives are automatically mounted?

That's all I need for now! Will be asking some more questions once I get this small hiccup solved ;)

Thanks in advance!

---

### Post by rygar on 2007-05-10
just did this for myself...

for starters, i have ntfs-3g installed to enable write access to ntfs drives (by default, ubuntu will only allow read access).  to install this, go to add/remove programs, type in ntfs, and install the "NTFS Configuration tool".  there is a GUI config under Applications -> System Tools in gnome.

next, unmount the drives you want to automount. (sudo umount /media/drive)
then make a directory for the mount (sudo mkdir /media/drive)

next, modify your fstab file:  gksudo gedit /etc/fstab

add a line at the bottom for whatever you want automounted.  for instance, i added:

/dev/sda1 /media/XP ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5 /media/Vista ntfs-3g defaults,locale=en_US.utf8 0 0

i suppose if you don't have ntfs-3g installed, just change it to ntfs.

if you want to test it, you can unmount your drives and reload fstab:

sudo umount /media/drive
sudo mount -a

....or just restart your computer.  either way, whatever desktop icons you create will be restored on startup!

---

### Post by strabes on 2007-05-10
To find out the /dev locations of your windows drives just run this command in a [terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
``` If you're lost just paste the output of that command in this thread and someone will tell you what to do.

---

### Post by nuahs on 2007-05-11
Thanks guys!! Going to try now and see what I get :D

---

### Post by nuahs on 2007-05-11
Worked like a charm! Thanks rygar ;)

Now if I could only figure out how to mount my windows raid0 partition? fdisk does not recognize them it appears...

---

### Post by Gonzalo_VC on 2008-05-18
> **rygar said:**
> just did this for myself...
for starters, i have ntfs-3g installed to enable write access to ntfs drives (by default, ubuntu will only allow read access).  to install this, go to add/remove programs, type in ntfs, and install the "NTFS Configuration tool".  there is a GUI config under Applications -> System Tools in gnome.
next, unmount the drives you want to automount. (sudo umount /media/drive)
then make a directory for the mount (sudo mkdir /media/drive)
next, modify your fstab file:  gksudo gedit /etc/fstab
add a line at the bottom for whatever you want automounted.  for instance, i added:

/dev/sda1 /media/XP ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5 /media/Vista ntfs-3g defaults,locale=en_US.utf8 0 0



[COLOR="Navy"]I also found this: [http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU)
"To automount the same drive you would have to edit your /etc/fstab file and add the entry;
/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0"
but in my case didn't work :(

I hope Ubuntu gets a script to easily automount drives, offering this in a menu when clicking with your right mouse button. Other distros do!
[/COLOR]

---

