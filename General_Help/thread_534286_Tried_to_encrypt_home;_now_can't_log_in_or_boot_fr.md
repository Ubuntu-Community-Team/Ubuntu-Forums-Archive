---
title: "Tried to encrypt /home; now can't log in or boot from cd"
date: 2007-08-25
forum: General Help
---

### Post by clove on 2007-08-25
I tried to encrypt the /home partition of my new Dell 1420n using [_[COLOR="Blue"]these[/COLOR]_]("http://polishlinux.org/howtos/encrypted-home-partition-in-linux/") instructions (after adding a new partition to where I was going to move /home).  I ran cryptsetup and got all the way to "Automatic Mounting" section where I was supposed to set up PAM and pam_mount, however, I got nothing but errors trying to get these set up and finally gave up.

Now, when I boot up my machine, I get to the logon screen, and I get "Authentication failed" when I enter my user name.

When I try to boot off the Ubunto CD, I get "/bin/sh: can't access tty; job control turned off" and then a "(initramfs)" prompt.

I"m really stuck here.  I've learned my lesson and will just give up with trying to secure my files if I can get this thing booted again.

Thanks.

---

### Post by jamvegan on 2007-08-25
Well, I'm not sure what is going on, but can you boot in recovery mode into a root shell?  Also, when you say that booting gets to the logon screen, is that the graphical logon screen?  And does it fail authentication as soon as you enter your username, or do you enter your password, as well?

---

### Post by clove on 2007-08-25
Thanks for replying.  Yes I can boot in recovery mode and get to all my directories through the shell.  When I navigate to the home directory, I see my username intact there.  And yes, when booting normally, I get to the graphical login screen and get the authentication error as soon as I enter my username (yes I'm sure it's right).  I can't even get to the password.

As far as the error I mentioned when booting off the Ubunto cd, I found out that's a problem with all Dell 1420n's and I need to use the alternate cd instead, which I just downloaded. But I'd prefer to fix this without going through an entire clean install if possible because it looks like a huge hassle for this model of Dell.  However it's not the end of the world if I have to start over because I don't have anything important on this machine yet.

---

### Post by jamvegan on 2007-08-25
I've only done a quick read through of the tutorial you were following (and have never done anything of the sort myself), so let me see if I understand what you've done.

You created a brand new partition.  You set up encryption on it.  You copied the contents of your /home directory to this new partition.  You mounted the new partition to /mnt/home.  You tried to set up automounting with PAM, but had problems.

Questions: Did you leave your original /home directory intact?  Did you get PAM and pam_mount installed, and then have trouble with configuration?

---

### Post by clove on 2007-08-25
Yes, created the partition and copied contents of home to it. But I don't believe I've done anything yet to point the system to that new partition as the "new" home.  I haven't deleted anything from the existing home.

I think something went horribly wrong with the PAM or pam_mount install. The instructions are not simple. I remember seeing tons of error messages when the scripts were rolling by. I never even got to the part of the tutorial where I edit the /etc/pam.d/pam_mount file because it was never created during my install attempt. I believe the PAM or pam_mount botched install is causing the login problem. I'm not sure if there's any way to uninstall them.

---

### Post by jamvegan on 2007-08-25
I suspect that you are correct about PAM being the problem.  PAM (or at least some elements thereof) is part of a standard Ubuntu installation, so if you manually installed a different version that could have messed things up, I suppose.  I was going to suggest that you comment out or delete any lines that you added to the configuration files, but if you never got to that point, then that's obviously not the problem.

I don't know whether apt can deal with any problems you may have introduced when not using apt, but it couldn't hurt to run:
```
apt-get check
```

You could also check /etc/init.d/ for a pam_mount script, and if you find one, change its name so that it isn't run at boot (there are no scripts with "pam" in their name in a default install, so if you find any, you introduced them somehow).

---

### Post by clove on 2007-08-25
apt-get check didn't reveal anything, and nothing pam-related in the init.d directory...

BUT I went into etc and renamed the pam.d directory and rebooted.  Now I get a blue screen (right after the Ubuntu bar goes across the screen) saying "Can't find PAM configuration for GDM." When I hit OK, it goes out to a shell and I get a prompt saying "dell login:" When I type my username, I get "PAM Failure, aborting: Critical error - immediate abort".

So something is telling PAM to load somewhere, and if I can disable that, maybe there's hope afterall...

---

### Post by jamvegan on 2007-08-25
Actually, I don't think that completely disabling PAM will help.  I think that it is needed for normal login in Ubuntu.  Perhaps try reinstalling the following with apt-get?

libpam-modules
libpam-runtime
libpam0g
libpam-foreground

---

### Post by clove on 2007-08-25
Oh well...Tried reinstalling all four and it said everything is existing and didn't make changes.

BTW, I did find a command to list usernames
```
cat /etc/passwd | cut -d: -f1,5 | sed s/:/" "/g
```
and I've confirmed my username didn't change somewhere along the way.

This is beginning to look more and more like it's time to do a complete Ubuntu reinstall.

---

### Post by jamvegan on 2007-08-25
Yes, sometimes a clean install *is* the easiest way to get everything shipshape. :)

---

### Post by clove on 2007-08-26
Thanks, appreciate all the help.

It's too bad there's no simple way to encrypt /home.  It seems like it would be the most basic security precaution one could take, especially with a laptop.

In the meantime I'll just have to create a huge Truecrypt container file and store all my files in that.  I'll have to figure out a way to move all the config files into that for apps that store passwords in plain text like Gmail Checker and Pidgin.  I really don't want to have to worry about anything the day my laptop grows legs and wanders off on me.

If I ever figure out the whole encrypt home & PAM deal, I'll post a how-to.  But now off to rebuild my poor brand-new Dell...

---

