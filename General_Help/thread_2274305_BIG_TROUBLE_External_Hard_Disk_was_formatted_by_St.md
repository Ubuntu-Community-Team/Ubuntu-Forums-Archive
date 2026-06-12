---
title: "BIG TROUBLE: External Hard Disk was formatted by Startup Disk Creator"
date: 2015-04-19
forum: General Help
---

### Post by David_Esparza on 2015-04-19
Hello, everyone. Sorry for my English, I'm from Mexico. Well, I got this problem when I was creating an Ubuntu Startup Disk while I had connected my USB stick aside my External Hard Disk (1 TB) to my PC, in Ubuntu 14.10. I made a mistake and I selected the External Hard Disk instead of the USB, so the program started to format the Hard disk and install the Startup Disk on it, and it don't even finished the process because it appeared an error message about the DB or something (I was in panic so I closed it quickly) before I could canceled it! (or that's how I remember; I´m not sure if I canceled it before: everything happened fast...) The Startup Disk was not created but all the files were erased. I'm not having luck recovering the lost data using some recovery programs 'cause I think the 'format method' that the Startup Disk Creator used is "uncommon"; or because the file size is very large so the standard recovery program can't finish the job. Or maybe the error that I mentioned has to do with it, but I don't really know. I should be able to recover the files 'cause I have not added anything to the hard disk since I formatted it. Many people recommend me Photorec, but the problem with this program is that it will give me the files without no properties or names or folders, and when it comes to 600 GB... that involve a lot of work.  Well, I think that's all, friends. Please... Can anyone tell me how to recover this hard disk? I will appreciate very much the help that you can give me.

---

### Post by Bashing-om on 2015-04-19
David_Esparza; Happens;

But a long hard road, and tough to recover from . Why backups are so important.

Here is the background and possible means.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
 The tool 'scalpel' may be of value:
```

apt-cache show scalpel

```
You will have to install the tool and read the man page for usage.
Then there is the industry standard 'testdisk' .
The directions for 'testdisk' :
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) <- written in a user-friendly way and introduces you to testdisk in a gentle way:
[http://ubuntuforums.org/showthread.php?t=2112112](http://ubuntuforums.org/showthread.php?t=2112112)

[INDENT][INDENT]a sad state of affairs;
[INDENT][INDENT][INDENT][INDENT]there is hope
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by David_Esparza on 2015-05-05
Thank U, man :)

I'll try

---

### Post by RobGoss on 2015-05-05
When working with any distributions it can sometimes be tricky and sometimes we make mistakes like this but! we can surely learn from all of this and one day we'll get good at this. Good luck

---

