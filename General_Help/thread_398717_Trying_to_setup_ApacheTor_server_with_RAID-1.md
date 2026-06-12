---
title: "Trying to setup Apache\Tor server with RAID-1"
date: 2007-04-01
forum: General Help
---

### Post by Kazol on 2007-04-01
I'm trying (for 4 weeks already) to get Ubuntu working on a PIII 800Mhz 256MB RAM for a web\tor server. It has 2x10GB HD that I want to configure as RAID-1.

1.Do you think I should install the text version (on the alternate cd)? I'm a beginner to Linux commands, and want a step-by-step guide for installing\configuring apache\tor, and enabling ftp for the web directories.

2.How do I configure RAID partitions? I have spent over 6 hours trying to do this, nothing worked. The only way is to (somehow) mount unmountable HDs and setup RAID-1 with Ubuntu already installed. I couldn't even open any hd using the live CD.

3.If I were to follow this article:
[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)
Should I have 3 HDs?-1 for OS, 2 for the actual data? Is it possible just to mirror the OS\data1 hd?

I would have installed Windows Server 2003 a long time ago, but I couldn't even configure RAID-1 on that! Maybe I'm doing something wrong-the help files were terrible-did not exactly specify what hd to convert to dynamic, etc.

---

### Post by MoLE on 2007-04-12
I would definitely go with the alternate or server CD for this task.  It is a server you're running after all! 

[http://users.piuha.net/martti/comp/ubuntu/raid.html]("http://users.piuha.net/martti/comp/ubuntu/raid.html")

This method would probably be your best bet.  No reason not to use the LTS release for a server, I hope?

---

