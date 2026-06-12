---
title: "Can create folder in a USB but not files"
date: 2018-03-01
forum: General Help
---

### Post by jacortijo on 2018-03-01
Hi,
I am using Ubuntu 17.10 and I am facing a really annoying issue while trying to use a USB stick.

It seems like I can create folders but only folders, no files at all.
I checked the permissions in a terminal and they seem ok.

jose@EliteX:/media/jose$ ll
total 12
drwxr-x---+ 3 root root 4096 mar  1 21:18 ./
drwxr-xr-x  4 root root 4096 jun 16  2017 ../
drwxrwxrwx  1 jose jose 4096 mar  1 21:19 65BC1FB7386C1E9A/

I can create files from the terminal but from nautilus I only have the option to create folders.

Before the usb was getting mounted in /mnt folder but I just delete the folder there and it got mounted in the user home folder which makes more sense to me. 
But in any case, the issue persists....

could you please tell me what is going on? is it a known bug? 

thanks!
J

---

### Post by deadflowr on 2018-03-01
> I can create files from the terminal but from nautilus I only have the option to create folders.
By design.
Bug? Feature?
Depends on what side you're on.

I believe it was decided that the ability to create empty documents seemed like a waste. (to the nautilus devs, that is)
So that was removed.
With the goal of forcing users to use gedit to deal with document creations.

some references and tricks:
[https://askubuntu.com/questions/777711/create-new-document-right-click-option-missing-in-ubuntu-gnome]("https://askubuntu.com/questions/777711/create-new-document-right-click-option-missing-in-ubuntu-gnome")
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1632027]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1632027")
[https://wiki.archlinux.org/index.php/GNOME/Files#Create_an_empty_document_in_Files_3.6_and_above]("https://wiki.archlinux.org/index.php/GNOME/Files#Create_an_empty_document_in_Files_3.6_and_above")

I think, but did not dig for it, that there is a thread in the Ubuntu Development Forums on it.
So do a forum search might bring you some discussions.

---

### Post by ubname on 2018-03-01
> **jacortijo said:**
> Hi,
I am using Ubuntu 17.10 and I am facing a really annoying issue while trying to use a USB stick.



I can create files from the terminal but from nautilus I only have the option to create folders.

...
thanks!
J

I can create file, have you put a file in model folder, then the menu option will be available

---

