---
title: "Broken GRUB needs help"
date: 2013-01-17
forum: General Help
---

### Post by D0natell0 on 2013-01-17
Hi, 
I'm trying to fix an old PC running Ubuntu 8.04, using a Live-CD with the boot-repair tool.

I get the message "Please enable a repository containing GRUB2 in the software sources of Ubuntu 8.04.4 LTS (sda1)".

How do I do this please?

Am I right in thinking the 'sources.list' file is missing something?
Background: Hardware on this machine isn't supported in newer versions, so I'm stuck with this old Ubuntu release.

Thanks in advance.

---

### Post by sudodus on 2013-01-17
Ubuntu 8.04 LTS was a good version, but it passed end-of-life in April 2011. It's long gone, without any security updates. This is OK, if you run it locally without connecting to the internet, but very open to attacks when connected to the internet.

Maybe it will be easiest to repair it from an install drive of the same version, that you can find at this link

[[COLOR="red"]http://releases.ubuntu.com/8.04/[/COLOR]]("http://releases.ubuntu.com/8.04/")

---

### Post by oldfred on 2013-01-17
8.04 server is still supported, but desktop is not. Not sure if grub2 has been made available for 8.04 or not as it was grub legacy.

       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
    
You might want to just install Lubuntu or Xubuntu. 

       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
Lubuntu one stop thread - amjjawad
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
[https://wiki.ubuntu.com/Lubuntu#System_Requirements](https://wiki.ubuntu.com/Lubuntu#System_Requirements)

---

