---
title: "Lubuntu Default Keyring"
date: 2015-07-10
forum: General Help
---

### Post by dennis-shackleton49 on 2015-07-10
Hello, I saw a post about this in the forums, but no solution was officially found. I have the system asking me for a default keyring, but anything I type doesn't work. I have tried seahorse and the system then asks to enter the old default keyring. Is there some way to reset it? Or at least find what the keyring would be? Is there a file or folder holding it somewhere?

I'll add that there IS a solution to get a network established on the forums located here ([http://ubuntuforums.org/showthread.php?t=1454399&highlight=Lubuntu+Default+Keyring](http://ubuntuforums.org/showthread.php?t=1454399&highlight=Lubuntu+Default+Keyring)) but I am still wondering about this password problem as well. I'd like to fix it. The problem also occured after I installed packages from a package manager.

---

### Post by VMC on 2015-07-10
Have you looked into /etc/xdg/autostart? There's several gnome-keyring files. Open with text editor. Look for "X-GNOME-Autostart-Notify=whatever" Is it true or false.
[This may be of help]("http://askubuntu.com/questions/162850/how-to-disable-the-keyring-for-ssh-and-gpg").

Personally I followed mcduck's advice on post#7 [here]("http://ubuntuforums.org/showthread.php?t=1655397&p=10296836#post10296836").

Keyring has always been a thorn. It comes up countless times. Strange, but I have not had keyring issues using Lubuntu, only Xubuntu.
There are several 'hacks' out there. Choose your poison.

---

### Post by dennis-shackleton49 on 2015-07-11
Hey thanks VMC, I appreciate your response. I will check there :)

---

