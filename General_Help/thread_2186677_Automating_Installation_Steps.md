---
title: "Automating Installation Steps"
date: 2013-11-08
forum: General Help
---

### Post by Vannyi on 2013-11-08
On the website [http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_for_Linux#Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_for_Linux#Ubuntu) , I found the installation steps to install XBMC.  They consist of the below 5 steps

[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] python-software-properties pkg-config
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] software-properties-common
[COLOR=#C20CB9]**sudo**[/COLOR] add-apt-repository ppa:team-xbmc**/**ppa
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get update**[/COLOR]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] xbmc
I'm just curious, because I'm testing a couple of things on a VM that I am reloading regularly, is there any way to copy these 5 steps into a Linux version of a "batch file" which I could double click to automate the install of XBMC?  I know there is a version in the software center, but it is an older version.

Thank you

---

### Post by Kirboosy on 2013-11-08
A [shell script]("http://linuxcommand.org/writing_shell_scripts.php") with the commands in it would be easist way to automate the install.

---

