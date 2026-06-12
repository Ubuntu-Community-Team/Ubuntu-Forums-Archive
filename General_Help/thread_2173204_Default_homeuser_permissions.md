---
title: "Default /home/user permissions"
date: 2013-09-08
forum: General Help
---

### Post by bewareofthephog on 2013-09-08
I jacked up my /home/user permissions, I had to chmod -R 777 the entire folder to get everything working again.  Does anyone know what the default permissions are or if there is a tool that'll reset them?

---

### Post by deadflowr on 2013-09-08
The default is usually 755, but you can set it as 700 if you like.
As long as the owner(you) has full rights, it'll be okay.
Otherwise you'd need to be sudo'd to make changes.

---

### Post by bewareofthephog on 2013-09-08
Thanks!  I was having problems with mediatomb seeing Music, Photos, and Videos and I made one of those 2AM terminal changes where right after you go "NOOOOOOOOOOOOOOOOOO!".  I ctrl+c'd as fast as I could but I think my SSD is a little faster than my fingers could move and the damage was done :(

---

### Post by Impavidus on 2013-09-08
That is 775 for the directories, the files have 664. The middle digit doesn't really matter as by default you're the only member of your group.

---

### Post by oldfred on 2013-09-08
This will do it in one command. But always becareful as the -R is recursion and that also changes all lower level files also, so not use on system partitions other than /home.

 chmod -R a+rwX,o-w /home/$USER
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

But you may need a couple of files corrected separately if you have issues.

   .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

---

