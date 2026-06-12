---
title: "Java 6 Plugin for Swiftfox 2.0.1"
date: 2007-02-07
forum: General Help
---

### Post by true_friend on 2007-02-07
I want to install java 6 plugin for swift fox 2.0.1 installed in /opt
i installed java 6 plugin from synaptic but it is not working with it. seems it only installed in konqueror(using kubntu edgy).
can some one guide me to install/copy/link (what ever is req) in opt/swiftfox/plugins directory
Regards
True_Friend

---

### Post by taurus on 2007-02-07
See if the new java plugins is in /usr/lib/firefox/plugins.  If it is, then just copy it over to /opt/swiftfox/plugins.

---

### Post by true_friend on 2007-02-07
nops it is not there :(

---

### Post by igknighted on 2007-02-07
It's not really the prefered way, but if you can't find libflashplayer.so on your system, go to adobe.com and download the flash 9 installer, but instead of running it's script, if you extract the archive the file I mentioned above is there, all you have to do is move it to the /opt/swiftfox/plugins folder as such:
```
sudo cp /path/to/libflashplayer.so /opt/swiftfox/plugins/
```
and you should be good to go.

---

### Post by true_friend on 2007-02-07
i do not know the path where it is installed
and it is java plugin flashplayer is ok in swift fox.

---

### Post by phossal on 2007-02-07
The name of the Java plugin is: *libjavaplugin_oji.so* The way it works is not totally unlike the flashplayer plugin, because you *do* want to create a sym link in the browser plugins directory pointing back to the JRE (sometimes within a JDK) holding the plugin.

---

### Post by old_geekster on 2007-03-12
> **taurus said:**
> See if the new java plugins is in /usr/lib/firefox/plugins.  If it is, then just copy it over to /opt/swiftfox/plugins.
Thanks so much.  I did exactly what you suggested and it worked like a charm. :)

I don't understand why it doesn't install in SF, the same as it does in FF.

---

