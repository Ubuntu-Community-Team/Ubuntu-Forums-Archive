---
title: "During update getting dependency error"
date: 2013-04-17
forum: General Help
---

### Post by phantom21 on 2013-04-17
During an update on ubuntu 12.04 LTS getting this error

Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic amd64 3.2.0.40.48 [1,722 B]
Fetched 1,722 B in 0s (12.8 kB/s)  
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.36.43); however:
  Version of linux-image-generic on system is 3.2.0.40.48.
 linux-generic depends on linux-headers-generic (= 3.2.0.36.43); however:
  Version of linux-headers-generic on system is 3.2.0.40.48.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Have tried sudo apt-get install -f, and it returns the same error.

Have already tried sudo apt-get update, sdo apt-get autoremove, sudo apt-get clean and then sudo apt-get install -f again.

No joy.

How can I fix this?

Thamks

Mark

---

### Post by gifford on 2013-04-17
You might try setting software sources to main server instead of server for the US. Also for update, I am assuming that you have pre-released updates checked?

---

### Post by phantom21 on 2013-04-20
OK.  Checked Main server.  Did not have pre-released updates checked.  will try now.

Thanks.

---

### Post by phantom21 on 2013-04-20
That did not help.

Mark

---

