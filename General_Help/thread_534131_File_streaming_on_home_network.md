---
title: "File streaming on home network"
date: 2007-08-24
forum: General Help
---

### Post by Auax on 2007-08-24
When I used Vista, I could watch a video or listen to music that was saved on one of my other computers with no problem... but with Ubuntu, it has to copy the file first, then it can play it.

Is there a way to fix this so I can stream files again?

The computer I want to view files on is running Kubuntu 7.04, and the computers with all of my videos are running XP Home, and XP Professional.

---

### Post by Auax on 2007-08-25
Help?

---

### Post by fenian on 2007-08-25
How are you downloading the video to the linux box?

---

### Post by Auax on 2007-08-25
Just through remote places, I click on my MSHOME network, and select one of the computers.

---

### Post by fenian on 2007-08-25
First install samba if you haven't already...
> 
sudo apt-get install samba samba-common samba-client smbfs

then create a mount point for the network share...

> cd /media
sudo mkdir winmedia

(you can name the mounpoint something other than winmedia if you want)

Next get the ip address of the windows box, the name of the share, and the username and password of a windows user with permission to access  the share.

Now, edit the file system table (/etc/fstab) file to include it:
> 
sudo gedit /etc/fstab

add the following line...

> //192.168.0.2/myshare /media/win-share cifs username=user,password=pass,users,rw 0 

replace user with the username of the windows user and pass with the password of the windows user.
Save the file exit and reboot.
The shared volume should now be mounted in /media/winmedia and you should be able to use your media player to launch the files from there without downloading them.

---

