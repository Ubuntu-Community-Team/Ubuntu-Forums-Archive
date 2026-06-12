---
title: "Amarok does not remember settings?"
date: 2007-03-04
forum: General Help
---

### Post by hardyn on 2007-03-04
im using amarok 1.44 with gnome, and am finding that is does not remember settings.

every launch it behaves as if it were newly installed, it does not remember media directory, or menu options... this suggests that a config file is missing or improper permissions somewhere... what to i have to tweak to make it work correctly?

thanks.

---

### Post by bloodniece on 2007-03-04
you could remove and reinstall, that way any config files mssing or corrupt would be reinstalled. Be sure to purge when you remove so you get all fresh stuff on the reinstall.
I added a regex wildcard just to cover all amarok stuff.

```
 sudo apt-get remove --purge amarok*
```

Then

```
sudo apt-get install amarok
```

---

### Post by hardyn on 2007-03-04
yup.. .still no...

---

### Post by hardyn on 2007-03-04
apparently by default, you dont own /home/$user/.kde and the perms are all jacked up.

you much force ownership and permissions.

/home/$user > sudo chown $user -R .kde

provide permissions to your taste using chmod.

---

### Post by Yellowbelly on 2007-03-04
> **hardyn said:**
> apparently by default, you dont own /home/$user/.kde and the perms are all jacked up.

you much force ownership and permissions.

/home/$user > sudo chown $user -R .kde

provide permissions to your taste using chmod.

What does this mean? I'm having the exact same problem. I'll switch to KDE just to use this program since it's the only decent mp3 player close to on par with itunes.

---

### Post by hardyn on 2007-03-04
i will assume that you understand the unix file permissions...

anyway... you do not have ownership of the .kde directory by default for some reason.  but its pretty easy to fix.

using sudo you have to give your user permission to use your .kde directory.

so if you open your terminal window:

sudo chown $user -R .kde    (where $user is your user name)

you will now have ownership of the directory.
and if you apply

sudo chmod 664 -R .kde

this will allow you read and write acess, your group read and write access and everybody else read access to your .kde directory...

this is going to be easier than switching desktops.

cheers.

---

### Post by Yellowbelly on 2007-03-05
thanks but I started it up today and now like 5 error messages came up. Should I have done this while the program was not running?

---

### Post by hardyn on 2007-03-06
yeah probably, but i dont think it will cause your problems... what are the errors?

---

### Post by Yellowbelly on 2007-03-06
I found your other thread with your errors and they are the exact same errors. I tried running that code through the terminal but it didn't do anything. Even the first time it seemed like it didn't do anything although it asked for my password. I tried reinstalling, then completely removing and reinstalling and nothing worked.

---

### Post by hardyn on 2007-03-06
poke around in nautilus as see what the permissions are set to.

---

### Post by DoorGunner on 2007-03-06
did you settings>Configure Amarok>Collection -=>>SQLITE?

---

### Post by Yellowbelly on 2007-03-06
yeah it was set as SQLite. And how do I poke around nautilus. I've heard of it but have no idea what it does or what to do with it.

---

### Post by hardyn on 2007-03-07
its the gnome equivilent of 'my computer', im sure that you have looked at it.

set the view to 'show hidden files'

find .kde in your /home/$user directory

right-click, properties, permissions

---

### Post by Yellowbelly on 2007-03-07
sweet! thanks dude. it worked.

---

