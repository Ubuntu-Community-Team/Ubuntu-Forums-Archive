---
title: "synaptic couldn't resolve archives.ubuntu.com"
date: 2005-03-24
forum: General Help
---

### Post by hyspah on 2005-03-24
i have been trying a system update yet synaptic keep saying:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-perl/libxml-perl_0.08-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-perl/libxml-perl_0.08-1_all.deb)
  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-grove-perl/libxml-grove-perl_0.46alpha-11_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libx/libxml-grove-perl/libxml-grove-perl_0.46alpha-11_all.deb)
  Could not resolve 'archive.ubuntu.com'


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/aptconf/aptconf_0.8_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/aptconf/aptconf_0.8_all.deb)
  Could not resolve 'archive.ubuntu.com'

---

### Post by TasKiNG on 2005-03-24
Do you connect to the  internet directly or through a proxy server?

I connect through a server and had the same problem. to get around this I had to set a variable by adding:-

export http_proxy=http://yourserveraddress:port

I put this in /etc/profile so it was set each time.

Hope this helps

---

