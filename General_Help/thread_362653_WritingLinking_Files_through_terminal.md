---
title: "Writing/Linking Files through terminal"
date: 2007-02-15
forum: General Help
---

### Post by zraffz on 2007-02-15
I created a link to the plugin of JRE for mozilla but I cant write to the mozilla-firefox folder, can somebody tell me how to; via terminal would be fine.
The linked file is:
/home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link to libjavaplugin_oji.so
and Mozilla Firefox's Plugin folder is:
/usr/lib/mozilla-firefox/plugins

---

### Post by dcstar on 2007-02-15
> **zraffz said:**
> I created a link to the plugin of JRE for mozilla but I cant write to the mozilla-firefox folder, can somebody tell me how to; via terminal would be fine.
The linked file is:
/home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link to libjavaplugin_oji.so
and Mozilla Firefox's Plugin folder is:
/usr/lib/mozilla-firefox/plugins

```
sudo cp /home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link /usr/lib/mozilla-firefox/plugins
```

---

### Post by zraffz on 2007-02-15
zraffz@zraffz-desktop:~$ sudo cp /home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link /usr/lib/mozilla-firefox/plugins
cp: cannot stat `/home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link': No such file or directory

---

### Post by dcstar on 2007-02-15
> **zraffz said:**
> zraffz@zraffz-desktop:~$ sudo cp /home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link /usr/lib/mozilla-firefox/plugins
cp: cannot stat `/home/zraffz/Desktop/jre1.5.0_11/plugin/i386/ns7/link': No such file or directory

Well, that's exactly what YOU put in your previous post, how about you find out the filename you want to copy and use it in the command?

---

### Post by zraffz on 2007-02-15
the name of the file is libjavaplugin_oji.so

---

