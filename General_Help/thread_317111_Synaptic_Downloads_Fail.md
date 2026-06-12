---
title: "Synaptic Downloads Fail"
date: 2006-12-11
forum: General Help
---

### Post by jsjs94 on 2006-12-11
I've recently installed Xubuntu 6.10.  At first Firefox was having all sorts of timeout problems, but I disabled IPv6 and that seemed to solve that problem.

The Synaptic Package Manager is still having timeout problems though. Below, are the  two types of messages I'm receiving.  

[INDENT]W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vim/vim-perl_7.0-035+1ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vim/vim-perl_7.0-035+1ubuntu5_i386.deb)
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vim/vim-python_7.0-035+1ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/v/vim/vim-python_7.0-035+1ubuntu5_i386.deb)
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)[/INDENT]

I've tried the URL's in Firefox and been able to download the packages without difficulty.  Any thoughts on what's going on?  

- JS

---

### Post by scrooge_74 on 2006-12-11
i saw something about this yesterday in another thread, remove the us. part from the address in the sources.list or inside the repositories config

then do sudo apt-get update
sudo apt-get upgrade

It seems there is a problem with those US servers

---

### Post by organica on 2006-12-11
Are you on a network?  Are you using static IP or DHCP?

---

### Post by scrooge_74 on 2006-12-11
DHCP but you can change the address in the repositories to point to another mirror with no problem

command line then write sudo nano /etc/apt/sources.list

yesterday somebody was talking about problems with those mirrors

---

### Post by jsjs94 on 2006-12-12
Hehay!

Thanks for the advice. It worked like a charm.  Packages download and install.

- JS

---

