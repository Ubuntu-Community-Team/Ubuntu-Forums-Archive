---
title: "Grrrr... After Lubuntu install!"
date: 2016-05-01
forum: General Help
---

### Post by mnduck on 2016-05-01
When I finally took Win10 of an older Laptop, I took a disk image just incase and backed to "My Docs" as well.  By now most experienced members will have a cold finger running up and down their spines.  

The image worked fine, at least as far as I can tell, but the other backup?  I have a Fine Shiny  New folder very comfortingly called Documents it contains lots and lots of nothing!! !!!

After snivelling for a while and totally failing to find anyone else to blame it on I can manage with out the files but I'd like them back.

Is there anyway of extracting them from the image without rolling it back onto the machine? 

I used the Ienovo utility to make the image :(


Thanks.         Aamcle

---

### Post by Bucky Ball on 2016-05-01
Sorry, but this is not very clear. You now have Lubuntu installed and working fine, you are looking at your backup of your 'Documents' from the Windows install and you see your backed up folder but can't open it? We need details to help.

[LIST]
[*]What happens when you double click the folder?
[*]Is it a regular folder or a .zip or some other compressed folder?
[*]How did you back up you data? (You took a disk image and backed it up to 'My Docs'??? Not sure how that's possible as My Docs is on the disk you're backing up, but have no idea about Windows if that's what you used.)
[*]Is the 'Documents' folder full of nothing on an external or separate drive to your Lubuntu, if you are running it?
[/LIST]

Please confirm and answer all of the above, thanks.

PS: You may want to change your thread title to something that relates to your problem, e.g. 'Problems accessing backed up data' or something similar. Edit first post, Go Advanced.

---

### Post by mnduck on 2016-05-01
Sorry got carried away moaning, its my fault I should have checked by backups property.

When I took W10 off the laptop I made two backups :-

I copied the Documents folder to a pendrive.
And
I used Lenovos utility to create a disk image of the laptops entire HDD again to a pendrive. 

The "Documents"folder on the pendrive is viewable but empty! I should have checked.

That leaves me with the disk image, I don't want to roll it back onto the laptop but I would like to get files out of it. 

It's formatted exFat I can view it and it's component parts but I don't seem to be able retrieve individual files from it.

Any help would be very much appreciated.


Thanks.          aamcle

---

### Post by lisati on 2016-05-01
Did you "safely remove" the pendrive before removing it? If not, it's possible that you lost some of the data.

---

### Post by mnduck on 2016-05-01
The drive seems fine, I think I need some way to mount the image so I can recover files.


Atb.         Aamcle

---

### Post by yancek on 2016-05-01
I don't think there is support for xfat by default.  Take a look at the link below, the second post which tells you which software you need to install to use xfat.  Also, what happens when you try to retrieve files and how are you doing this?

[http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

---

### Post by buzzingrobot on 2016-05-01
Yes, you'll need "exfat-fuse" and "exfat-utils" installed to deal with FAT files and drives.

---

### Post by mnduck on 2016-05-01
Got them that's how I can mount the pendrive, but the won't let me mount the image in such a way that I can retrieve the individual files.


Atb.         Aamcle

---

