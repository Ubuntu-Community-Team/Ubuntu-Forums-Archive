---
title: "Can not open display"
date: 2013-06-15
forum: General Help
---

### Post by JamesDonaldChilds on 2013-06-15
I have an ssh server and a 12.04 serber install. I have an x server on my pc with putty connected to the server as it is headless. I have been succesfully running gparted and gedit through my x server on my pc but all of a sudden it wont access my x server and says cannot open display. also throws an error about gtk. any help appreciated.

---

### Post by zero2xiii on 2013-06-15
Hay,

please supply more information, what error are you getting?
Are you using the -X or -Y options when  ssh'ing into the server?

Thanks

---

### Post by JamesDonaldChilds on 2013-06-15
The error is literally "cannot open display:" and I'm using putty which just allowed me to tick x11 forwarding. Previously I did not have to use -x or -y and pulling up the GUI of gparted or gedit worked flawlessly, I don't even know what these do.

---

### Post by JamesDonaldChilds on 2013-06-15
Now I'm getting a different error.


"xxx@xxx:~$ sudo gedit
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedCannot open display:
Run 'gedit --help' to see a full list of available command line options."

Note: running "sudo gedit" previously worked flawlessly, created a gui on my windows machine.

---

### Post by JamesDonaldChilds on 2013-06-15
bump, Help please! ;]

---

### Post by 3rdalbum on 2013-06-16
You should never use 'sudo' with graphical programs. Instead you need to use 'gksudo' or 'pkexec'.

This may be why you are getting this kind of error. Check the permissions of the .Xauthority file on the server - it should be readable and writable by the user.

---

