---
title: "usbdisks - way too many in Nautilus"
date: 2007-04-05
forum: General Help
---

### Post by dannemil on 2007-04-05
Could someone help me get rid of all of these usbdisks that keep showing up in Nautilus (please see the attached screenshot). It would not be so bad if they just got listed in the file tree, but peridodically Nautilus pops open another window and adds another one of the usbdisks. This is very annoying when I am in the middle of working on something to have these Nautilus windows popping up as it adds to the list of mounted usbdisks under /media

I really only have one usb external hard drive that I want mounted, as well as being able to detect a usb key drive when I plug that in occasionally. Somehow I have managed to get a list of around 15 (count 'em) usbdisks showing up in Nautilus.

Any help would be appreciated.


Jim

---

### Post by fdrake on 2007-04-05
wow .. i'd like to have so many usb ports like you do..   :)


terminal:

sudo nano /etc/fstab

(copy and paste here the results)

---

### Post by fdrake on 2007-04-05
... never mind, did you actually try to delete the uneccessary usb folders?? 
sudo rm -r <foldername>

---

### Post by chrisccoulson on 2007-04-05
^^ It may be worth making sure the USB device isn't mounted in any of the folders before doing that though.

---

### Post by dannemil on 2007-04-05
many thanks - I just removed them using sudo rm -r, rebooted, and the problem appears to be solved. Now if I could only figure out how I got them there in the first place:)

---

