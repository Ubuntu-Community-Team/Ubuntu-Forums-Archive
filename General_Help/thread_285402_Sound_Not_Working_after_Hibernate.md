---
title: "Sound Not Working after Hibernate"
date: 2006-10-26
forum: General Help
---

### Post by kaptainlange on 2006-10-26
Last night my gf decided that my computer should hibernate.  It's never worked so I never do it, and for good reason.

When I woke up this morning my sound wasn't working and apt-get update is also not working.

The error I get when trying to play a file via command line with mpg123 is:

```
ALSA snd_pcm_open error: No such file or directory
```

apt-get update produces this error:

```
Err http://us.archive.ubuntu.com dapper-updates Release.gpg                    
  Connection failed [IP: 146.137.96.7 80]
```

I can ping those addresses, and the addresses resolved when pinging are actually different.  My internet is also seemingly fine, everything else seems to resolve the proper IP's.

Thanks ahead of time for any insight.

---

### Post by kaptainlange on 2006-10-26
I've fixed the apt problem, but sound is still a mystery for me, again any help would be appreciated.

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

