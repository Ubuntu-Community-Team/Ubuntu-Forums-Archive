---
title: "Login error: error while loading shared libraries: libgssapi_krb5.so.2"
date: 2008-05-25
forum: General Help
---

### Post by KillerSiafu on 2008-05-25
Hello,

I'm running Gutsy on a home-built PC that is acting as my media server. The PC ran for several months without a reboot or installing any updates. Recently, I went in and applied the long list of updates that were available to it (not including updating to hardy) and was prompted for a reboot. After the reboot, when I tried to log back in, I got the following error:

Gtk-WARNING **: This process is currently running setuid or setgid.
..
Refusing to initialize GTK+
..
/usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: Input/output error

(Some error-fluff was removed, but those are the main parts of the error).

This computer has two users, neither of which are able to login unless I change the session to Failsafe-Gnome. 

So far I've tried looking for any problems in my .profile / .bashrc, I've removed my .ICEAuthority file, and I've done a chown on my home directory... all to no avail.

Anyone have any suggestions?

---

### Post by KillerSiafu on 2008-06-08
As it turns out, this was fairly simple to fix...

I just went into the package manager and reinstalled the libgssapi package, logged out, and was able to log back in with no problems.

---

### Post by Arand on 2009-12-06
I experienced something quite similar on my jaunty install just now, starting X/GNOME failing completely, .session-errors complaining about > /usr/bin/ssh-agent: error while loading shared libraries: libgssapi_krb5.so.2: cannot open shared object file: No such file or directory.
I tried quite a few things, including fsck-ing, reinstalling nvidia drivers, removing .config/gnome-session and .ICAuthority.

However what finally seemed to solve it was:```
sudo apt-get install libkrb53 --reinstall
```So I guess the file just suddenly fell into the bitbucket or something.
Putting this solution down here for google to index should it be relevant to others.

- Arand

---

### Post by lidex on 2010-01-25
> **Arand said:**
> I experienced something quite similar on my jaunty install just now, starting X/GNOME failing completely, .session-errors complaining about 
I tried quite a few things, including fsck-ing, reinstalling nvidia drivers, removing .config/gnome-session and .ICAuthority.

However what finally seemed to solve it was:```
sudo apt-get install libkrb53 --reinstall
```So I guess the file just suddenly fell into the bitbucket or something.
Putting this solution down here for google to index should it be relevant to others.

- Arand

Yes it is. Thankyou!

---

### Post by sonicb00m on 2010-05-08
my ssh on debian was broken because of this shared library for some weird reason. The reinstall fixed it.

---

