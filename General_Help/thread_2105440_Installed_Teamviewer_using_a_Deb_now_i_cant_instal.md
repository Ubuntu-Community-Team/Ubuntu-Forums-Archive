---
title: "Installed Teamviewer using a Deb now i cant install ia32-libs help!"
date: 2013-01-16
forum: General Help
---

### Post by Inous on 2013-01-16
Hello there,

I'm currently trying to install a dedicated server for a game, unfortunately I cant because when I use the command sudo apt-get install ia32-libs I get this in return:

```
(a huge wall of text) then...

0 upgraded, 335 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/101 MB of archives.
After this operation, 249 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 95108 files and directories currently installed.)
Removing teamviewer:i386 ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/teamviewer.postrm): No such file or directory
dpkg: error processing teamviewer:i386 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 teamviewer:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Any help would be appreciated! I'm using Ubuntu 12.04

Thanks!

---

### Post by sudodus on 2013-01-16
Welcome to the Ubuntu Forums :-)

If you need to uninstall Teamviewer, run the deb file to do that: doubleclick on its icon in a file browser and click the button ***Uninstall***

And after that try your command
```
sudo apt-get install ia32-libs
``` again

If you want Teamviewer, maybe it works if you reinstall it after installing ia32-libs.

But there might be a conflict, so that only one of those works. In general, when you install something that is not in the repositories, it is not tested and endorsed by Canonical for Ubuntu, so there is no guarantee, that it works without conflicts with other software.

By the way, I have installed and used Teamviewer in 12.04 (64 bit-version), and I have not yet found any problems like yours.

---

