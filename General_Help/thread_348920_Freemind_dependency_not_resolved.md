---
title: "Freemind dependency not resolved"
date: 2007-01-29
forum: General Help
---

### Post by useResa on 2007-01-29
I have installed [FreeMind]("http://freemind.sourceforge.net/wiki/index.php/Main_Page"), free mind mapping software, using [these  deb files]("http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=355162") and gdebi.

All files were installed successfully with the exception of plugin that provides the possibility to export files to PDF and SVG. Gdebi indicates> [COLOR=red]**Error: Dependency is not satisfiable: libbatik-java**[/COLOR]Does anyone have a suggestion how I can solve this?
Is there a repository that does have this package?

Thanks in advance

---

### Post by eombah on 2007-01-30
Hi useResa,  :-)

From [http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux) :

*#  sadly, libbatik-java and libjgoodies-forms-java don't seem to be part of any repository; so, you should add the Debian repository as described in the above notes, but be careful to not break your installation with too many pure Debian packages. *

and there it says:
[I]
You can always download the required .deb files from the Files section ([http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831](http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831)) and install them by hand, using dpkg or whatever, but the comfortable way is to add the following lines to your /etc/apt/sources.list:

   deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) <version>/
   deb-src [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) <version>/

Note 
    you need to replace <version> by either unstable or experimental: I use unstable for software for which I'm pretty sure it will make it into the official Debian repository, experimental for the rest. Currently, only experimental contains interesting things. [/I]

good luck!
Bart.

---

### Post by useResa on 2007-01-31
eombah :D,

Thank you for your suggestions, since your suggestions did put me on the track to solving this issue.

All I missed was the libbatik-java.deb file so I used my good friend "Google".
This helped me find [this page]("http://dir.filewatcher.com/d/Debian/all/contrib/libs/libbatik-java_1.5.1-1_all.deb.4318692.html") from which I could download the missing package.
After installation of this package (again using GDEBI) also the last plugin installed without any problems.

FreeMind is now operational with all plugins (btw: works great the export to pdf).

---

### Post by jefrey on 2007-09-11
Thanks so much for your suggestions!

I got it to work, but I had to use libbatik-java_1.6-3_all.deb from [this filewatcher page]("http://www.filewatcher.com/m/libbatik-java_1.6-3_all.deb.4839938.0.0.html").  

Enjoy.  :grin:

---

