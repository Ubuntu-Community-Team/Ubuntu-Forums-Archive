---
title: "Installing Brother printer drivers in 16.04"
date: 2018-03-27
forum: General Help
---

### Post by comlbox on 2018-03-27
[SIZE=3]I'm using Ubutu 16.04LTS. I have a new Brother MFC-J985DW.  After some searching, phone calls and hair pulling, I got Brother to give me their link to the drivers.  Here's the link to Brother's site: [http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104](http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104).
[/SIZE]
[SIZE=3]Their instructions for installing the drivers hasn't worked. I can't find support in 16.04 for the 'superuser' Brother mentions, but tried to create a superuser with: "su -l".  But after entering the password (and one different from my usual one), I got "authentification failure."  I'm wary of going further with superuser, as I understand "sudo" should get me authority to make the changes, and I'd probably do some damage anyway.

Following Brother's instructions I get:
[/SIZE]
[FONT=courier new]>ira@ira:~/Downloads$ sudo su gunzip linux-brprinter-installer-2.2.0-1.gz
>No passwd entry for user 'gunzip'
[/FONT]
[SIZE=3]Trying without "su" I get: [/SIZE]

[FONT=courier new]>ira@ira:~/Downloads$ sudo gunzip linux-brprinter-installer-2.2.0-1.gz
>[sudo] password for ira: 
>gzip: linux-brprinter-installer-2.2.0-1.gz: No such file or directory
[/FONT]
[SIZE=3]Any help would be greatly appreciated.  Thanks.[/SIZE]

---

### Post by comlbox on 2018-03-27
I took a leap, set up the superuser and ran the Brother installation software.  After several failures including in the superuser instructions (--  for newbies like me: READ THE INSTRUCTIONS CAREFULLY!), I was able to install the printer successfully.  It works for printing and scanning (with gscan2pdf) from the PC to the printer; I'll check for scanning from the printer's dashboard to a file.

---

