---
title: "jpg file association"
date: 2008-01-31
forum: General Help
---

### Post by tbzep on 2008-01-31
I've been having some file association troubles.  I found the solution for most of of it.  It seems that installing gDesklets messed things up, but I found some code that fixed most of the problems.  

My .jpg images are now associated with the correct software, but they won't open with a double click, nor witll the thumbnails show up until I've right clicked on them to look at the properties.  I get a warning when I double click.  I can right click and open them by choosing a program, but they still won't open with a double click afterward.  When I check the properties, they are associated with Image Viewer just like the .bmp's and other formats which are all working just fine.  

> The filename "dec_1024.jpg" indicates that this file is of type "jpg document". The contents of the file indicate that the file is of type "JPEG image". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "JPEG image", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

Edit:  After looking around the drive some more, I've found that PDF files are being treated the same way.  I can open them with "open with", but I get the same warning message as I got with the jpg files.

---

### Post by tbzep on 2008-01-31
I've tried this solution found elsewhere on the forum:


reinstall  packages:
gnome-mime-data
shared-mime-info
mime-support 

then ran code in terminal:

sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus

reboot.....no joy.  I am still having the same issue.

---

### Post by tbzep on 2008-02-01
Sorry to bump, but am I limited to reinstalling Gutsy?

---

### Post by tbzep on 2008-02-02
New info on the problem.

I created a new user account.  In that account, the file associations work.  I can click on a jpg or pdf and it opens.   However, it still isn't showing thumbnails of every jpg file in the new user account.  This seems random because I have folders all downloaded off the camera at the same time and all were processed by the same Nikon software at the same time, but only part of them are showing thumbnails.  

What can I change, reload, replace in my original user account to help remedy the file association problem on the original user account without having to resort to killing it off and setting up everything all over again in the new user account?

---

### Post by stani on 2008-02-02
> **tbzep said:**
> However, it still isn't showing thumbnails of every jpg file in the new user account.  This seems random because I have folders all downloaded off the camera at the same time and all were processed by the same Nikon software at the same time, but only part of them are showing thumbnails.  
Probably because some have bigger file size. Did you try to put a bigger value at  "Edit>Preferences>Preview>Only for files smaller than" in Nautilus?

Stani

---

### Post by tbzep on 2008-02-05
> **stani said:**
> Probably because some have bigger file size. Did you try to put a bigger value at  "Edit>Preferences>Preview>Only for files smaller than" in Nautilus?

Stani

That took care of the new account's thumbnails.  Thanks.  I didn't realize that you could limit thumbnails by filesize.  

My original account still has the same major issues noted in the original posts, however.

---

