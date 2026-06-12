---
title: "GDM could not write to your authorization file"
date: 2007-03-27
forum: General Help
---

### Post by spankymasterc on 2007-03-27
Well im getting fustrated and i dont know what to do plz plz help! i have my ubuntu 6.10 edgy eft and dual booting Vista.....

Well i dont know how or what cause an error but everytime i try to log in i get this error
 
> "gdm could not write to your authorization file. This could mean that you are out of disk space ot that your home directory could not be opened for writing. In any case, it is not possible to log in.

i have tried just about everything like 
> Sudo dpkg-reconfigure gdm
> Sudo dpkg-reconfigure xserver-xorg
> sudo dpkgs-reconfigure -phigh xserver-xorg

> Cd /home/tweeter/
sudo rm .ICEauthority
sudo /etc/init.d/gdm restart

and alot more and have no luck plz anyone help im desperate i dont wanna reinstall becuase my ubuntu was customized to the ***..... lol and i have loads of software 

The Hardrive is not out of space i used df -h and it shows it almost emty only 15% full plz help and thx in advance:guitar:

---

### Post by aysiu on 2007-03-27
Two things to try.

**First thing to try**:
Boot into recovery mode.

Type ```
chown -R tweeter:tweeter /home/tweeter
reboot
``` and then try logging in again.

**Second thing to try**:
Boot into recovery mode.

Type ```
sudo adduser test
reboot
``` and then try logging in as *test* (instead of *tweeter*). If test works, we'll work from there.

---

### Post by spankymasterc on 2007-03-28
ok it worked but now it start and all i see get is a black screen and nothing happens so i do ctrl + alt + backspace and then Crtl + Alt + F1 and log in there and type in startx and i get this :

```
Xlib: Connection to ":0.0" refused by server
giving up.
Xlib: "invalid MIT-Magic-Cookie -1 key
Xlib:Cannot connect xserver(or sumthin like that)
```

---

### Post by aysiu on 2007-03-28
I don't know what that message means, but these links (please explore them) seem to indicate it has something to do with the switching of users trying to use a different user's configuration file. Did you do some kind of *su* command?

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/59495-authontication-error-xlib-invalid-mit-magic-cookie-1-key.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/59495-authontication-error-xlib-invalid-mit-magic-cookie-1-key.html)
[http://lists.apple.com/archives/x11-users/2005/Jun/msg00017.html](http://lists.apple.com/archives/x11-users/2005/Jun/msg00017.html)
[http://lists.opensuse.org/opensuse/2001-02/msg00062.html](http://lists.opensuse.org/opensuse/2001-02/msg00062.html)

---

### Post by hyperspaced on 2007-05-30
See this thread:

[https://launchpad.net/ubuntu/+source/gdm/+bug/35217](https://launchpad.net/ubuntu/+source/gdm/+bug/35217)

It is a bug.

Here are the files that GDM writes at startup:

> 
+ /tmp/.gdm_socket for the GDM daemon and GUI program to talk to each other
  properly. Without the socket being setup, GDM probably would still work
  though the GUI program wouldn't be able to access the config file and would
  instead revert to the compiled-in defaults (e.g. your theming would probably
  be wrong). Features that require the socket to be working (such as
  automatic/timed login or any gdmflexiserver --commands) would also not work.
  Perhaps moving the socket to /var/tmp might make it less likely you'd have
  problems here?

+ GDM uses /tmp for the fallback Xauth key directory if the normal xauth
  directory (UserAuthDir in the GDM configuraiton) is also full. If GDM can't
  write xauth files, then it probably wouldn't let the user login. If both
  UserAuthDir and /tmp are full, this could be a problem with GDM not allowing
  users to log in at all.

+ /tmp/.ICE-unix, /tmp/.X11-lock, and /tmp/.X11-unix are also used. Not sure
  how GDM will break if it couldn't write these files. I'm guessing this might
  be the problem that causes GDM to fail to allow login when /tmp is full.

+ If the user's $HOME is full, it will put the .xsession-errors file in /tmp
  instead. Probably not a big deal if these don't get written, though I'm not
  sure what GDM does if it can't write them.



It would be a good idea to check the permissions of the /tmp folder.
I ran into this bug a couple of hours ago and although I freed enough disk space, I still couldn't log-in.

---

