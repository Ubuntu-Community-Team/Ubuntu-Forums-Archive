---
title: "HELP!! Cannot login as administrator!"
date: 2008-04-30
forum: General Help
---

### Post by Neo Adventist on 2008-04-30
OK, I don't what just happened, but I just lost all administrator access. You see, in my new (clean) Hardy Heron 64-bit installation, I've been keeping 2 separate user logins. One login, "superuser", had full administrative rights, and the other login, "guest", merely had basic (NON-SUDO) rights. The problem is that my administrative login now fails to, well, log in. After entering the username and password, this flag comes up:


***User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.***

After clicking "OK", I get a blank orange screen for about 30 seconds, then this flag pops up:

***The GNOME session manager was unable to lock the file '/home/superuser/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable; you could try logging in via the failsafe session and ensuring that it is.***

After again clicking "OK" I get a blank black screen for about 30 seconds, and I'm returned to the login screen. I have NO idea what's going on. Is this error causing a security breach?

---

### Post by msutton86 on 2008-04-30
have you tried to login into the terminal using your power user account?  hit ctrl-alt-f1.(ctrl-alt-f7 to return back to gui.)  If you can make it that far you can more than likely change you home directory or try to repair it.  [User Commands]("http://www.ahinc.com/linux101/users.htm")

Wish you luck!

---

### Post by lungten on 2008-04-30
I would suggest you to login to recovery mode (from GRUB) where you directly log in as 'root'. After that you can change the permission of the files **$HOME/.dmrc** and **/home/superuser/.ICEauthority** so that hey are writable by your **superuser** user.

---

### Post by Neo Adventist on 2008-05-01
Um, ok, I would appreciate more information before I do ANYTHING as root, please. *cue suspenseful music*

In terminal:

> 
guest@linuxAMD64-desktopPC:/home/superuser$ **ls -l .dmrc .ICEauthority**
-rw------- 1 superuser superuser  28 2008-04-30 16:39 .dmrc
-rw------- 1 superuser superuser 187 2008-04-30 16:39 .ICEauthority


If I'm understanding this correctly, the "-rw-------" refers to permissions, and it is saying:

 "file readable/writable by file owner (superuser); file NOT readable/writable by owner's group (superuser); file NOT readable/writable by any other user"

Am I at least correct in that regard? If so, what SHOULD that line look like? and what would be the proper way of correcting it in recovery mode?

Please bear with me, I'm still a very green ubuntu bean!  :popcorn:

---

### Post by Neo Adventist on 2008-05-01
Oooooooooooooh........  I think I have the answer already.

"644 Permissions" is a binary way of saying "-rw-r--r--", which in turn means:

"file readable/writable by file owner (superuser); file readable/ NOT writable by owner's group (superuser); file readable/ NOT writable by any other user"

AND, "chmod" is the command tool needed to change permissions!

So, in recovery mode, my codes should be:

#1: "cd /home/superuser/"
#2: "chmod 644 .dmrc"
#3: "chmod 644 .ICEauthority"

Am I on the right track? Am I missing something important? Please tell!

........ [http://linuxcommand.org/](http://linuxcommand.org/) is my friend indeed!

---

### Post by warp99 on 2008-05-01
> **Neo Adventist said:**
> Oooooooooooooh........  I think I have the answer already.

"644 Permissions" is a binary way of saying "-rw-r--r--", which in turn means:

"file readable/writable by file owner (superuser); file readable/ NOT writable by owner's group (superuser); file readable/ NOT writable by any other user"

AND, "chmod" is the command tool needed to change permissions!

So, in recovery mode, my codes should be:

#1: "cd /home/superuser/"
#2: "chmod 644 .dmrc"
#3: "chmod 644 .ICEauthority"

Am I on the right track? Am I missing something important? Please tell!

........ [http://linuxcommand.org/](http://linuxcommand.org/) is my friend indeed!

What's the ownership and file mode on your directory /home/superuser? Because the mode on both files in my system are 600 for the .ICEauthority file and 400 for .dmrc, so the problem appears to be at the /home/superuser level.

---

### Post by Neo Adventist on 2008-05-02
In Terminal:

> 
guest@linuxAMD64-desktopPC:~$ **ls -l /home**
total 8
drwxr-xr-x 33 guest guest 4096 2008-05-01 20:52 guest
drwxr-xr-x 37 root  root  4096 2008-04-30 17:28 superuser
guest@linuxAMD64-desktopPC:~$ **cd /home/superuser/**
guest@linuxAMD64-desktopPC:/home/superuser$ **ls -l .dmrc .ICEauthority**
-rw------- 1 superuser superuser  28 2008-04-30 16:39 .dmrc
-rw------- 1 superuser superuser 187 2008-04-30 16:39 .ICEauthority


As near as I can figure:
the directory "/home/superuser/" is set at 755
the directory "/home/guest/" is set at 755
the file ".ICEauthority" is set at 600
the file ".dmrc" is set at 600

---

### Post by warp99 on 2008-05-02
Here is your problem:

> drwxr-xr-x 37 root root 4096 2008-04-30 17:28 superuser

Your ownership is set to root instead of superuser, so do the following:
```
sudo chown -R superuser:superuser /home/superuser
```
and all will be back to normal.

---

### Post by Neo Adventist on 2008-05-02
All right! Thank you. However, I will have to do this in recovery mode, because I have no sudo access at the moment as "guest".

---

### Post by warp99 on 2008-05-02
> **Neo Adventist said:**
> All right! Thank you. However, I will have to do this in recovery mode, because I have no sudo access at the moment as "guest".

No you don't just type 'su superuser' at the command line to change user, then run your commands. When done type 'exit'.

---

### Post by Neo Adventist on 2008-05-02
> **warp99 said:**
> No you don't just type 'su superuser' at the command line to change user, then run your commands. When done type 'exit'.

Too late, I did it already! XD

YES!! IT IS BACK!! THANK YOU!!

Though why in the world was my screen resolution knocked back down to 800x600? Oh well, fixed that too.

---

