---
title: "xfce switch user/logout/restart keyboard shortcuts"
date: 2007-09-07
forum: General Help
---

### Post by steeef on 2007-09-07
I've just switched to xfce from Gnome, and I love it. I'm busy recreating things that I had setup in Gnome, but I can't figure out one thing: when I press the power button on my laptop or click the Quit icon on my panel, I get a row of buttons that allow me to Restart, Shutdown, Logout, etc. This works as expected, but with Gnome I could type ALT-R to restart, or ALT-S to shutdown. I noticed there are no keyboard shortcuts for these buttons in xfce, and I'm forced to either click on them with my mouse, or use the arrow keys to select the right one and hit ENTER.

Am I missing something? Is there a way to enable keyboard shortcuts for these buttons, or was this an intentional design?

---

### Post by mali2297 on 2007-09-15
> **steeef said:**
> Am I missing something? Is there a way to enable keyboard shortcuts for these buttons, or was this an intentional design?

I also miss keyboard shortcuts in that menu. It can hardly have been intentional, rather neglected. 

If anyone has found a solution to this, please share.

---

### Post by donal on 2007-11-03
I am new to linux and was just about to give up on this one.  But with a bit of persistence it looks like i found a way to do this:

First i saw this blog which shows you how to assign commands to keyboard shortcuts.
[http://xubuntublog.wordpress.com/2007/05/29/your-wish-is-xubuntus-command/](http://xubuntublog.wordpress.com/2007/05/29/your-wish-is-xubuntus-command/)

The command you want here is:
sudo shutdown -P now

but assigning that to a keyboard shortcut straight off won't work. The problem is you need to provide a password to use this sudo command. To get around this you can do the following: 

in terminal:
sudo visudo
add this line at the end of the file:
your_user_name ALL=NOPASSWD:/sbin/shutdown -P now


where your_user_name is your username
save and exit (Ctrl+o Enter Ctrl+x) 

i got this from the following link by the way
[http://ubuntuforums.org/archive/index.php/t-413377.html](http://ubuntuforums.org/archive/index.php/t-413377.html)

This lets you run the shutdown command without the need to provide a sudo password and you are all good.  Just assign the command:

 sudo shutdown -P now

 to whatever key combination takes your fancy. Hope this helps someone out there.

---

### Post by mali2297 on 2007-11-04
> **donal said:**
> I am new to linux and was just about to give up on this one.  But with a bit of persistence it looks like i found a way to do this:

First i saw this blog which shows you how to assign commands to keyboard shortcuts.
[http://xubuntublog.wordpress.com/2007/05/29/your-wish-is-xubuntus-command/](http://xubuntublog.wordpress.com/2007/05/29/your-wish-is-xubuntus-command/)

The command you want here is:
sudo shutdown -P now

but assigning that to a keyboard shortcut straight off won't work. The problem is you need to provide a password to use this sudo command. To get around this you can do the following: 

in terminal:
sudo visudo
add this line at the end of the file:
your_user_name ALL=NOPASSWD:/sbin/shutdown -P now


where your_user_name is your username
save and exit (Ctrl+o Enter Ctrl+x) 

i got this from the following link by the way
[http://ubuntuforums.org/archive/index.php/t-413377.html](http://ubuntuforums.org/archive/index.php/t-413377.html)

This lets you run the shutdown command without the need to provide a sudo password and you are all good.  Just assign the command:

 sudo shutdown -P now

 to whatever key combination takes your fancy. Hope this helps someone out there.

Thanks, I also found this workaround. 

You can do the corresponding thing for **sleep** and **hibernate**, the commands are respectively
```

sudo /etc/acpi/sleep.sh
sudo /etc/acpi/hibernate.sh

```

If you don't want to mess with the sudoers file, you can instead exchange sudo with **gksudo**. Of course, then you will be prompted with a password every time you want to shutdown/sleep/hibernate the computer.

---

