---
title: "Help! I can't access my bookmarks"
date: 2007-08-18
forum: General Help
---

### Post by mad_man on 2007-08-18
I need help accessing my bookmarks in the directory /home/myname/.mozilla. Unfortunately because I was trying to update my display driver so that it recognized my Radeon 9550 I don't have any display at all. As such I'm trying to reformat my hard drive and am trying to get all of my data off before doing so. I'm currently running off of a live CD and for some reason it won't let me open /home/myname/.mozilla so that I can get to my bookmarks! Can anyone help me?

---

### Post by ajgreeny on 2007-08-18
Before you do anything like reinstalling you should try getting your display running again.  Start your installed ubuntu into the command line.  Now login with your username and password and you will get a command prompt username@hostname.
Now type
sudo dpkg-reconfigure xserver-xorg
and one by one go through the questions accepting the default until you get to the graphic card.  Here you need to chose the ati option.  Carry on to the end and then reboot by typing:-
sudo shutdown -r now
That may well solve your problem but if not and you do reformat and reinstall, you need to mount your hard disk with the data on first.
with the live CD running, open a terminal and make a now folder as a mount point with:-
sudo mkdir /media/ubuntu
Now mount the hard disk partition with ubuntu on to that place with:-
sudo mount /dev/hda2 /media/ubuntu -t ext3  (this assumes ubuntu is on hda2, so change it if needed.
Now plug in a usb flash drive, which should automount and you can copy those files you need from /media/ubuntu/home/username on to the flash drive easily.  It's worth copying everything you want to keep, of course, such as the .mozilla,  .mozilla-thunderbird,  .gconf, and all your documents.  In fact if you can copy the whole of the home folder you will be certain to have everything you could possibly want, even if you don't use everything on your new install.

Good luck and I hope this all makes sense.

---

### Post by mad_man on 2007-08-19
Thanks I'll try that

---

### Post by mad_man on 2007-08-19
Umm... There was a problem. It says that I don't have the permissions necessary to access the folder. What do I do now?

---

### Post by ajgreeny on 2007-08-19
Access which folder, and at which point of the activities you're trying to carry out?

---

### Post by mad_man on 2007-08-19
It says that I can't access the .mozilla folder after I had mounted the drive and tried to open it.

---

### Post by ajgreeny on 2007-08-20
Did you try reconfiguring xorg as I suggested?  If it didn't work, in the live CD try the following in a terminal, after mounting your hard disk:-
sudo cp /media/ubuntu/home/username/.mozilla /media/usbdrivefolder/
This should copy the folder from the ubuntu harde disk to the usb drive, unless I have totally got things wrong, which I don't think I have.

---

### Post by mad_man on 2007-08-20
Yes I did try reconfiguring the xorg-xserver. Actually I probably should have mentioned that I had tried that before asking, sorry. Anyway I'll try what you said.

---

### Post by mad_man on 2007-08-23
Hey sorry about not answering for so long but it wouldn't work. Is there anyway to do it in terminal because when my computer loads up without the live CD I can still use command line so I could probably do it that way.

---

### Post by ajgreeny on 2007-08-23
Yes you can do it easily from your cli login with:-
sudo cp -r /.mozilla /media/usbdrivefolder
or if the usb drive is big enough you can copy all your home folder with:-
sudo cp -r /home/username/ /media/usbdrivefolder

You may not even need the sudo so try it without first and see if it works.

---

### Post by mad_man on 2007-08-27
Uh how do I find my usb? Do I need to mount it first? If so how do I do that?

---

### Post by ajgreeny on 2007-08-27
USB drives should normally be automounted.  If not you will need to insert it and then run **sudo fdisk -l** to see what is listed that is not usually there.  That will be your usb drive.

---

### Post by mad_man on 2007-09-24
Uh I'm not sure if your still there, sorry that it has been so long I have been busy copying all that I can and have also been busy with exams and stuff. Anyway when I tried to copy to the usb it did not work and ended up creating a folder in my media drive. For some reason it is not mounting properly. Is there any way I can do it from the live CD? If so that would probably be best if not my friend has suggested something that might fix my system and I  will just have to risk doing so. Again sorry that I took so long.

---

### Post by mad_man on 2007-09-26
Hey me again thanks for all your help, I finally managed to copy the bookmarks file using the knowledge that I picked up while trying to solve the problem. Thanks again.

---

