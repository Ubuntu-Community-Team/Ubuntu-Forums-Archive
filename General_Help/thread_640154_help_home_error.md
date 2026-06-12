---
title: "help home error"
date: 2007-12-13
forum: General Help
---

### Post by tmm2112 on 2007-12-13
I just started getting this error.  When I boot up, it says that my $home/.dmrc file is being ignored.  File should be owned by user and have 644 permissions.  user's $home directory must be owned by user and not writable by other users.

This all began because I could not copy ndiswrapper files into my "home" folder, as I was instructed to do on the Ubuntu docs page.  It said I did not have the permission, so I changed the permissions on my "home" folder.  This caused the error on boot up.

So, anyone have any idea on the boot up error and/or why I can't copy files to my home folder and why changing the permission caused this error?

---

### Post by p_quarles on 2007-12-13
Changing the permissions on the entire home folder will definitely cause this to happen. 

Anyway, here's how to fix it:
First step: revert the ownership/permissions of .dmrc to its old state by running these commands:
```
sudo chown *username* .dmrc
```
then:
```
chmod 644 .dmrc
```
Log out, log back in.

If that doesn't work, you can force the system to generate a new .dmrc file by running this:
```
mv .dmrc bak.dmrc
```
This will rename your .dmrc file to something the system doesn't recognize, while still preserving the data contained. You could also simply delete the file, but this way will allow you to recover old settings if need be.

---

### Post by dondad on 2007-12-13
If you change the permissions on your home folder, this will happen. Here is what I do to fix it when I mess it up. (one other way to mess it up is to accidentally use sudo rather than gksudo on a graphical application like nautilus)

To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R* username*:*username* .

Note the dot

then 

sudo chmod -R u_rwx .

again, note the dot.

This will set your home folder to 755 and everything in the folders to 644.

---

### Post by tmm2112 on 2007-12-15
Well, this is a nice development.  When I booted up to make the recommended changes, my system will no longer allow me to log in.  It says that I was only on for 10 seconds and kicks me back to the log in window, over and over.  

The details say that the system is refusing to initialize GTK+ and can't create a whole list of directories.

I booted into a failsafe terminal and tried the commands suggested, but this was my response:

'No such file or directory'

Any suggestions?  Does this mean a fresh install is needed?

Side question.  If I reinstall, how do I do so without upsetting my WinXP partition?  I did this once before (reinstall) and it wrecked my XP partition and I had to wipe the whole disk and start over.

Thanks for suggestions...

:confused:

---

### Post by taurus on 2007-12-15
When you boot into recovery mode, you are logged in as root, not as a regular user anymore.  Therefore, there is no /root/.dmrc.  You need to use your actual log in name when you change the permission/ownership of your $HOME/.dmrc.

_Assuming_ your log in name is **don**, try

```
chown **don**:**don** /home/**don**/.dmrc
chmod 644 /home/**don**/.dmrc
```
Reboot and see if you can log in again.

---

### Post by tmm2112 on 2007-12-15
The response was "cannot access .dmrc, no such file or directory"

---

### Post by taurus on 2007-12-15
What is the exact command that you ran?  I assume you were in a recovery mode, right?

What's the output of this command?

```
ls -la /home
```

---

### Post by tmm2112 on 2007-12-16
Sorry for the time lag.  I can't seem to devote enough time to get this fixed.

I ran the ls -la /home command and here's what I got:

total 12
drwxr-xr-x 3 mark mark 4096 dec 7 03:58 .
drwxr-xr-x 21 mark mark 4096 dec 7 04:08 ..
drwxr-xr-x 35 mark mark 4096 dec 13 21:10 mark

The previous command I ran was chown mark:mark /home/mark/ .dmrc

The result of that was  "cannot access .dmrc, no such file or directory".

Thanks

---

