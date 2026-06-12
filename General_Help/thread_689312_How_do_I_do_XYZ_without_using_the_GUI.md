---
title: "How do I do XYZ without using the GUI?"
date: 2008-02-06
forum: General Help
---

### Post by kprateek88 on 2008-02-06
There seems to be a lot of emphasis on being able to do things without using the CLI, but my question is different. There are many common things which I would like to be able to do without the GUI:

1) The CLI is more reliable. KDE + Compiz has some quirks, and something goes wrong every now and then.
2) Using the CLI can be faster.
3) I can tell another program or write a script to run "/path/to/file --arguments", but I can't tell it to click on an icon and select a menu item.
4) Using a tty...

Here are a few things I know how to do with the GUI, but not from the command line:
1) Shutdown, restart, suspend, hibernate, without needing root priviledges. (Actually, I can't even do this from the GUI properly: [http://ubuntuforums.org/showthread.php?p=4207995](http://ubuntuforums.org/showthread.php?p=4207995) ).
2) Lock the graphical session.
3) Mount and unmount USB devices without being root and without messing around with /etc/fstab.

---

### Post by bodhi.zazen on 2008-02-06
> **kprateek88 said:**
> There seems to be a lot of emphasis on being able to do things without using the CLI, but my question is different. There are many common things which I would like to be able to do without the GUI:

1) The CLI is more reliable. KDE + Compiz has some quirks, and something goes wrong every now and then.
2) Using the CLI can be faster.
3) I can tell another program or write a script to run "/path/to/file --arguments", but I can't tell it to click on an icon and select a menu item.
4) Using a tty...

Here are a few things I know how to do with the GUI, but not from the command line:
1) Shutdown, restart, suspend, hibernate, without needing root priviledges. (Actually, I can't even do this from the GUI properly: [http://ubuntuforums.org/showthread.php?p=4207995](http://ubuntuforums.org/showthread.php?p=4207995) ).

I don't know about hibernate.

For shutdown, use visudo and add a line allowing you to run shutdown w/o a password :

> %admin ALL=(ALL) NOPASSWD: /sbin/shutdown
%admin  ALL=(ALL) NOPASSWD: /sbin/reboot

Place those lines in the "groups" section ;)

Then shudown -h now = shutdown
shutdown -r now = reboot
reboot = reboot

> 2) Lock the graphical session.

You can try xtrlock, it is in the repos

[http://www.digipedia.pl/man/xtrlock.1x.html](http://www.digipedia.pl/man/xtrlock.1x.html)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xtrlock&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=xtrlock&searchon=name&subword=1&version=all&release=all)

> 3) Mount and unmount USB devices without being root and without messing around with /etc/fstab.

The command that allows this is pmount.

[http://www.penguin-soft.com/penguin/man/1/pmount.html](http://www.penguin-soft.com/penguin/man/1/pmount.html)

Pmount mounts in /media

pmount /dev/sdxy usb

There are a few "rules", ie the device must not be in /etc/fstab for one ...

You can make life easier with alises , put them in ~/.bashrc

---

### Post by kuja on 2008-02-06
To shutdown using the cli, you need to use the shutdown command. To make it usable by anybody, you'll want to put hte exact command including all arguments in the sudoers file ... the lines will probably look like this:

To edit the file use the command "sudo visudo"

```
%admin localhost = NOPASSWD:/sbin/shutdown -h now
%admin localhost = NOPASSWD:/sbin/reboot
```
(note: reboot is just an alias for "shutdown -r now"

To lock session in KDE: dcop kdesktop KScreensaverIface lock
To bring up logout menu: dcop kdesktop KDesktopIface logout

Not sure about the rest ...... that's a start though.

edit: looks like someone else got to it first, oh well.

---

### Post by kprateek88 on 2008-02-07
Thanks.

Using visudo and all is fine for me, since I'm root (and the sole user, in fact) on my system. However, this is not **equivalent** to K-menu->Log Out->Shutdown, which can be used by a non-root user out of the box, without requiring changes to /etc/sudoers (which needs root priviledges). If one (a non-root user, in particular) can do it from the K menu, surely there should be a way to do it from the command line... 
Or is it a conscious decision not to have command-line equivalents of things like K menu->Log Out->Shutdown, to prevent malicious programs (running as an ordinary user) from misusing it?

---

### Post by kuja on 2008-02-07
Come to think of it, there may be a slightly more direct way to do it that can be done without editing sudoers. I'm somewhat certain that it does it through grub .... soooooooooooo, try this

grub
halt

or 

grub 
reboot

---

### Post by bodhi.zazen on 2008-02-07
> **kprateek88 said:**
> Thanks.

Using visudo and all is fine for me, since I'm root (and the sole user, in fact) on my system. However, this is not **equivalent** to K-menu->Log Out->Shutdown, which can be used by a non-root user out of the box, without requiring changes to /etc/sudoers (which needs root priviledges). If one (a non-root user, in particular) can do it from the K menu, surely there should be a way to do it from the command line... 
Or is it a conscious decision not to have command-line equivalents of things like K menu->Log Out->Shutdown, to prevent malicious programs (running as an ordinary user) from misusing it?

No, all gui run commands.

First, there is no reason to run as root, this is a big security risk.

Second, I am not familiar with the kde commands. You can look at the menu to see what the commands are. I think for log out it uses /usr/bin/stopkde

One can run stopkde on a kde session, or any other process, they own, but not another uses kde session or process (without root access).

Shutdown are going to be the commands we gave you. I am not sure how KDE handles them though.

---

### Post by all2ez on 2008-04-03
For anyone interested in the suspend, I was trying to get a one-click suspend icon and thanks to some help from this post and others I was able to do it by creating an "Application in Terminal" launcher to run the command:  

```
sudo /etc/acpi/sleepbtn.sh
```

To avoid having to enter the password I used visudo to edit /etc/sudoers as described above, but I used the line:

```
%admin ALL=(root) NOPASSWD:/etc/acpi/sleepbtn.sh
```

I also noticed that there is a file /etc/acpi/lockbtn.sh that you can use the same way to lock the screen from the command line if you didn't already figure that one out.

---

