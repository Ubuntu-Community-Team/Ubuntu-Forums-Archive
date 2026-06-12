---
title: "Synaptic Package manager"
date: 2005-09-03
forum: General Help
---

### Post by rold50 on 2005-09-03
Hi,

When I run Synaptic Package manager I get this messages:

W: Couldn't stat source package list [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/universe Packages (/var/lib/apt/lists/mirror.mcs.anl.gov_pub_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)




any way to fix that?

---

### Post by bjweeks on 2005-09-03
Go to terminal and type ```
sudo apt-get update 
``` if you get any errors post them here.

---

### Post by rold50 on 2005-09-03
ok that fixed that problem

but I have a different problem now.
I'm trying to install freeglut3-dev

when I click on apply I get this message:

Some of the packages could not be retrieved from the server(s).
('Failed to open file.  ' [IP: 140.221.37.133 21])

and then when I click yes, I get 
W: Failed to fetch [ftp://mirror.mcs.anl.gov/pub/ubuntu/pool/main/x/xorg/xlibmesa-glu-dev_6.8.2-10_i386.deb](ftp://mirror.mcs.anl.gov/pub/ubuntu/pool/main/x/xorg/xlibmesa-glu-dev_6.8.2-10_i386.deb)
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 140.221.37.133 21]

---

### Post by bjweeks on 2005-09-03
If you dont need it remove that repository because the package is question is in ubuntu main repository. Rember if you remove to do a apt-get update.

---

