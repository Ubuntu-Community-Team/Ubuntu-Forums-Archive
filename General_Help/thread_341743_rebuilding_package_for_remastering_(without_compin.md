---
title: "rebuilding package for remastering (without compinling)"
date: 2007-01-19
forum: General Help
---

### Post by diarrhoe on 2007-01-19
Hi,

I want to make my own ubuntu-ISO with an edited default configuration file for the openssh-server.

I extracted the openssh-server-package using dpkg -e for the debian-commandfiles and dpkg -x for the program files. Then I added a ssh-subdirectory in the /etc-directory of the package an wrote my own sshd_config there. 
After that I rebuilt the package with dpkg-deb -b und copied it to my extracted ISO-Directory und rebuilt the ISO.

After installing the base-system I tried to install the ssh-package from the CD using apt-get install (and aptitude) but it told me only that the package was broken.

I would be very glad if anyone could help me.

---

