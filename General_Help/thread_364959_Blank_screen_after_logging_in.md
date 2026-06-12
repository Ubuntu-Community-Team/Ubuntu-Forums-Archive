---
title: "Blank screen after logging in"
date: 2007-02-18
forum: General Help
---

### Post by Sureshot324 on 2007-02-18
I boot up my computer, get to the Ubuntu login screen, enter my user name and password, and the Ubuntu loading screen shows for a few seconds, and then the screen goes blank.  It is beige in color, and I can move my mouse pointer around, but there's nothing else on the screen and I can't do anything.  I've left it like this for over 10 minutes and nothing happens.

The one thing I can do, is ctrl-alt,backspace, which takes me back to the login screen.  I tried changing the session to gnome failsafe, but had the same problem.  I changed the session to a terminal, and edited the xorg.conf file to use the nv driver instead of nvidia.  This worked and I could boot to the desktop.  However, if I change the driver back to nvidia I have the same problem.  With the nv driver my screen resolution can only go to 1024x768 instead of the native 1680x1050.

I installed Beryl yesterday, and it worked fine after several reboots.  I though that might be the problem, so i ran apt-get remove beryl, but this did not fix my problem.

I am really stumped, since I don't even know what's causing this.  Is there a boot log file somewhere, so I can at least see what the error is?  Any help will be much appreciated.  I am using Ubuntu 6.10 Edgy x64.

---

### Post by llamakc on 2007-02-18
Did Beryl require you to alter the /etc/gdm/gdm.conf-custom file? or the /etc/gdm/gdm.conf file? I would walk backwards through the setup steps to see if you forgot to 'undo' a particular step.

Did you make sure that they're still not in your ~/.config/autostart directory?

---

### Post by GrumpySmurf on 2007-02-19
This problem [has been reported]("http://www.ubuntuforums.org/showthread.php?t=359163") by other users, including myself on that thread. Searching for "Blank Desktop" or "Blank GNOME" will show a few hits for other threads of similar problems.

This is obviously a common problem. Does anyone reading this know the best way to get a lot of developer attention? In my experience, bug reporting will only get one, maybe two, developers looking at a problem.

This is really annoying for me. I don't relish the thought of reinstalling, for the couple hours it would take to get my configuration set up how I like it again (samba mounts, printers, etc). This is enough for me to skip out on Ubuntu and Linux again entirely and use Windows again for the simple fact that while it has its own problems, they aren't complete show stopping issues that can't be easily solved.

And after using Linux for so long, this is really disappointing.

---

### Post by Sureshot324 on 2007-02-20
I seem to have fixed this problem by deleting all these folders:

~/.gnome
~/.gnome2
~/.gconf
~/.gconfd
~/.metacity

I also deleted beryl.desktop and emerald.desktop from ~/.config/autostart/.

---

