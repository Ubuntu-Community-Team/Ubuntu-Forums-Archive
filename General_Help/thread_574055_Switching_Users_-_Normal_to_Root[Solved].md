---
title: "Switching Users - Normal to Root[Solved]"
date: 2007-10-12
forum: General Help
---

### Post by mooseweb on 2007-10-12
Can someone please help me figure out how to change users from a normal user to the root admin. I made the normal user NOT have admin privileges and I need to switch back to the root admin to give that user privileges. This is what I am doing.

System > Quit... > Log Out

I type the username as root and the password. But it gives me a error saying the following:
Root admin cannot login from this screen.

---

### Post by Namtabmai on 2007-10-12
Yeah root isn't allow to login into a X session by default. You can fix this by going to System->Login Window->Security and selecting Allow local system administrator to login... but you'll probably need admin privileges for that.

The easier way would probably be to swap to a console (Control+Alt + F1) log in as root there and make the change, then switch back to the X window (Control+Alt + F7) and log out. You'll also need to restart X in order for the new permissions to take effect so Control+Alt+Backspace at the login screen.

---

### Post by dabl on 2007-10-12
> **mooseweb said:**
> I made the normal user NOT have admin privileges 

What does this mean -- what did you do?  *buntu default installation process automatically sets up the "installing user" as a user who has the ability to assume, via the *sudo* prefix and its GUI counterparts *gksu* (for Gnome desktop) and *kdesu* (for KDE desktop), the power of the "Super User" aka "root user" aka "system administrator", _when needed_.

So, supposing Mr. User needs to run Nautilus with root privileges -- the command is ```
gksu nautilus
```

and that's it -- you're good to go.  For command line operations, you just ```
sudo mount
``` or ```
sudo apt-get install
``` or whatever.  :)

---

### Post by mooseweb on 2007-10-12
> **Namtabmai said:**
> Yeah root isn't allow to login into a X session by default. You can fix this by going to System->Login Window->Security and selecting Allow local system administrator to login... but you'll probably need admin privileges for that.

The easier way would probably be to swap to a console (Control+Alt + F1) log in as root there and make the change, then switch back to the X window (Control+Alt + F7) and log out. You'll also need to restart X in order for the new permissions to take effect so Control+Alt+Backspace at the login screen.

Ok, so what command do I need to enter? I got to the login screen, but now what?
*New to linux and GNONE, etc...

---

### Post by dabl on 2007-10-12
> **mooseweb said:**
> Ok, so what command do I need to enter? I got to the login screen, but now what?

```

sudo su
```

The prompt will change to a "#".  :)

---

### Post by mooseweb on 2007-10-12
Ok so once the prompt comes up, I just change the number? So this is like 1 = On and 2 = Off?

*Sorry I just want to make sure I get this 100% perfect, for work so if I screw up, I really screw up.

---

### Post by Namtabmai on 2007-10-12
> **mooseweb said:**
> Ok so once the prompt comes up, I just change the number? So this is like 1 = On and 2 = Off?

*Sorry I just want to make sure I get this 100% perfect, for work so if I screw up, I really screw up.

Well it depends on what you mean by your user not having admin access, I can only guess that means you didn't make him part of the admin group (which will allow him to sudo/su).

First check
```

groups <username>

```
Will list all the groups <username> belongs to.
For me this is;
```

groups andrew
andrew : andrew adm dialout cdrom floppy audio dip www-data video plugdev users scanner netdev lpadmin powerdev admin mythtv

```

So for you, you'll probably want to add your users to the admin group
```

gpasswd -a <username> admin

```

---

### Post by ShadowDeath on 2007-10-12
Well if you want to enter as a root there is a simple way to do it via terminal...

Open a terminal and simple type

```
su root
```

it will ask you for the root password... type it and you are now the root...

but be carefull using the root account... :)

---

### Post by Namtabmai on 2007-10-12
> **ShadowDeath said:**
> Well if you want to enter as a root there is a simple way to do it via terminal...

Open a terminal and simple type

```
su root
```

it will ask you for the root password... type it and you are now the root...

but be carefull using the root account... :)

Of course that only work if the user is a member of the admin group, which from the sounds of it the user has been removed from.

---

### Post by mooseweb on 2007-10-12
Got it to work, thanks guys.

@Namtabmai:
No, shadow was right because you run that inside terminal, then type in the

```
gpasswd -a <username> admin
```

That will add you to the group

---

### Post by Sef on 2007-10-12
[Root/Sudo]("https://help.ubuntu.com/community/RootSudo") explains the idea of using sudo instead of root.   Which way you go is up to you.

---

