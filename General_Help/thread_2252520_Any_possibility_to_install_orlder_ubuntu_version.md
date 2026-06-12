---
title: "Any possibility to install orlder ubuntu version?"
date: 2014-11-12
forum: General Help
---

### Post by Portaro on 2014-11-12
I have this graphic card - [Radeon 9200 PRO] , but I have many problems to play games on wine that I have for example MEDieval II total war, there are a pixel shader unsuported message, if I run wine with LIBGL_ALWAYS_SOFTWARE=1 the game works but very slowly.

I know that is impossible install the proprietary drivers on ubuntus.

But my question is there are some older version of Ubuntu that leave me to install catalyst drivers of the site drivers for linux?

And if I can** what is the method to install some packages on the older versions**, because maybe the repositories exists, I only need libreoffice, google-earth jdownloader and transmission.

Thanks!

---

### Post by grahammechanical on 2014-11-12
Each release of Ubuntu has its own repositories and when the release reaches end of life those repositories are closed. Not only that but the server location of those repositories are changed to the old-release.ubuntu.com

You can find old release here

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) 

But once installed you will not be able to update or install any applications unless you edit the sources list to change the repository addresses to old-release repository. Look at the Requirements section of this wiki page on upgrading an EOL release. That will show you what you need to do to the sources.list file.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by Portaro on 2014-11-12
Thanks for help me.

---

