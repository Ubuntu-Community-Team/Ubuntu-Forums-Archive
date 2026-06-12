---
title: "Purging Encfs"
date: 2017-03-10
forum: General Help
---

### Post by Quarkrad on 2017-03-10
Running 16.04.  I have installed encfs, set up a password and all is OK.  Via synaptic I completely remove encfs, or using the terminal **sudo apt-get purge --auto-remove encfs**.  Restart machine and now I am free of encfs.  I install encfs again using **sudo apt-get install encfs** and go through the setup process.   When I get to the point of entering a (new) password I am asked to enter my password (not set up a new one).  If I enter my old password I can use encfs - so purging the original configuration did not delete (I'm assuming) the file that contained my password.  Is it possible to completely get rid of encfs and be able to install it again, using it with a new password?

---

### Post by oldrocker99 on 2017-03-10
You entered your old password in Users and Groups, and you have to enter it twice before you can change your password in the third box. You likely didn't enter the new password.

---

### Post by Quarkrad on 2017-03-10
I'm following this [https://www.howtogeek.com/121737/how-to-encrypt-cloud-storage-on-linux-and-windows-with-encfs/](https://www.howtogeek.com/121737/how-to-encrypt-cloud-storage-on-linux-and-windows-with-encfs/) - sorry, I should have explained a little more in my first post.  Although I using pCloud rather than Dropbox the principle is the same and I have transferred an encrypted file up onto pCloud.  However, I want to start all over again in terms of encfs - to purge it off my PC and start again.  When I followed the url I did not knowingly enter the password in Users and Groups but perhaps that is what happened as part of the set up process.  Where in Users and Groups would I find the encfs password(?) - I've just had a look and there is nothing like encfs.

---

### Post by Quarkrad on 2017-03-11
bump

---

### Post by The Cog on 2017-03-11
Uninstalling the encfs application will not delete your data files and folders. 
If you want to remove your data from dropbox, then remove the data (Dropbox/encrypted according to the linked article).
```
rm -rf ~/Dropbox/encrypted
```

---

### Post by Quarkrad on 2017-03-12
It is not so much removing folders and files I'm worried about - it's the fact that after removing encfs, and reinstalling, my old password is fixed as the encfs password.  I can't get rid of the password used in the first install of encfs.  It is as if there is some configuration file somewhere, containing the original password, that is always present and active when reinstalling encfs.

---

### Post by The Cog on 2017-03-13
There is such a configuration file. It is in ~/Dropbox/encrypted along with all your other encfs files, and probably called .encfs6.xml (the name starts with a dot so you need to enable viewing hidden files).
Uninstalling the application does not rummage through every user's home folder looking for personal encfs configuration files or data to delete.

Actually the config file does not contain the password itself. If the password you provide when you start encfs is able to decrypt the data there, then you gave the correct password. Otherwise you gave the wrong password.

---

