---
title: "Can't download repository keys"
date: 2006-11-07
forum: General Help
---

### Post by shingalated on 2006-11-07
I'm trying to enable the repositories to download and install software and when I reload the package list with 'apt-get update' or in synaptic, I am unable to download any of the gpg keys that are required.  The router that I am on uses port 8080 for remote management and can not be disabled.  This is what I get when I do 'sudo apt-get update':
```

Err http://www.getautomatix.com dapper Release.gpg
  Could not connect to 192.168:8080 (192.0.0.168), connection timed out
```

I get this for each key that needs to be downloaded.  Is there a way to get and install the keys without using port 8080?

---

