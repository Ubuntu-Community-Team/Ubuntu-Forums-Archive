---
title: "File Owner Issue"
date: 2006-09-29
forum: General Help
---

### Post by storeman on 2006-09-29
I am very new to ubuntu and Linux so bear with me. I have an openoffice file that I want to edit. Here's what happens.
I navigate to the file (/etc/openoffice/sofficerc) and open it and make the changes. So far, so good. Now, when I try to save the file, I get a message that says, 'You do not have the permissions necessary to save the file.' I am the only user on the system so as I understand it, I should have full administrative rights. Evidently I am missing something. I have searched a bit and have seen some information on using SUDO to change file ownership but even doing that, I get an error message that says the activity is not permitted. I am at a loss. Please help.

Thx

I am very familiar with Openoffice files in the Windows environment.

---

### Post by whizbaby on 2006-09-29
First of all I think you should do (simply open a terminal)
ls -la .open<TAB>  (hit the tab key)
it will auto-complet to something similar to
ls -la .openoffice.org2/

This is your user configuration directory in which you are allowed to change anything you want (search in there) which will override default settings. Changing in /etc/ would mean to change it for the whole system. In this case it's not bad but in other cases it can be, so get the habit to change user-related settings in your homedir (so if something is broken you only need to remove a file which will be regenerated with default values at next start of OO).

If you still want to do it use sudo this way to edit 
sudo nano /etc/openoffice/sofficerc
(nano or any other editor)
this should allow you to save changes.

---

### Post by FuzZy2006 on 2006-09-29
well - linux uses file permissions. this way, only the root can write to some files. that folder is a system folder, and the computer by default doesn't let you write in it. if writing to that file wouldn't damage the pc (if it isn't a config file), in the terminal you might type : ```
/etc/openoffice/
```
then ```
sudo chmod a+w sofficerc
``` 
sudo gives you administrator rights (it should request a pass)
chmod changes the file permissions
a+w = all the users gain write permissions
Now you might be able to write to it. Another way to do is is to open it from the terminal by typing ```
sudo openoffice /etc/openoffice/sofficerc
``` - this will open the file without changing the file permissions

---

### Post by storeman on 2006-09-29
Thanks for the help. Both techniques worked.

Storeman

---

