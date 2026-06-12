---
title: "Root login problem"
date: 2006-10-07
forum: General Help
---

### Post by DarkOdysseus on 2006-10-07
I have two user accounts I use. I use a regular user account because I am new and learning shell programming. Now when I try to log in to my root user account, I get a weird message:

User's $HOME.dmrc file is being ignored. This prevents
the default session and language from being saved.
File should be owned by user and have 644
permissions. User's $HOME directory must be owned by
user and not writable by other user.

I was kinda messing with privilages while learning shell scripting today. Can anyone please help a desperate noob that is about to freak out.

---

### Post by jISh on 2006-10-07
The root account is disabled in Ubuntu by default. Check [http://wiki.ubuntu.com](http://wiki.ubuntu.com) for more information if you absolutely need it. Otherwise, you can use "sudo", although I can see that being a problem with some scripts.

---

### Post by DarkOdysseus on 2006-10-07
what do you mean disabled by default? I was able to use it yesturday and now I cant. And what can I do with sudo?

---

### Post by aysiu on 2006-10-07
It means you're not allowed to log in as root unless you do something to allow yourself to log in as root.

[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by DarkOdysseus on 2006-10-24
Today while learning about shell scripting, I tryed to give my self rights the root user home folder. I guess it worked because I got no echo. Now when I try to login to my root user, I get this weird message:

User's $home/.dmrc file is being ignored. This prevents
the default session and language from being saved.
File should be owned by user and have 644
permisions. User's $HOME directory must be owned by 
user and not writable by other user.

It prevents me from logging into my root user account. Can someone please help me out with which I can get rid of this problem.

---

### Post by aysiu on 2006-10-24
I don't know why you even need to log into your root account, but have you tried this? ```
sudo chown root:root /root/.dmrc
sudo chmod 644 /root/.dmrc
```

---

### Post by DarkOdysseus on 2006-10-24
Today while I was learning shell scripting, I tryed to give myself rights to the root user's home folder. I guess it worked because I got no echo and I was told if I got no echo then it worked. I logged out and tryed to login to my root user account and got a weird message:

Users $home/.dmrc file is being ignored. This prevents
the default session and language from being saved.
File should be owned by user and have 644
permissions. Users $HOME directory must be owned by
user and not writable by other user.

I'm guessing this means that I need to give back my permissions I stole. The hitch is I dont know how. Can anyone help?

---

### Post by DarkOdysseus on 2006-10-24
I tryed the first command and I got this back:
chown: cannot access `/root/.dmrc': No such file or directory

I tryed the second command and got the same thing.
Am I just retarded.

---

### Post by matthewstory on 2006-10-24
Boot into recovery (single user mode), this is an option in grub.  Once you've done that . . . 

chown -R root:root <root home>
chmod -R 664 <root home>

then restart:

shutdown -r now

Should work fine, in the future . . . don't do this . . . haha.  Instead use sudo to edit files, and if you really need to use root for an extended period of time . . . (and i highly recommend that you never to this) then use sudo to execute a root shell:

sudo /bin/bash

But again . . . i highly recommend you never do that last thing i told you to do.

---

### Post by DarkOdysseus on 2006-10-25
I did everthing you told me.
and when I went to log in, I got a funny message saying the session only lasted 10 seconds and it could be an installation error and not enough disk space (I have tons). here is a more detailed error:

(grnome-session:4897): libgrnomevfs-WARNING**: Unable to create ~/.gnome2 directory: Permission denied.

Could not create per-user gnome configuration directory '/home/root/.gnome2/: Permission denied.

---

### Post by matthewstory on 2006-10-25
I'm a bit confused . . . firstly the root home directory should be /root, not /home/root, secondly, why are you trying to initialize a gnome  session as root?  You should never log in as root in Ubuntu, or initialize a gnome session on any linux flavor using root.  As has been already stated, Ubuntu lacks a SU by default, and it takes quite a bit of hacking to get it to have one.  The lack of SU is a security issue, as the makers of Ubuntu believe that an administrative user with sudo priveleges is more secure than a SU . .. a belief commonly shared among modern OS makers (including Apple's OS X).  Even in Linux distros where this is not the case - e.g. debian, redhat, suse etc. - you still can't initialize a gnome or KDE or X session as root.  Please stop this foolishness, and just religate yourself to running programs with sudo if you need to . . . you can even launch GUI programs with sudo from the CLI . . . ex sudo vlc.

---

### Post by matthewstory on 2006-10-25
one question . . . did you create a user named root?  It seems like this might be the case . . . though it also seems impossible.

---

