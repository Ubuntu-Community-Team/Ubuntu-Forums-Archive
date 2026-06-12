---
title: "Change to a simpler password"
date: 2022-11-26
forum: General Help
---

### Post by otyugh on 2022-11-26
Hey,
today I wanted to set a simpler password (Ubuntu 20.04), but I couldn't because the GUI didn't allow me to. So instead I used the console and used "sudo password username" ; but at the connection, it asks me still my old password.
It means there is another mechanism handling session passwords ; here is my question : how can I change it to accept any password I want or disable it altogether  ?

---

### Post by deadflowr on 2022-11-26
As far as i remember (which is probably not well) you need to edit a pam file if you want a simpler password, as it sets a minimum password length.
I don't know how relevant this is any more but might be what you want:
[https://ubuntuhandbook.org/index.php/2015/06/minimum-password-length-ubuntu/]("https://ubuntuhandbook.org/index.php/2015/06/minimum-password-length-ubuntu/")

Fwiw, disabling a password disables the user so don't do that.

Also
> So instead I used the console and used "sudo password username" ; but at the connection, it asks me still my old password.
What do you mean by that?
You need to logout and back in again or reboot so the system reloads it's settings in order for the changes to take affect.
But I don't know if that's what you mean by connection.

Changes also require that the system is writable,
if somehow stuck in read-only the changes will eventually disappear.

---

### Post by otyugh on 2022-11-26
I don't mean disabling the password, I just want a trivial one (like one letter). I find it stupid to have a complicated one when starting as boot from grub when the drive isn't encrypted is *really* trivial.

> You need to logout and back in again or reboot so the system reloads it's settings in order for the changes to take affect.
Since when ? Password are supposed to be stored in /etc/passwd and are updated system-wise, if it wasn't for another piece of software partaking, right ?

---

### Post by deadflowr on 2022-11-26
> Since when ? 
[s]Not sure how long, but it's been this way for as long as I've run linux.
Maybe things were different 15 or 20 years ago, but that's beyond my own historical usage.[/s]

Nevermind, I was thinking of groups and whatnot, not passwords.


> Password are supposed to be stored in /etc/passwd and are updated system-wise,
No passwords are stored in /etc/passwd.
Passwords are stored in the root-only readable shadow file.
/etc/passwd contains the globally readable user information list of the system.

---

### Post by otyugh on 2022-11-26
> No passwords are stored in /etc/passwd.
Oh, yes my bad, should have checked, bad memories, bad.

---

