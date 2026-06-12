---
title: "How to write changes to grub.cfg on a live USB?"
date: 2014-07-23
forum: General Help
---

### Post by jj.wauters on 2014-07-23
I liked to make my live USB persistent like described in thread [http://askubuntu.com/questions/375153/usb-live-does-not-save-files-between-sessions](http://askubuntu.com/questions/375153/usb-live-does-not-save-files-between-sessions).
However I cannot save my changes on file /cdrom/boot/grub/grub.cfg and/or modify the file permissions.

How to do ?

---

### Post by grahammechanical on 2014-07-23
Have you installed Ubuntu onto a USB memory stick with persistence? When we install Ubuntu the installer will default to installing grub onto sda. We must make sure that grub is installed on the USB memory stick.

We are not supposed to edit grub.cfg. There are a few other Grub configuration files that we are allowed to edit. After editing one of those files we run this command and a new version of grub.cfg will be written.

```
sudo update-grub
```

To edit system files we need to run the editor as Administrator. And we can only change file permissions if we are running the commands as administrator. What is it you wish to do? This command will open Gedit as administrator.

```
gksudo gedit
```

This command will open the file manager as administrator

```
gksudo nautilus
```

Be careful to make backups of any file you edit.

Regards.

---

### Post by jj.wauters on 2014-07-24
I created a Ubuntu live USB and provided persistence. 
However there seem to be a little bug as the live USB does not remember any changes on it. 
You have to insert the keyword "persistent" in grub.cfg like :
*linux    /casper/vmlinuz.efi **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --*
Unfortunately I tried to do so after booting from the stick. In that case you cannot edit the file or use the chmod command.
Now I accessed from my harddrive, made the change and it's working 

Greetings

[LIST]
[*] 	 		 			):P 		

 	
[/LIST]

---

### Post by jj.wauters on 2014-07-24
I created a Ubuntu live USB and provided persistence. 
However there seem to be a little bug as the live USB does not remember any changes on it. 
You have to insert the keyword "persistent" in grub.cfg like :
*linux    /casper/vmlinuz.efi **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --*
Unfortunately I tried to do so after booting from the stick. In that case you cannot edit the file or use the chmod command.
Now I accessed from my harddrive, made the change and it's working 

Greetings

[LIST]
[*]                           ):P 
[/LIST]

---

