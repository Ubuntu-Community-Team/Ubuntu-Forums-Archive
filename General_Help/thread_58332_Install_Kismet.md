---
title: "Install Kismet"
date: 2005-08-19
forum: General Help
---

### Post by 0tk on 2005-08-19
HI,

I am trying to install kismet.  Though it is asking me for the ubuntu installation CD.  IS there a way to change the media type to always update from the internet instead of using the Ubuntu CD?

Regards,
0tk
[http://www.0tk.net](http://www.0tk.net)

---

### Post by 0tk on 2005-08-19
HI guys,

Fixed this issue myself :)

Regards,
0tk
[http://www.0tk.net](http://www.0tk.net)

---

### Post by starkruzr on 2005-09-26
Maybe I'm a complete idiot, but I can't find kismet in the package list in either Add/Remove or Synaptic.  I tried to build it from source and discovered I don't have a development environment.  Installed gcc and it told me "checking for C compiler default output file name... configure: error: C compiler cannot create executables."  WTF?

Also, I can't su to root?  Huh?  I *know* what my password is (or thought I did?) and it's not working.

---

### Post by majikstreet on 2005-09-26
sudo su    and then enter your password for your account..

Also, sudo apt-get install build-essentials

and yes it's in apt-get/synaptic: [http://packages.ubuntu.com/hoary/net/kismet](http://packages.ubuntu.com/hoary/net/kismet)

you may need to add extra repo's: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

