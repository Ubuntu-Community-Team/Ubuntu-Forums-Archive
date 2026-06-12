---
title: "Synfig SVN make error ?"
date: 2007-12-09
forum: General Help
---

### Post by cywhale on 2007-12-09
Hello. Im trying to compile latest svn synfig on Ubuntu Gutsy, all dependancies installed as described in the build howto. 'make'ing synfig studio i get the following error (last lines of &#8216;make&#8217;):

creating synfigstudio make[3]: 

```
Verlasse Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/src/gtkmm&#8217; make[3]: Betrete Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/src&#8217; 
make[3]: Für das Ziel »all-am« ist nichts zu tun. make[3]: Verlasse Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/src&#8217; 
make[2]: Verlasse Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/src&#8217; Making all in images 
make[2]: Betrete Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/images&#8217; 
synfig -q installerlogo.sif -o installerlogo.png &#8211;time 0 
synfig(5496): error: Size of Canvas mismatch (app:592, lib:560) 
FATAL: Synfig Version Mismatch make[2]: * [installer_logo.png] Fehler 9 
make[2]: Verlasse Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio/images&#8217; 
make[1]: [all-recursive] Fehler 1 
make[1]: Verlasse Verzeichnis &#8216;/home/cywhale/synfig-src/synfigstudio&#8217; 
make: ** [all] Fehler 2
```

'Fehler 2' means 'error 2'
'Verlasse Verzeichnis' means 'leaving directory'

Any idea what is going wrong here ? Looked in the bugtracker, ubuntu forums.

I'd appreciate any help.

---

