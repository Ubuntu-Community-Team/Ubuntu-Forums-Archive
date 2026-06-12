---
title: "CertTools Hangs"
date: 2007-09-19
forum: General Help
---

### Post by jts on 2007-09-19
Whenever I try and generate a private certificate, Ubuntu seems to hang.

certtool --generate-privkey --bits 32 --outfile mekey.pem

I get no CPU usage, errors or memory usage.  Anyone have any suggestions?

---

### Post by jts on 2007-09-21
According to the GENTOO WIKI ([http://gentoo-wiki.com/Certificate_Authority](http://gentoo-wiki.com/Certificate_Authority)), if there is no entropy available, the certtool will hang.  So how do you create it in on UBUNTU server?  Login to another SSH window and begin typing?

---

### Post by jts on 2007-09-21
Apologize for replying to my own thread, but hopefully this will save someone else some time.

If you are using VMWARE, this is how I was able to get it to work.  
I ran the cert generation tool in an SSH console.I went into the VMWARE guest console and generated some traffic.  Traceroute to google, "cat /var/log/*.log > /dev/null", etc.

It seemed to generate enough entropy to create the certificates.   If someone would confirm that you can do this with 2 separate remote ssh sessions, that would put the icing on the cake.

---

