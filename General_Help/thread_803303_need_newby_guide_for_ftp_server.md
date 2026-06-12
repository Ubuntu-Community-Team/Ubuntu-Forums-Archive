---
title: "need newby guide for ftp server"
date: 2008-05-22
forum: General Help
---

### Post by sdowney717 on 2008-05-22
I have been looking at proftpd vsftpd and truthfully, I cant figure out where the files go that a client could download.
is there any easy guide out there to tell me step by step?

I simply need an anonymous ftp server setup on the local network. 
Where I can put 2 files. And I need to know the website access url that would point to these 2 files in that folder.

It seems like all the documentation assumes you already know a lot of stuff and deals mainly with specialty configuration parameters.

I got further with this until I got a cryptic warning
[http://gentoo-wiki.com/HOWTO_vsftpd](http://gentoo-wiki.com/HOWTO_vsftpd)
vsftpd: refusing to run with writable anonymous root

'What this cryptic message means is that your ftp root directory is writable. Since it's anonymous, vsftpd doesn't like that. chmod -w the ftp root to get rid of this common error. '

OK, this statement assumes you know where to chmod -w something, but gives no idea where to do this



nothing in here about where files go?
[http://www.proftpd.org/localsite/Userguide/linked/userguide.html](http://www.proftpd.org/localsite/Userguide/linked/userguide.html)
[http://cosi.clarkson.edu/docs/faq/proftpd.html](http://cosi.clarkson.edu/docs/faq/proftpd.html) 
[http://vsftpd.beasts.org/](http://vsftpd.beasts.org/)

---

### Post by latna on 2008-05-22
Look in your vsftp.conf and look for a directive called "anon_root".

```
man vsftp.conf
```

---

