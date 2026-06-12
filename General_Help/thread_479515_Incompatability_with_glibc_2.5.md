---
title: "Incompatability with glibc 2.5"
date: 2007-06-20
forum: General Help
---

### Post by Blofeld07 on 2007-06-20
Sorry I'm pretty new at Ubuntu so some of this might not make the most sense.  I'm currently using an up-to-date version of Feisty.

I'm  having an issue with installing PGI portability 6.0.  This is an older version that's needed to run another program I have.  Unfortunately the installer gives the error "ERROR: unknown glibc version (2.5).Exiting..."  I know that the newer version of the software is compatible, but it doesn't work with the other program I need.  
The documentation:  [https://www.pgroup.com/doc/pgiwsrn608.pdf](https://www.pgroup.com/doc/pgiwsrn608.pdf)  
Here it says that the release supports up to glibc 2.3.5 and gcc 4.0.0

I have two questions:

1.  Is there a way of installing an older version of glibc along side the newer version and make the installer happy?  As I understand it these can't be downgraded.

2.  Is there some end around way of getting the old version of PGI Portability installed?  Maybe a live CD using the older version of glibc that could be used to install it?  It seems that the Portability directory just needs to be added to  /etc/ld.so.conf.

Thanks

---

