---
title: "Install Java version 8 with PPA which will automatically keep it up to date"
date: 2014-03-25
forum: General Help
---

### Post by Cavsfan on 2014-03-25
If you have used the previous manual method I had been posting when a new Java version came out you will need to manually uninstall that version from Firefox plugins before adding the PPA.

Enter [COLOR=#000000][COLOR=#0000FF]sudo rm -r -v /opt/java[/COLOR][/COLOR]
Then [COLOR=#000000][COLOR=#0000FF]rm -v ~/.mozilla/plugins/libnpjp2.so[/COLOR][/COLOR]

Once that has been done click on the blue link in my signature [[COLOR=blue]_Install Java via WEB UPD8 PPA_[/COLOR]]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")
There are instructions there from the WEB UP8 site to install a PPA and Java version 8. It will keep itself up to date without any need to manually enter commands.

Oracle only offers Version 7 Update 51, so this is a big improvement.

This method will work on Ubuntu and Linux Mint.

---

### Post by Cavsfan on 2014-03-28
I was definitely not trying to take credit for this, just wanted to get the word out that Java version 8 can be found. Even if Oracle doesn't offer it.

---

### Post by Cavsfan on 2014-04-03
In Firefox enter ```
about:plugins
``` in the address bar and you should see this:

**Java(TM) Plug-in 11.0.2**

File: libnpjp2.so
Path: /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnpjp2.so
Version: 11.0.2
State: Enabled
Next Generation Java Plug-in 11.0.2 for Mozilla browsers

In Chromium enter **chrome://plugins/** in the address bar and you should see this:

[COLOR=#000000][FONT=Ubuntu]**Java(TM)** - Version: 11.0.2
Next Generation Java Plug-in 11.0.2 for Mozilla browsers[/FONT][/COLOR]

---

