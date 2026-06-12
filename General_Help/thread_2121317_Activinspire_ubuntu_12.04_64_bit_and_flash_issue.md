---
title: "Activinspire ubuntu 12.04 64 bit and flash issue"
date: 2013-03-01
forum: General Help
---

### Post by davidvandoren on 2013-03-01
Hi there! Nice design editor here at Ubuntuforums

I've got a problem with my interactive whiteboard software (activinspire) and my 64 bit Ubuntu 12.04.

I had flash already installed and working. After installing activinspire the software did not want to start so I found a solution on their forum and enered this into the terminal 
```
sudo ln -s /usr/lib/i386-linux-gnu/libjpeg.so.8 /usr/local/lib32/libjpeg.so.62
``` 

It did the trick and activinspire just opened up as supposed to. 

However, it gives me a warning that I have to install flash. The audiofiles won't play within the software as supposed to. 


Flash still works great in Firefox though. I reinstalled a the version from the adobe website but no avail.

Any suggestions? 

By the way the software is great, works on my 32 bit system.

Thanks!

---

