---
title: "I'm kinda new to Linux so...."
date: 2008-06-26
forum: General Help
---

### Post by NewToLinux123 on 2008-06-26
Hello I just got Ubuntu Like a week ago so I've learned lots already about Ubuntu and Linux but I have one problem I can only login to Failsafe Gnome and not the regular one so I really don't know what to do if anyone can give me some info in how to fix this I will be very happy thanks..

---

### Post by jualin on 2008-06-26
During the login window click on options and then change the session to Gnome, and not Gnome Failsafe.

---

### Post by NewToLinux123 on 2008-06-26
> **jualin said:**
> During the login window click on options and then change the session to Gnome, and not Gnome Failsafe.

Yeah I have tried that and the other sessions too but what it does is it tries to go into it but goes right back to the login screen if that makes any sense so there might be another explanation as to why it does this to me.

---

### Post by jualin on 2008-06-26
I thought you meant Recovery Mode for some reason. I don't know why this is happening to you maybe you should check the kernel messages when you log in.

---

### Post by jualin on 2008-06-26
How about trying to reinstall the ubuntu-desktop package. This should install gnome again and may fix your problem. Now that's the Windows way of thinking. Maybe one of the people from the forum have a better idea.

---

### Post by NewToLinux123 on 2008-06-26
> **jualin said:**
> I thought you meant Recovery Mode for some reason. I don't know why this is happening to you maybe you should check the kernel messages when you log in.

Does not pop up with any messages just goes straight back into login screen.

---

### Post by NewToLinux123 on 2008-06-26
> **jualin said:**
> How about trying to reinstall the ubuntu-desktop package. This should install gnome again and may fix your problem. Now that's the Windows way of thinking. Maybe one of the people from the forum have a better idea.

Now if I reinstall will I still have all my programs and files on my computer or will it be erased??

---

### Post by NewToLinux123 on 2008-06-27
Anyone know how I can fix my problem??:confused:

---

### Post by jualin on 2008-06-27
yea you would have the same programs on your computer. But only if you reinstall ubuntu-desktop from Synaptic Package Manager.

---

### Post by ladr0n on 2008-06-27
open a terminal, type ```

sudo chown username:username .dmrc
sudo chmod 644 .dmrc
```
where username is your login name

Log out and try to log in to a normal Gnome session.

---

### Post by forger on 2008-06-27
> **jualin said:**
> How about trying to reinstall the ubuntu-desktop package. This should install gnome again and may fix your problem.

Actually, ubuntu-desktop is a meta-package (a "shortcut") to install other programs, it won't reinstall gnome, but it might fix missing dependencies

---

### Post by pietjanjaap on 2008-06-27
Maybe your video driver is not ok, which hardware do you have?

Try install envy, here you can remove ati and nvidea drivers, and reinstall it.




With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

