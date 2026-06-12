---
title: "Brother MFC-7340 Scan and Print Instructions for 15.10"
date: 2016-05-14
forum: General Help
---

### Post by timothy11 on 2016-05-14
Here are  commands to install packages for MFC-7340 on Ubuntu 15.10 for scanning and printing that I consolidated from previous posts.

Driver deb packages are available here:
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128)

sudo apt install apparmor-profiles
sudo apt-get install apparmor-utils
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo mkdir /var/spool/lpd
sudo apt-get install sane-utils psutils tcsh
sudo apt-get install lib32stdc++6
sudo dpkg -i brmfc7340lpr-2.0.2-1.i386.deb
sudo dpkg -i cupswrapperMFC7340-2.0.2-1.i386.deb
sudo dkpg -i brscan3-0.2.13-1.amd64.deb
sudo dpkg -i brscan3-0.2.13-1.amd64.deb
sudo dpkg -i brscan-skey-0.2.1-3.amd64.deb
sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb


# 1. Open "/lib/udev/rules.d/40-libsane.rules" file.
# 2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
# If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"". 
# The lines to be added (remove the leading '#' as this was added to make this and executable shell script).


# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

---

