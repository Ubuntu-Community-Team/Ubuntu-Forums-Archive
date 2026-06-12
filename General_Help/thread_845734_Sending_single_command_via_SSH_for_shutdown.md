---
title: "Sending single command via SSH for shutdown"
date: 2008-06-30
forum: General Help
---

### Post by MightyPez on 2008-06-30
Ok, this will take some explaining, please bear with me.

Currently I run an Ubuntu box in my bedroom with a TV tuner and use it primarily for watching TV in bed. It's nice, but being the lazy person I am, I hate getting up to shut the box down.

I also have an HTC phone with WIFI that has a terminal and is capable of an SSH connection. I can connect to my network, dial in to the Ubuntu box with SSH and execute a shutdown command.

But can this be made even more simple? Perhaps a simple batch file to send a shutdown command to the Ubuntu TV? 

Security isn't an issue so I am not afraid to run everything as root and disable any safeguards. There is nothing sensitive on the machine and if it were wiped out tomorrow it would be no loss.

---

### Post by soccerboy on 2008-06-30
> **MightyPez said:**
> Ok, this will take some explaining, please bear with me.

Currently I run an Ubuntu box in my bedroom with a TV tuner and use it primarily for watching TV in bed. It's nice, but being the lazy person I am, I hate getting up to shut the box down.

I also have an HTC phone with WIFI that has a terminal and is capable of an SSH connection. I can connect to my network, dial in to the Ubuntu box with SSH and execute a shutdown command.

But can this be made even more simple? Perhaps a simple batch file to send a shutdown command to the Ubuntu TV? 

Security isn't an issue so I am not afraid to run everything as root and disable any safeguards. There is nothing sensitive on the machine and if it were wiped out tomorrow it would be no loss.

You could put the sequence of commands you execute into a shell script file, basically put the commands in and make the top line to read
```
#!/bin/sh
```

---

### Post by bluepowder7 on 2008-06-30
learn how to make an alias file.  call it "die" and have it execute the "sudo shutdown -P now" command

---

### Post by Habbit on 2008-06-30
It's as simple as sending the shutdown command over SSH. Either you connect as root, or as a normal user with sudo access like this:```
$ ssh COMPUTER "sudo halt"
Password:   # Presented by SSH in order to login to remote machine
Password:   # Presented by remote sudo
(remote machine powers down)
```

You can get rid of the first password prompt by creating a SSH key for you and setting it up with the remote host. This can be done very easily with the "Applications->Accessories->Passwords and cipher keys" program (make sure to pick a SSH key, not a PGP one).

The second prompt can also be avoided by editing the remote /etc/sudoers file so that the "shutdown" command (or whatever you're using to halt/reboot the machine) does not require password for users with "admin" sudo access, by adding a line like this (be very careful when editing the sudoers file, as a wrong syntax may leave you without root access and require the use of a single-user-mode reboot or even a LiveCD to set things right) ```
%admin ALL=NOPASSWD: /sbin/shutdown
```

IIrc there is another, easier but more dangerous way in Ubuntu and other distros in which the "halt", "poweroff" and "reboot" programs in /sbin are executables of their own instead of just scripts which call "shutdown": set them SETUID root like this ```
$ sudo chmod +s /sbin/reboot
```Pay attention to the following facts when following this path:
[LIST=1]
[*]In Hardy, only "reboot" is a true executable; the other two are symlinks to the first, so the +s flags is only required on the first.
[*]Why setuid these three programs instead of "shutdown"? Because the latter is way more advanced and can schedule delayed shutdowns, etc. You most probably don't want every plain user to be able to run this.
[*]BEWARE: SUIDing an executable will make EVERY USER be able to run it as root, while the sudo method only granted paswordless privileges to certain users.
[*]As a consequence, calling the three SETUIDed programs no longer require sudo: they can be invoked bare by every user.
[/LIST] 

The end result of the SSH key configuration and the sudo way of passwordless powerdown should be: ```
$ ssh COMPUTER "sudo halt"
(remote machine powers down)
```

---

### Post by MightyPez on 2008-07-03
Perfect, thank you Habbit. This is exactly what I was looking for.

---

