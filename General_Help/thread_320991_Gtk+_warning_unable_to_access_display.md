---
title: "Gtk+ warning: unable to access display"
date: 2006-12-18
forum: General Help
---

### Post by Beowulf.1000 on 2006-12-18
Yesterday I installed Ubuntu 6.10, "Alternate" i386 CD (has additional boot menu items like rescue mode, etc), to my main PC on an extra hard disk (I have been using Mandriva 2006 on that PC but I am liking Ubuntu on my laptop and other PC).

Well, this "alternate" cd install is odd compared to the regular CD. I am having issues getting Synaptic up and running. I can become root (#) without doing sudo, but in a terminal with the root # prompt if I run synaptic I get an error something like "Gtk+ Warning: unable to access
display" so I can not bring up Synaptic for package management.  As user, $ prompt, I can bring up Synaptic with "synaptic" command but I can not do anything with it since I do not have admin privilages as user.  Synaptic does not even show up in the Gnome GUI menus like with the regular non-alternate CD install.

This alternate CD was a bit odd--- I remember the initial user being by default OEM, then I was able to add Beowulf as a user.  Then I was told to run some script oem-config or something close to that name, and then after that OEM was gone as admin user.  I also did I think 
  sudo passwd
to get a root # prompt without having to use sudo for root commands. So now I can get a root prompt by doing  "su -". But I can not bring up synaptic as root which really is not good.

I chose the non-alternate install just because it had more options on boot of the CD, and because the regular 6.10 CD had issues after install with a friend's laptop. But I am tempted to reinstall Ubuntu today and this time use the regular non-alternate CD, unless there is some simple thing I could do to solve this issue. Any ideas?

---

### Post by taurus on 2006-12-18
At the prompt (as regular user), run

```
gksudo synaptic
```

---

### Post by dalonso on 2006-12-18
From the shell:

```
su -
export DISPLAY=:0.0
synaptic
```

---

### Post by taurus on 2006-12-18
Don't do the "**su -**" thing!  Instead, log in with your username and password and open a terminal and run this command...

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

