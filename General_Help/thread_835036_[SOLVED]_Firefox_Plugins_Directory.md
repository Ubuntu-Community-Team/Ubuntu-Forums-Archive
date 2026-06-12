---
title: "[SOLVED] Firefox Plugins Directory"
date: 2008-06-20
forum: General Help
---

### Post by thornate on 2008-06-20
Where is the Firefox 3.0 plugins directory in Hardy? I'm trying to create a symbolic link to the Java plugin (following instructions on the [Java website]("http://java.com/en/download/help/5000010500.xml#enable")). I've done it in 
/usr/lib/firefox-3.0/plugins
/usr/lib/firefox/plugins
/usr/lib/flashplugin-nonfree
/usr/lib/mozilla/plugins

And none of them seem to work - when I restart firefox, it is not in the plugin list. So where is the correct place to put the link?

---

### Post by Zorael on 2008-06-20
/usr/lib/mozilla/plugins is the one shared by all Mozilla-based browsers; Firefox, Swiftweasel, etc.

What symlink did you create? edit: Doh, meant ls -l, not ln -s. I suck.
```
$ ls -l /usr/lib/mozilla/plugins
```

---

### Post by thornate on 2008-06-20
```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by Zorael on 2008-06-20
I honestly don't see why that shouldn't work. Double-check that you don't have any other symlinks in other plugin directories pointing to the OpenJDK plugin (which seems to be royally buggy, at least on my systems.)

If I'm not mistaken, that's the /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so.

Of course, I'm *assuming* you're running a 32-bit environment, or at the very least a 32-bit browser in a 64-bit environment.

---

### Post by thornate on 2008-06-20
I'm in a 32 bit environment.

A clash with gcjwebplugin would seem likely as it is in my plugin list, disabled. The only problem is that none of the plugin directories have a symlink to that particular plugin. 

Is there any way to select the file and see where there are links to it?

---

### Post by Zorael on 2008-06-20
/etc/alternatives/xulrunner-1.9-javaplugin.so

If you want to create java symlinks it's actually better to link to that one. Then you can use update-alternatives to switch between your java plugins.

```
$ sudo update-alternatives --config xulrunner-1.9-javaplugin.so

There are 2 alternatives which provide `xulrunner-1.9-javaplugin.so'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
 +        2    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/gcjwebplugin.so

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'xulrunner-1.9-javaplugin.so'.
```

If Sun's plugin isn't there to pick, you'll need to install it as an alternative. Then rerun the above command. **edit:** forgot --install. :<
```
$ sudo update-alternatives --install /etc/alternatives/xulrunner-1.9-javaplugin.so xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so 90
```


Lastly go over your plugins folders, make sure they link towards that /etc/alternatives symlink.

---

### Post by thornate on 2008-06-20
Hurrah, it works now. I can play Bubble Bobble!

Thanks
:KS:KS

---

