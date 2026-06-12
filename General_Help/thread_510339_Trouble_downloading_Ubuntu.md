---
title: "Trouble downloading Ubuntu"
date: 2007-07-26
forum: General Help
---

### Post by Alfie on 2007-07-26
As concluded in my earlier [post]("http://ubuntuforums.org/showthread.php?p=3077144#post3077144") I downloaded and installed the 64-bit version of Ubuntu. This caused trouble installing Flash and Java. 

That`s why I now have tried to download the 32-bit version. I tried that from [http://no.releases.ubuntu.com/7.04/](http://no.releases.ubuntu.com/7.04/) and from [http://www.ubuntu.com/getubuntu/](http://www.ubuntu.com/getubuntu/). I even tried the Norwegian page [http://www.ubuntu.no/LastNed](http://www.ubuntu.no/LastNed). All with no luck.

Seems like the downloader starts, but then nothing happens when I decide to save to disk. If I try to open with File Roller everything is ok, but then I don`t get to save what I opened. 

Anyone else got this problem?

---

### Post by tronica on 2007-07-26
getting flash to work in 64 bit is easy, I always just instal 32bit flash then install nspluginwrapper, and you have flash. or use 32-bit firefox.

check this out

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox_.2864-bit.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox_.2864-bit.29)

---

### Post by Alfie on 2007-07-26
If that`s possible nothing would be better. I followed the descriptions as described, but it failed when I came to these to commands.

> 
sudo dpkg -i nspluginwrapper-0.9.91.2-1.x86_64.deb 
sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb
 

> 
alf@alf-laptop:~$ sudo dpkg -i nspluginwrapper-i386-0.9.91.2-1.x86_64.deb
dpkg: Feil ved behandling av nspluginwrapper-i386-0.9.91.2-1.x86_64.deb (--install):
 får ikke tilgang til arkivet: No such file or directory
Det oppsto feil ved behandling av:
 nspluginwrapper-i386-0.9.91.2-1.x86_64.deb

In english. Couldn`t access archive.


---

### Post by Alfie on 2007-07-27
Any suggestions?   :confused:

---

