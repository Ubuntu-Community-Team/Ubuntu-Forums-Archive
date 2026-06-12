---
title: "How to force boot with xfce"
date: 2014-02-27
forum: General Help
---

### Post by mynot on 2014-02-27
Hi. I've been running Xubuntu 13.10 with xfce environment and thought I'd try Cinnamon which I'd installed some time ago. It seems ok until I open any of the panel items (eg Menu), at which point it appears to lock, ie it won't accept keystrokes or mouseclicks. This means I can't select Logout from the menu and thus can't get back to xfce. How can I tell Xubuntu to boot with xfce? (I have several Linux os's on the system and a rescue cd).
Note that I'm not interested in solving the problem with Cinnamon, only getting back to xfce.
Thanks

---

### Post by ajgreeny on 2014-02-27
One of the problems of using autologin is that the system automatically  goes to the last chosen DE.  If you can not get to the logion screen for  the reason you cite here, and do not know how to kill a frozen  xsession, you can not get to a login screen to change to a different DE.
From your running cinnamon desktop, there is probably a command to stop the cinnamon session, but never having used cinnamon I do not have a clue what it may be.

So as a workaround you can hold Rt Alt+Print screen+K to kill the xsession. This should get you back to the lightdm login screen, where you can again choose Xubuntu session.

---

### Post by zvacet on 2014-02-27
On login screen you can choose witch desktop you want to start.Select xfce and login.

---

### Post by Bucky Ball on 2014-02-27
Hit Ctl+Alt+F1. This will give you a command line. Type 'sudo reboot now' (without the apostrophes). Enter password, hit enter and the machine should reboot.

When you get to the login screen click 'Sessions' and choose xfce session. ;)

* Just realised it won't accept keystrokes. Scratch that. But give it a try anyway ...

---

### Post by Bashing-om on 2014-02-27
mynot; Hi !
How a bout this approach ?
Boot up with "text" as a boot parameter (grub boot menu)
I expect you will boot to a text terminal;
Login-> username and password;
What results from either (as we do not know what is set up in the control file ~/.xinitrc)
```

startx
##or##
startxfce4

```
Then perhaps we can see about removing cinnamon(??).

When all else fails
[INDENT][INDENT]there is always the command line[/INDENT][/INDENT]

---

### Post by zvacet on 2014-02-27
Boot in recovery mode and type

```
nano /etc/lightdm/lightdm.conf
```

find the lines

```
autologin-guest=false 
 autologin-user=username
 autologin-user-timeout=0
 autologin-session=lightdm-autologin
```

and make them look like this

```
#autologin-guest=false 
#autologin-user=username
#autologin-user-timeout=0
#autologin-session=lightdm-autologin
```

Ctrl+X  to exit and save file and that is it.Reboot and you should find on login screen option to login to xfce.

---

### Post by mynot on 2014-02-27
Thanks for the replies. After getting things into a worse muddle ZVACET's suggestion to edit lightdm finally solved the problem.

Now, can anyone please point me to a good description of what happens between Linux loading and the desktop being displayed? What, for example, is the relationship between Linux, X11, lightdm and xfce? What configuration files are used? (Not asking anyone to answer these questions - just point me to a source.) At the moment it's a mystery and solving problems is a matter of picking posts more or less at random and trying things.

Thanks again.

---

### Post by Bucky Ball on 2014-02-27
Please mark this thread as solved to help others and start a new thread with any other questions. These new ones are unrelated to your thread title and you have more chance of support in a new thread. Thanks.

---

