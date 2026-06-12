---
title: "Cannot log in: Session lasted less than 10 seconds"
date: 2008-02-17
forum: General Help
---

### Post by sahibd27 on 2008-02-17
I can no longer logon to ubuntu!!!! I am using 7.10. I think I know the cause of my problem, but I don't know how to fix it. And I really don't feel like having to reinstall ubuntu and all the apps I had before. When I use failsafe terminal mode, I can't really do anything because it cannot find commands such as 'ls' or 'printenv'. When I login to Failsafe GNOME, it just freezes and causes me to shut the computer down through brute force. Any other attempt to login gives me something like this:

'Your session only lasted less than 10 seconds.' Here are the /.xsession-errors details:

process:6150: Gtk-WARNING **: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+:
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 17: id: not found
/etc/gdm/Xsession: 191: ls: not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
exec: 204: x-terminal-emulator not found

I think what caused this problem is the fact that I changed the /etc/environment, the .bashrc, and the ~/.profile file to add some environment variables. I had to do this for a CS project, and I read that if you want to set environment variables, you do it in this file. Anyway, I changed the path variable:

export PATH=$PATH:/$EC2_HOME/bin

Anyways, I'm a noob to Ubuntu and I don't know how to add environment variables. And I believe that has led to my problem above, but I could be mistaken (but I doubt it).

Please help me.

---

### Post by seventhc on 2008-02-17
you might try booting into the live cd and undo the changes that you've made.
For future reference, I would add a second user on the machine for testing purposes, this way you'll always have your main account incase something goes wrong.
In the live cd you can use sudo and you should be able to make changes. sudo won't ask for a password but I believe you'll still get the needed permissions.

---

### Post by arpad9 on 2008-03-02
I just saw your post because I'm trying to get rid of the Gtk setuid errors in my .xsession-errors file.

I don't think this is your problem.  I had your problem when I set up /tmp on RAID.  I didn't mount it read/write. /tmp needs to be writable by the world (777).  In your case maybe that's not the problem and you inadvertently changed permissions or ownership on some of the files you were editing.  Check permissions and ownership in your home dir (don't forget dotfiles). ' ls -ld .*'

Arpad

---

### Post by ronaldv2li on 2008-03-03
I had the same problem. Tried different methods... nothing worked... except - adding new user. 

I'm a complete N00b, but I think your current user quite hopelessly lost. Something is corrupted. However... if you create a new user it doesn't have that problem :)

Here's what I did:

Booted through recovery mode. Should be in as root. 
Add new user:

```
adduser <username>
```

Fill in the details.

Now you would want to give your user administrator permissions.
Type:

```
gpasswd -a <username> admin 
``` 

To login in normal mode as normal user:

```
gdm
```

Did it some time ago, might have forgotten something. Let me know how it went ;)

---

### Post by jseyerle on 2008-03-06
I had the same problem after trying to setup my own env.
To fix this login to terminal.

PATH=/bin:/usr/bin:/usr/sbin; export PATH

Then go and remove what you added to the /etc/enviroment file
I also removed .bashrc and .profile edits i had made, but i think the problem is /etc/enviroment

exit

login again

---

