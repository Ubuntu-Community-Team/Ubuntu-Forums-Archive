---
title: "Help w/ .ICEauthority error!"
date: 2008-01-25
forum: General Help
---

### Post by silentsniper on 2008-01-25
well. i have the same problem... on my secondary acc. i cant get in either so i logged in and verified myself as root on the main account and chmod -ed the permissions to rw-r-r
and then that didnt work so i tried other permissions leaving out execute because it says "cannot execute the binary file" so..... i chmod-ed the file /home/robert/.ICEauthority and then i used "ls -l /home/robert/.ICEauthority" without the "" and it showed exactly the right permissions that i applied so i logged out and still couldnt log in as "robert" so.... i went into failsafe and looked at my permissions for the account that has the error and they didnt save!! and i was verified as root. well..... i cant figure out why the permissions changes to the .ICEauthority dont save when i am verified as root.... help please!!

---

### Post by taurus on 2008-01-25
Boot into recovery mode and post the output of this command here.

```
ls -la /home/robert
```

---

### Post by silentsniper on 2008-01-25
ok, i got a list of permisions to files and directories in that folder....now what? thanks by the way

---

### Post by taurus on 2008-01-25
I just want to see who's the owner of /home/robert and what would the permissions look like.

While you are still in the recovery mode, try

```
chown -R robert:robert /home/robert
chmod 755 -R /home/robert
chown 600 /home/robert/.ICEauthority
chown 600 /home/robert/.dmrc
shutdown -r now
```
Now, see if you can log in as robert again.

---

### Post by silentsniper on 2008-01-25
.dmrc? what is that? brb gonna try those command thanks!

---

### Post by silentsniper on 2008-01-25
ok i tried and i am back in except at login it said that  the dmrc thing was being ignored and that it should be 644 so i am the only one who can read write and execute and not others

-thanks. 
-robert

btw......do i change both 600 values to 644 or one with the dmrc?

---

### Post by taurus on 2008-01-25
Just open a terminal and change the permission on that file.

```
chmod 644 ~/.dmrc
```

---

### Post by silentsniper on 2008-01-25
so.. can you explain to me why i use the "~" key and what the "-R" does as well as why you put a numbered permissions value for chown i thought only chmod used numbered permissions values and chown used the unknown "-R" character.

---

### Post by silentsniper on 2008-01-25
ok.. loggedin again got same thing " the user's $HOME/.dmrc file is being ignored" and "the permissions should be 644 so the file is only readable and writeable by the user and noth others"

---

### Post by taurus on 2008-01-25
What's the output of this command from a terminal?

```
ls -la ~/.dmrc
```

The ~ means your $HOME directory.  In other words, it is the same as /home/robert.

The -R means recursive, meaning changing all files and directories.

---

### Post by silentsniper on 2008-01-25
-rw-r--r-- 1 600 robert


also, the permissions dont save when i mod them for an odd reason....even when su is used..

---

### Post by taurus on 2008-01-25
I assume you are currently logged in as robert and you are using Gnome window manager.  Can you post the whole outputs of these commands from a terminal?

```
ls -la ~
id
```

---

### Post by silentsniper on 2008-01-25
robert@CNS03:~$ ls -la ~ id
ls: id: No such file or directory
/home/robert:
total 244
drwxr-xr-x 27 robert robert  4096 2008-01-25 09:47 .
drwxr-xr-x  5 root   root    4096 2008-01-08 09:08 ..
-rwxr-xr-x  1 robert robert  8064 2008-01-25 09:46 .bash_history
-rwxr-xr-x  1 robert robert   220 2008-01-08 09:08 .bash_logout
-rwxr-xr-x  1 robert robert  2298 2008-01-08 09:08 .bashrc
drwxr-xr-x  3 robert robert  4096 2008-01-08 09:10 .cache
drwxr-xr-x  5 robert robert  4096 2008-01-08 09:14 .config
drwxr-xr-x  3 robert robert  4096 2008-01-14 07:53 Desktop
-rw-r--r--  1    600 robert    28 2008-01-15 08:15 .dmrc
drwxr-xr-x  3 robert robert  4096 2008-01-08 09:29 Documents
-rwxr-xr-x  1 robert robert    16 2008-01-08 09:10 .esd_auth
drwxr-xr-x  3 robert robert  4096 2008-01-11 08:23 .evolution
lrwxrwxrwx  1 robert robert    26 2008-01-08 09:08 Examples -> /usr/share/example-content
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 .fontconfig
drwxr-xr-x  4 robert robert  4096 2008-01-25 09:47 .gconf
drwxr-xr-x  2 robert robert  4096 2008-01-25 09:53 .gconfd
drwxr-xr-x  3 robert robert  4096 2008-01-08 09:10 .gnome
drwxr-xr-x 10 robert robert  4096 2008-01-25 09:47 .gnome2
drwx------  2 robert robert  4096 2008-01-08 09:10 .gnome2_private
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 .gstreamer-0.10
-rw-r--r--  1 robert robert   112 2008-01-25 09:47 .gtk-bookmarks
-rwxr-xr-x  1 robert robert    88 2008-01-08 09:10 .gtkrc-1.2-gnome2
drwxr-xr-x  2 robert robert  4096 2008-01-14 10:20 .hplip
-rw-------  1 robert robert   785 2008-01-25 09:47 .ICEauthority
drwxr-xr-x  3 robert robert  4096 2008-01-08 09:10 .local
drwxr-xr-x  3 robert robert  4096 2008-01-08 09:31 .mozilla
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 Music
drwxr-xr-x  3 robert robert  4096 2008-01-25 09:46 .nautilus
-rwxr-xr-x  1 robert robert 73728 2008-01-14 08:36 nautilus-debug-log.txt
drwxr-xr-x  3 robert robert  4096 2008-01-10 09:23 .openoffice.org2
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 Pictures
-rwxr-xr-x  1 robert robert   566 2008-01-08 09:08 .profile
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 Public
-rwxr-xr-x  1 robert robert   298 2008-01-10 09:23 .recently-used
-rw-r--r--  1 robert robert  4421 2008-01-25 09:47 .recently-used.xbel
-rw-r--r--  1 robert robert     0 2008-01-25 09:45 .sudo_as_admin_successful
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 Templates
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 .Trash
drwx------  2 robert robert  4096 2008-01-25 09:33 .update-notifier
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:10 Videos
drwxr-xr-x  2 robert robert  4096 2008-01-08 09:29 .w3m
-rwxr-xr-x  1 robert robert   116 2008-01-15 08:15 .Xauthority
-rw-r--r--  1 robert robert  2308 2008-01-25 09:47 .xsession-errors


alright.....when i logged in as root using "su" earlier i gave myself permissions to read and write to the iceauthority but they didnt save.....why??

---

### Post by taurus on 2008-01-25
There is a wrong owner that owns your ~/.dmrc.  Not sure what 600 is so run this from a terminal.

```
sudo chown robert /home/robert/.dmrc
```
Now, log out and back in again and see if it still complains about your ~/.dmrc.

---

### Post by silentsniper on 2008-01-28
alright that worked, sorry i didnt get back to you earlier OSC was over. thanks for the help!!!!

---

