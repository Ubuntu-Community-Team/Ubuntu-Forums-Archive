---
title: "Login Problems"
date: 2014-08-09
forum: General Help
---

### Post by richwein on 2014-08-09
I am running Lubuntu, recently upgraded to version 14, my main user home directory is using the ubuntu encryption

I can not log into my main username.  The last thing I did before this failure was try to add an environment variable to the end of my user " .profile " file, then logged off and can not log on again.  If I enter a wrong password, the login dialog reports that I entered an incorrect password, however when I enter the correct password for my login, the screen blanks for a second as though it is logging me in, then brings up the user login/password dialog again.  Did the desktop crash ?

I have another login, but I had never entered that login to sudoers list.  So, I can not sudo from my second login identity.  I do have the super user password -- is there away to get into super user from a non sudoer login ?

Before I go to my backup is there any troubleshooting I can do ?

It almost appears to me that my main login knows my password, but something in the desktop does not want to run or crashes, but I get no messages at all.

Thanks for any help.

---

### Post by Impavidus on 2014-08-09
Yes, I think your desktop crashes as soon as you login. Try switching to the console (ctrl+alt+F2) and login there. You problem was probably caused by the changes to your .profile. Undo the changes using the command line. Use the nano or vim text editor or restore a backup. Return to the graphical login with ctrl+alt+F7. Try if that fixed it.

---

### Post by richwein on 2014-08-10
Thank you Impavidus.  

I did not know about ctrl+alt+F2 and ctrl+alt+F7 .  It was simple to restore the .profile to the backup version after getting to the command line.

---

