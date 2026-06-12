---
title: "init: ureadahead main process (241) terminated with status 5"
date: 2012-12-27
forum: General Help
---

### Post by polaatx on 2012-12-27
Hello, I get the following message when booting into my newly installed 10.04. It stops loading at this message permanently and doesn't go further. Any help would be appreciated. Do I have to reinstall? 

*init: ureadahead main process (241) terminated with status 5*

Hardware: acer aspire 3680 laptop

---

### Post by rnerwein on 2012-12-27
> **polaatx said:**
> Hello, I get the following message when booting into my newly installed 10.04. It stops loading at this message permanently and doesn't go further. Any help would be appreciated. Do I have to reinstall? 

*init: ureadahead main process (241) terminated with status 5*

Hardware: acer aspire 3680 laptop
hi
think i can't help you much - but error 5 is defined as:

#define EIO          5  /* I/O error */

cheers

---

### Post by polaatx on 2012-12-27
> **rnerwein said:**
> hi
think i can't help you much - but error 5 is defined as:

#define EIO          5  /* I/O error */

cheers

thanks for response. What does 

#define EIO          5  /* I/O error */

mean?

---

### Post by rnerwein on 2012-12-28
> **polaatx said:**
> thanks for response. What does 

#define EIO          5  /* I/O error */

mean?
hi
the given PID 245 shows me it is a very early systemprocess.
i/o means (mostely) a process want to access a non available device block (bad block)
it can be a network access to. have a look in /var/log/boot.log, syslog and kern.log
for more error messages 
ureadahead is reading data during boot up into the memory. this is done for faster boot and is standard (what i now) in ubuntu 10.04
cheers

---

