---
title: "how to remove installed sl-modem sources"
date: 2005-08-08
forum: General Help
---

### Post by eeried on 2005-08-08
Hello,

I installed sl-modem-source_2.9.9a-1ubuntu4_386.deb
 -- very easy to install from the tar.gz source

Now I realised the winmodem needs a Conexant driver.

I don't know how to remove "make uninstall" doesn't do anything (missing target it says).

i don't have any sound any more and I suspect it's because of these modules.

Your help would be very much appreciated  ;-)

---

### Post by charlieg on 2005-08-08
Did you install the tar.gz or the .deb?  Your description is ambiguous although attempting 'make uninstall' to imply you used the tar.gz originally.

All make install usually does is to put the binary in /usr/bin or another of the 'bin' directories.  So search for the associated executable and delete it.  I'd be surprised if it did anything else and if it did it will be shown in the Makefile.

---

### Post by eeried on 2005-08-08
Hello,
Many thanks for your reply, charlieg!

I installed the deb package but then realized it only stuck a .tar.gz file in /usr/src

So I thought I had to extract this .tar.gz file and then compile and install the file. I now have a new dir: /usr/src/slmodem/

I have no experience at all with installing from source. 

Do I simply delete  /usr/src/slmodem/?

i'll look through /usr/bin as well and delete all slmodem files if any.

I'm feeling very dumb!

---

