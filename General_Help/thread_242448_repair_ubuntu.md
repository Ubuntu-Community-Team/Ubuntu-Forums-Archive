---
title: "repair ubuntu?"
date: 2006-08-23
forum: General Help
---

### Post by shootdamonkey on 2006-08-23
any way of repairing or re-installing ubuntu? as i'm getting weird problems that i cant seem to fix (mostly to do with ubuntu not allowing me to access any admin feature even with the right password, and a problem with metacity)

---

### Post by aysiu on 2006-08-23
To reinstall, just pop in the CD and reboot.

Maybe we should work on solving your other problems, though?

---

### Post by shootdamonkey on 2006-08-24
well to start with everytime the box comes up wanting the admin password, like when changing settings and updating etc, it accepts the password yet does nothing afterwards. It wouldnt accept the password to do the software update, yet i managed to sudo apt-get upgrade and the updates worked fine.

Also i cant change themes because it says that themes maybe missing or a imay have a problem with metacity.

Help appreciated :)

---

### Post by chrisccoulson on 2006-08-24
When performing administrative tasks from GNOME or using sudo, the password you enter is your own password, not the root password.

You have to make sure your user account is on the sudoers list though. If not, you'll need to set this up. To do this, I think you'll need to open a terminal as root, by doing:

```
su -
```

Enter your root password. You are now in the terminal as root. Type:

```
visudo
```

This allows you to edit the sudoers file. In it, you should see a line similar to:

```
%admin         ALL = (ALL) ALL
```

If it isn't there, add it.

Now, you need to make sure that the user account you use normally is in the admin group. I'm at work at the moment, and I can't remember how to do this off the top of my head, but I think it should be something like:

```
usermod -g admin <username>
```

I'm not 100% sure though.

---

### Post by Ramses de Norre on 2006-08-24
He can use sudo so his sudoers file is fine..

What's the output when you type ```
gksudo synaptic
``` in terminal?

---

### Post by chrisccoulson on 2006-08-24
My apologies! I missed that bit

---

