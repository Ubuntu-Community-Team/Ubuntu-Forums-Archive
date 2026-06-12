---
title: "Permissions trouble after installing virtualbox"
date: 2007-04-22
forum: General Help
---

### Post by chio on 2007-04-22
I've installed the virtual machine package VirtualBox, added myself to the group vboxusers and rebooted.

But now I seem to have lost all permissions to do anything on my own computer -- "add/remove programs" and most of the administration options have disappeared from my menus and if I go into a terminal and type *sudo whatever*, nothing happens, it just returns me to a prompt with no message. 

How can I set my permissions back to what they were? I'm not that arsed about VirtualBox, if I break that, so be it -- I just don't want to have to reinstall yet again.

Cheers
Andy

PS. Yes, I know this forum's flooded out with one post every eight seconds and this isn't a very interesting or "sexy" problem, but all help will be greatly appreciated!

---

### Post by qpieus on 2007-04-22
This happened to me too. What happened was when I added my username to vbox users, I somehow REMOVED myself from all other groups I belonged too. It sounds like the same happened to you. Go into a terminal window and type```
groups
``` and see what the output is. if you only see vboxusers then that's the problem. I belong to the following groups, for your reference.```
randy adm cdrom floppy audio dip video plugdev lpadmin scanner admin fuse vboxusers

```
The admin group is what allows you to sudo, for example.
While you check that out, I'll do some looking around and see if I can find the references I used to fix the problem (I don't remember exactly what I did).

---

### Post by qpieus on 2007-04-22
OK, I found the method to add yourself back to the admin group:

- restart the system and choose recovery mode from the grub menu (it may be called rescue mode - I don't remember), you'll enter a shell with root privileges - no need for password

- addgroup username admin

- reboot and choose your normal kernel.

Now you can add yourself into whatever groups you need to by using the gui interface (try System > Admin > Users and Groups)

Here's some info on this subject by aysiu:
[http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

---

