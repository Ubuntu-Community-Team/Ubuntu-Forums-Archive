---
title: "Login as Root"
date: 2007-05-27
forum: General Help
---

### Post by dontgetshocked on 2007-05-27
I am using Kubuntu 7.04 and KDM as the manager and need to login as root at the login screen. How can I add the root user and also other users to the login menu?

---

### Post by dfreer on 2007-05-27
you should never need to login as root at the login screen. ever.
that being said, this is how you do it:
login as regular user
in terminal type:
```
sudo su
```
and enter your password. then:
```
passwd
```
and it'll prompt you to create a new password for the root account.

then you'll need to go to System > Administration > Login Window:
Under the security tab, click "Allow local system administrator login"
That *should* take care of letting you login as root. once again, because it is worth repeating, you should never need to allow root logins, or set the password for root.

As for other users, simply adding a new user will let them login. *confused* if it isn't letting them login, is there a error message? how did you add the new users?

---

### Post by dontgetshocked on 2007-05-27
I am not using GDM so I cant use the Login Window so what do you suggest? It is not in my menu at all.Also, if I try using KUser I get the following error message;

Error Opening  /etc/shadow  for reading 
Then it opens but I cant change anything without another error message.
Error message;
Cannot open file /etc/passwd.bak for editing.

---

### Post by sethmahoney on 2007-05-27
Why do you need to login as root?

---

### Post by dontgetshocked on 2007-05-27
Well, I find it easier to find the files I need such as copying a file to a folder which doesnt show up using Konqueror. I wanted to find the folder Windows and copy a dll file to the system folder and i cant find the thing logged as me. Maybe it's my lack of knowledge of using the file manager but I dont how to get done what I want without logging in as root, I am used to the file manager in OpenSuse which is so much easier.How can I open the file maneger and acces all the folders on my drive and copy the file (s) I need as me without being root?

---

### Post by dfreer on 2007-05-27
> **dontgetshocked said:**
> I am not using GDM so I cant use the Login Window so what do you suggest? It is not in my menu at all.Also, if I try using KUser I get the following error message;

Error Opening  /etc/shadow  for reading 
Then it opens but I cant change anything without another error message.
Error message;
Cannot open file /etc/passwd.bak for editing.

Hmmm, I thought login window was in both KDE and gnome... well, sorry, can't quite help you with that part. I know in gnome you can also edit the /etc/gdm/gdm.conf-custom file, perhaps there is a /etc/kdm/ directory? then again, kde never puts it's config files in logical locations so I dunno.

EDIT: The above error looks like a permissions error. did you run KUser as root?

---

### Post by dfreer on 2007-05-27
> **dontgetshocked said:**
> Well, I find it easier to find the files I need such as copying a file to a folder which doesnt show up using Konqueror. I wanted to find the folder Windows and copy a dll file to the system folder and i cant find the thing logged as me. Maybe it's my lack of knowledge of using the file manager but I dont how to get done what I want without logging in as root, I am used to the file manager in OpenSuse which is so much easier.How can I open the file maneger and acces all the folders on my drive and copy the file (s) I need as me without being root?

In gnome you could launch the file manager nautilus with a 
```
sudo nautilus
``` 
In kde.... I'm guessing sudo konqueror?

---

### Post by sethmahoney on 2007-05-27
> **dfreer said:**
> 
```
sudo nautilus
``` 
In kde.... I'm guessing sudo konqueror?

This will launch the file manager as "root".  You can also try launching the file manager (in Gnome - I'm not terribly familiar with KDE) by clicking on Places, then Computer, then doubleclick on Filesystem.  This will get you into / and from there you can go wherever you want.  You'll only be able to edit files if you do it dfreer's way though.  But what are you trying to do that requires that you muck in the filesystem?  There may be an easier way.

---

### Post by rillip on 2007-05-27
Try following the instructions here:

[http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse](http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse)

It is a page for SuSE, but KDE is KDE, should still work.

Edit: of course, with the provisio you really shouldn't :p

If the file doesn't show up in conquerer, is it a hidden file?    Try going to view -> show hidden files

---

### Post by pbw on 2007-05-27
Sure.. you can also just add a service menu to konqueror for it. example: [http://kde-apps.org/content/show.php/Root+Actions+Servicemenu+(for+Kubuntu)?content=48411](http://kde-apps.org/content/show.php/Root+Actions+Servicemenu+(for+Kubuntu)?content=48411) or [http://kde-apps.org/content/show.php/Root+(su)+Konqueror?content=41801](http://kde-apps.org/content/show.php/Root+(su)+Konqueror?content=41801) .

If you still would rather login as root than create or take a peek at kde-apps for various service menus that fill your need. Then all you have to do is go in kcontrol --> system administration. and from there it's pretty self explanatory.

-- pbw

---

### Post by dfreer on 2007-05-27
> **rillip said:**
> Try following the instructions here:

[http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse](http://kim.biyn.com/Linux/How_to_enable_root_logins_in_kde_on_suse)

It is a page for SuSE, but KDE is KDE, should still work.

From link:
> Fortunately this is an easy fix. You will need to restart your XWindow environment for this change to take effect so make sure you save your work before continuing.

1. Open the file /opt/kde3/share/config/kdm/kdmrc
2. Look for a line containing the text to "AllowRootLogin" - depending on the distribution you run you may find that the line is either commented out (has a # to the left) or it is set to false.

This line must be uncommented and must not be set to false. The line is located somewhere around line 246. See the following example:

# Allow root logins?
# Default is true
AllowRootLogin=true

In this example, the setting is not commented out (the two lines previous to AllowRootLogin are) and it is set to true, enabling root to log in. Save the file after making the change and then restart your Xwindow environment.

Seriously, wtf is with KDE and the location of it's config files!!?! lol oh well

---

### Post by pbw on 2007-05-27
kde isnt stored in /opt in ubuntu as stated in the quote, maybe that's why it sounds weird.

As for the location of configs.. it's pretty straightforward. kdm config is in /etc/kde3/kdm

User configuration in ~/.kde/share/apps and ~/.kde/share/config/ . Doesn't sound that confusing or weird to me. Sounds pretty organized *shrug*

---

### Post by aysiu on 2007-05-27
One or both of these links will solve your problem.
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by dfreer on 2007-05-27
> **pbw said:**
> kde isnt stored in /opt in ubuntu as stated in the quote, maybe that's why it sounds weird.

As for the location of configs.. it's pretty straightforward. kdm config is in /etc/kde3/kdm

User configuration in ~/.kde/share/apps and ~/.kde/share/config/ . Doesn't sound that confusing or weird to me. Sounds pretty organized *shrug*

ok, that's better. most of the stuff I'd seen had locations like /opt/, so maybe I just haven't used KDE for awhile. good to know :D

---

