---
title: "Recompiling ipsec-tools with libradius, libpam"
date: 2005-09-05
forum: General Help
---

### Post by koan on 2005-09-05
Hello,

I am attempting to use ipsec-tools for a remote access VPN gateway.  I am stuck with authentication, as the ipsec-toois build doesn't include libpam or libradius support.

So I need to recompile it with libpam and libradius support.

The configure command is

  ./configure --with-libpam=<folder> --with-libradius=<folder>

What I'd like to know is where I can get hold of the necessary libraries to make this work.

I have freeradius installed, which references libradius, but pointing the configure command at these files doesn't help.

Clearly I do not know what I am doing  :) 

Any help?

Thanks,

koan

---

### Post by ZaherM on 2005-09-05
In order to compile the *-dev packs should be installed.

Open Synaptic (or Kynaptic in case you are using Kubuntu).
Do search for **libpam0g-dev** and **libpam0g** install both.
Also search **libradius1-dev** and **libradius1** and install both.

Now try to run ./configure without any parameters.

I hope this will work and you will be able to compile :).

---

