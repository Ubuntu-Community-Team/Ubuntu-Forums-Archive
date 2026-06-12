---
title: "Hi I need some help about my hard drive running xubuntu?"
date: 2014-10-18
forum: General Help
---

### Post by andreadixon825 on 2014-10-18
Hi, have a hard drive and it has data that I need to use and get off of it was formated in windows 7 and  xubuntu is not seeing it, what way can I do to xubuntu to show that hard drive. Thank you for letting me post.  :)

Oh and I downloaded GParted and it shows it but I cant access it?

---

### Post by O9aIevckc0 on 2014-10-18
is it an internel drive (inside your computer) or an externel hard drive e.g. a usb drive 
and what file system does it use?
if it has a ntfs filesystem installing ntfs-3g and rebooting may help

you can install it with this command using the terminal
apt-get install ntfs-3g

(if this works please mark this thread as solved)

---

### Post by O9aIevckc0 on 2014-10-18
when you say you cant acess it do you mean you get an error or a permission denied ?

could you post the output of 

sudo lsblk -f

while the disk is attached

---

### Post by andreadixon825 on 2014-10-18
Hi, thanks for the reply. I did just like you said and it works now thank you so much :)

---

