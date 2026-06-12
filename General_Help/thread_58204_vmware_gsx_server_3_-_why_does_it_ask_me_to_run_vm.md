---
title: "vmware gsx server 3 - why does it ask me to run vmware-config.pl after every reboot"
date: 2005-08-19
forum: General Help
---

### Post by simion on 2005-08-19
I've got vmware gsx server 3 installed happily.  When I'm done I run the vmware-config.pl script.  Everything works, I've got a windows install running quite happily.  I can shut it down and start it up again with no problems.  Whenever I reboot though, I have to run the vmware-config.pl script again before it will start.  I can just keep hitting enter an accepting the defaults and everything works again.  Any ideas?  It sounds to me like it isn't writing a config file somewhere.  I've searched all over the place for a solution to this and can't find any other postings about it.

cheers
simion

---

### Post by mlmurray on 2005-08-19
I had the same problem with VMWare 4.5.2.  I actually had a problem where VMWare wouldn't compile the modules under kernels >= 2.6.11 and was refered to this patch (just run the "runme" script) and that fixed it.  It also fixed the problem with the having to re-compile the modules each time using Hoary.

Here's the link to the latest version of this script:  

[http://ftp.cvut.cz/vmware/vmware-any-any-update93.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update93.tar.gz)

I'm not 100% certain this works for version 3, but the problem you're having is certainly familiar.

---

### Post by atentik on 2008-03-09
Did you provide the installation code during installation? This can be obtained free from vmware site.

---

