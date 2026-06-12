---
title: "simple one!"
date: 2008-05-24
forum: General Help
---

### Post by Kaneda187 on 2008-05-24
Here we go again... another noob question, i get a password prompt everytime i boot for wireless access with this msg:

The application 'nm-applet' (/usr/bin/nm-applet) wants to access to the default keyring, but its locked

it only started appearing since i changed my password.... how do i make it go away?:confused:

---

### Post by ibuclaw on 2008-05-24
There is good [howto thread here]("http://ubuntuforums.org/showthread.php?t=192281&highlight=libpam-keyring") about the matter.

It fixed my Debian Etch box, so it will fix Ubuntu right up too!

[EDIT]
Only take note at this part:
> 
Now, you will need to edit one file. I use vi, but if you are more comfortable with a graphical editor you can enter the following:

```
sudo gedit /etc/pam.d/gdm
```

add the following two lines to the end of the file:

```

auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

```
Now you can reboot and it should not ask you for your keyring password to log onto your encrypted wireless network


Regards
Iain

---

### Post by ibuclaw on 2008-05-24
If you are still getting problems.
Try deleting your keyring altogether...

Press **Alt+F2** and type in:
```
nautilus ~/.gnome2/keyrings
```

Then remove or rename the "login.keyring" file.

Logout/Login, Disable/Re-Enable the Wireless Connectivity in nm-applet and enter your WPA/WEP password key, followed by your new keyring.

Should stop bugging you from now on.

Regards
Iain

---

### Post by Kaneda187 on 2008-05-24
Got it thanks!! 

just gotta say its the helpful people like you and others that make this forum great keep up the good work!

---

