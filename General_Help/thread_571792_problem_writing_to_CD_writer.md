---
title: "problem writing to CD writer"
date: 2007-10-09
forum: General Help
---

### Post by GuyNZ on 2007-10-09
Hello, 
I have upgraded to 7.10 in an attempt to fix writing to my CD-ROM and it hasn't helped.When I put a blank disk in it doesn't seem to recognise it as a blank disk and asks me to use a blank disk for writing. However the output of lshw suggests it should allow writing? Not sure why it says scsi when it is an IDE drive. Any ideas appreciated. 

Guy

*-cdrom
                description: CD-R/CD-RW writer
                product: CD-Writer+ 9100
                vendor: HP
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0a
                serial: [HP      CD-Writer+ 9100 1.0a Oct29 ,  MY0025E
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

---

### Post by Scunizi on 2007-10-09
I have the same problem with a HP dvd740 w/ lightscribe.. Used it about 4 times then it just quit recognizing ANY blank disk.. really weird..  I ended up buying a new dvd writer (not HP)

---

### Post by JJNova on 2007-10-12
Heh. I have a 740 that has done the same thing. I'm under the impression that it has something to do with burning libraries to be honest. Windows users have the problem also, but it can be fixed be uninstalling/reinstalling their burning software (or reformatting the whole thing)

---

