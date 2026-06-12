---
title: "VMware Server 1.0.4 on 7.04 (x86_64)"
date: 2007-10-15
forum: General Help
---

### Post by bwa32 on 2007-10-15
Does anyone have a guide for making this work?  I suspect I'm missing some 32 bit libraries (trying to run the vmware console with an absolute path -> 'file not found' and ldd doesn't believe that 'vmware' is an executable.  The contents of /lib seems comparable to /lib64.

vmware-config.pl fails because it cannot run /var/lib/vmware/openssl to generate SSL certificates with the ldd symptoms described above.

Again, this is on a 64 bit installation.

I'm an experienced Linux user (12 years) but a newbie to Ubuntu/Debian, so I'm not quite sure how to proceed.

I have other questions as well, but if I can't use VMware, I will have to use something else. :-|

Thanks!

---

### Post by JohnnySkidmark on 2007-10-17
[How To Install VMware Server + MUI 1.0.4 On Ubuntu 7.04]("http://www.howtoforge.com/vmware_server_1.0.4_plus_mui_ubuntu_7.04")

---

