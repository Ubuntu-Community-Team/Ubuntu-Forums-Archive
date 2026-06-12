---
title: "Repositories"
date: 2007-05-26
forum: General Help
---

### Post by ankursethi on 2007-05-26
This is not the first time I've had this problem. I cannot access in.archive.ubuntu.com, neither can I access archive.ubuntu.com. The DNS lookup is successful but the connection simply times out. I tried in Firefox, and the same thing happens. Any ideas what might be wrong? Are the repos overloaded or something?

>   Could not connect to in.archive.ubuntu.com:80 (91.189.89.8), connection timed out [IP: 91.189.89.8 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main iamerican 3.1.20.0-4.3
  Could not connect to in.archive.ubuntu.com:80 (91.189.89.8), connection timed out [IP: 91.189.89.8 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/ispell/ispell_3.1.20.0-4.3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/ispell/ispell_3.1.20.0-4.3_i386.deb)  Could not connect to in.archive.ubuntu.com:80 (91.189.89.8), connection timed out [IP: 91.189.89.8 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/i/ispell/iamerican_3.1.20.0-4.3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/i/ispell/iamerican_3.1.20.0-4.3_i386.deb)  Could not connect to in.archive.ubuntu.com:80 (91.189.89.8), connection timed out [IP: 91.189.89.8 80]


NOTE : My ISP does not block any ports.

---

### Post by ankursethi on 2007-05-26
I found a mirror :
[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/)

Is it okay to use it? This is what goes in the sources.list, right?
> [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) feisty main restricted
...and so on for other repos. Right?

---

### Post by ankursethi on 2007-05-26
Bump!

Can somebody **please** tell me whether using the UK Mirror Service is okay or not?

---

