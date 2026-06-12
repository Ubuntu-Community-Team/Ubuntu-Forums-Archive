---
title: "Dell DSET on Ubuntu?"
date: 2007-02-19
forum: General Help
---

### Post by Grax on 2007-02-19
I'm trying to run Dell's DSET on my Ubuntu 6.10 server.  Here is a link to the program:

[ftp://dropbox.us.dell.com/dropbox2/ips/DSET/DSET-Linux/delldset_v1.3.0.bin](ftp://dropbox.us.dell.com/dropbox2/ips/DSET/DSET-Linux/delldset_v1.3.0.bin)

Then I run the application, it runs, but gets an error when I try to install/create a report.  The error is:

Error: RPM had a problem installing or upgrading DSET. Aborting

I know that this isn't a supported linux flavor, so stated by Dell, however is there a way to get it to run?

Thanks,

Andrew

---

### Post by Cathead Fred on 2007-02-20
Hi Grax,

  Sorry to hear about your problem. I believe the file you are trying to install is a .rpm file. This won't work in Ubuntu. You need to convert the .rpm file to a .deb file. Here is a link to instructions on how to do this with a package called alien.

[http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/)

Good luck and post your progress.

Cathead Fred

---

