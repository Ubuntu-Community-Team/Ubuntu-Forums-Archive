---
title: "Webmin with chroot'd bind"
date: 2006-12-14
forum: General Help
---

### Post by can2002 on 2006-12-14
Following the excellent guide at [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10) I've configured my first Ubuntu box (Edgy Eft on Sparc), having been a firm RH/FC user previously.

I configured bind to run chroot'd as per the guide and that's working fine.  The primary function for the box/s is to run bind and I wanted to add Webmin to make this process a little easier.  The installation from the tar.gz file worked fine, and I'm able to manage the bind configuration without issue.

The one problem I do have is starting/stopping bind from within Webmin.  If I leave the webmin bind module as default and run without chroot, it works; however with chroot it doesn't.  When I select the options to run under a chroot directory and specify a different user/group, I get "failed to start bind" followed by the normal response from /usr/bin/named with incorrect options.

I appreciate it's probably more a Webmin issue than Ubuntu, but if anyone could assist I would be grateful!

Cheers,
Chris

---

### Post by CoMfUcIoS on 2008-02-04
On Webmin -> Servers - > Bind Dns Server on the upper left there is a link 'Module Config'

On the ' Chroot directory to run BIND under' change it from none to '/var/lib/named/'

Also on the 'Command to start BIND' change it from default to '/etc/init.d/bind9 start'

Worked for me :)

---

