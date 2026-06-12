---
title: "I have no name! - ubuntu 12.04 LTS"
date: 2013-08-04
forum: General Help
---

### Post by GmHMwzr on 2013-08-04
I have a very weird error I'm not sure how this has happened, when I remotely ssh in I get the following

I have no name!@xx:~$ id
uid=1000 gid=1000(ubuntu) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),110(netdev),111(admin),1000(ubuntu)
I have no name!@xx:~$ ssh localhost
You don't exist, go away!
whoami: cannot find name for user ID 1000

I still have full sudo access
/etc/passwd - looks fine
/etc/shadow - looks fine

This happened around the time I saw the error: [http://pastebin.com/v7NsCjtc](http://pastebin.com/v7NsCjtc)

any ideas :(

---

### Post by oldfred on 2013-08-04
Linux is not space friendly. And I did not think you could create a user name with spaces?? I thought it defaulted to your first name and all lowercase.

Most places in Linux you have to escape a space with quote\ for\ spaces or in some cases \040 instead of the space or use "quote for spaces". 
But it just is better to use CamelCase, under_score or justonename rather than spaces.

[http://www.tuxfiles.org/linuxhelp/weirdchars.html](http://www.tuxfiles.org/linuxhelp/weirdchars.html)

---

