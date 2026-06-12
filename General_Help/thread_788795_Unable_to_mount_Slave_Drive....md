---
title: "Unable to mount Slave Drive..."
date: 2008-05-10
forum: General Help
---

### Post by wes_029 on 2008-05-10
Okay I installed Ubuntu as a stand alone OS on a 320GB drive.  I have another HD as a slave thats an 80GB drive formated in NTFS form.  It has all of my data, media, mp3's, ect...  but it will not allow me to mount the drive.  
I am completely new to Linux OS, Windows, I can answer most anything...  
When I double click the Drive I get an error message saying "Cannot mount volume." 
Wheh I click on details I get the following: 
$LogFile indicates unclean shutdown (0, 0)  Failed to mount '/dev/sdb1':Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g/dev/sdb1/media/jupiter [2] -o force  Or add the option to the relevant row in the /etc/fstab file:  /dev/sdb1/media/jupiter [2] ntfs-3g force 0 0 

I have no idea what that means or where to type those commands.  I do not have Windows installed on this PC to do option 1!  Any help greatly appreciated! 

Wes

---

### Post by wes_029 on 2008-05-10
okay, not too sure what it is that I have done, but now when I try to mount the drive I get an error saying "Cannot Mount Volume." You are not privileged to mount the volume 'Jupiter [2]'. 

Gives no details! 

Thanks in advance for ANY help! 
Wes

---

### Post by logos34 on 2008-05-10
Follow the instructions.  Since you don't have windows, try:

sudo mkdir /media/jupiter

sudo mount -t ntfs-3g /dev/sdb1 /media/jupiter 

OR

sudo mount -t ntfs-3g /dev/sdb1 /media/jupiter -o force

---

