---
title: "Firefox 3 java runtime"
date: 2008-03-04
forum: General Help
---

### Post by Techwiz on 2008-03-04
I recently installed Firefox 3 and can't get Java runtime to work. I had it in Ff 2. But not in 3. How can I get it? I tried the Java web site and followed instructions, but to no avail. Ideas?

---

### Post by Kingsley on 2008-03-05
Do you still have FF2? If so, Java might work if you symbolically link the java .so file from the FF2 plugins folder to the FF3 plugins folder.

sudo ln -s /path/to/ff2plugin.so /path/to/ff3pluginfolder

---

### Post by Techwiz on 2008-03-05
No I don't currently have Ff2. And the /usr/lib/firefox/plugins folder does contain a symbolic link to *a* Java plugin.

---

### Post by nettucu on 2008-03-06
[FONT="Courier New"]in /usr/lib there are many firefox*:
       firefox/
       firefox-3.0b3/
       firefox-addons/
       firefox-plugins/

     Apparently 3.0b3 reads from /usr/lib/firefox-3.0b3

/usr/lib/firefox-3.0b3/plugins is a symlink to 
/usr/lib/firefox-addons/plugins

    and in the /usr/lib/firefox-addons/plugins there is no symlink to the java plugin. You need to symlink the javaplugin in /usr/lib/firefox-addons/plugins dir:

     ```
sudo ln -s /etc/alternatives/firefox-3.0-javaplugin.so /usr/lib/firefox-addons/plugins/libjavaplugin.so
```

     Make sure you symlink the /etc/alternatives version. Like this whenever you switch java versions you get the right plugin version.[/FONT]

---

