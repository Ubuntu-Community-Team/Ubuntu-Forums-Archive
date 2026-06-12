---
title: "cannot open shared object file: (id.so.conf)"
date: 2014-07-03
forum: General Help
---

### Post by g35celicaz on 2014-07-03
I am trying to install lesssfs with Berkeley DB and I get the following error:

./lessfs: error while loading shared libraries: libdb-6.0.so: cannot open shared object file: No such file or directory

The readme files for installation tell me to add the following into id.so.conf: 

/usr/local/BerkeleyDB.6.0/

(although, I just noticed that there are more than several of these files, and I don't know if I put it in the right one)

So, in the end, the file looks like this:

include /etc/ld.so.conf.d/*.conf
/usr/local/BerkeleyDB.6.0/

Could this be the reason for the error?

Thanks for your help in advance

---

