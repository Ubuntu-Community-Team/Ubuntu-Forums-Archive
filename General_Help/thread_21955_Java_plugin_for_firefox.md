---
title: "Java plugin for firefox"
date: 2005-03-24
forum: General Help
---

### Post by Lost on 2005-03-24
Ok I've done this before but forgot how to do it. Something to do with creating a dynamic link right? Can someone assist?

---

### Post by bnutting on 2005-03-24
This might help: [http://www.ubuntulinux.org/wiki/AddingJavaSupport/view?searchterm=java](http://www.ubuntulinux.org/wiki/AddingJavaSupport/view?searchterm=java)

---

### Post by capitan.harlock on 2005-03-24
Here I did all the right way, but java doesn't work for Firefox: symbolyc link to java-plugin is where it must be and java itself is installed 

java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

Flash plugin is also not working properly: falsh menus are shown, but no text in them...
I installed flash through apt-get, all is perfectly working (same relases) with Mandrake...

Oh, I just found out java is perfectly working with Opera 8 (beta 3)... Opera does not use java-plugin, but java itself

---

### Post by bnutting on 2005-03-25
What does your /usr/lib/mozilla-firefox/plugins directory look like?

---

### Post by bnutting on 2005-03-25
Oh and how about your ~/.mozilla/plugins ?

---

### Post by Dracontopes on 2005-03-25
[QUOTE=Lost]Ok I've done this before but forgot how to do it. Something to do with creating a dynamic link right? Can someone assist?[/QUOTE]
 [http://www.ubuntuguide.org/#jre-mozilla](http://www.ubuntuguide.org/#jre-mozilla)

:)

---

### Post by kb00heda on 2005-03-25
What about this? I downloaded and installed the deb-package, which seems to work fine, even though the manually installed JAVA did the job too.

[http://www.ubuntuforums.org/showthread.php?t=21975](http://www.ubuntuforums.org/showthread.php?t=21975)

/David

---

### Post by capitan.harlock on 2005-03-25
[QUOTE=bnutting]What does your /usr/lib/mozilla-firefox/plugins directory look like?[/QUOTE]

This way (all plugins seems to be correctly linked and flash is working, after all, even if not as expected)

flashplayer.xpt@    libjavaplugin_oji.so@  nphelix.so@
libflashplayer.so@  mplayerplug-in.so@     nphelix.xpt@

---

### Post by Psquared on 2005-03-25
[QUOTE=capitan.harlock]This way (all plugins seems to be correctly linked and flash is working, after all, even if not as expected)

flashplayer.xpt@    libjavaplugin_oji.so@  nphelix.so@
libflashplayer.so@  mplayerplug-in.so@     nphelix.xpt@[/QUOTE]

Thats the way my mozilla-firefox/plugins and my mozilla/plugins directories look too. Except, that in my firefox-plugin, the libjavaplugin_oji.so file has a different icon. It looks like 3 different colored cubes. In the mozilla/plugins the file has a plain icon. I found that the java plugin is not installed for the Mozilla browser, but it is for Firefox. Does it only work for one browser? Why no java plugin for the Mozilla Browser?

Can I get java to work for both browsers? How?

---

### Post by capitan.harlock on 2005-03-26
[QUOTE=Psquared]Why no java plugin for the Mozilla Browser?
Can I get java to work for both browsers? How?[/QUOTE]

Well, if java plugin works fine for Firefox, should also work for Mozilla; you simply have to create a symbolic link for Mozilla plugins directory also, as you did for Mozilla-Firefox (default is  
ln -s /usr/bin/java/usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/libjavaplugin_oji.so - you must change to jre version you have installed, of course)

---

### Post by capitan.harlock on 2005-03-26
I found out the symbolic link in plugins directory is broken, but I cannot understand why...

---

### Post by Psquared on 2005-03-26
[QUOTE=capitan.harlock]Well, if java plugin works fine for Firefox, should also work for Mozilla; you simply have to create a symbolic link for Mozilla plugins directory also, as you did for Mozilla-Firefox (default is  
ln -s /usr/bin/java/usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/libjavaplugin_oji.so - you must change to jre version you have installed, of course)[/QUOTE]

When I do that it says the file (I guess it means link) already exists. However, as I said, the icon looks different. Can I safely delete the java icon in /mozilla/plugins (I don't want to disturb mozilla-firefox/plugins) and then run the command again?

---

### Post by chandra on 2005-06-07
After upgrading to mozilla-firefox 1.0.4~5.04ubp1+1.0.2-0ubuntu1, I
lost the use of my Java plugin.  I had also installed sun-j2re1.5 and 
sun-j2sdk1.5.  This is what I did to restore functionality:

1. ls -al /usr/lib/mozilla-firefox/plugins/libjavaplugin.so

gave

lrwxrwxrwx  1 root root 39 2005-06-06 17:00
/usr/lib/mozilla-firefox/plugins/libjavaplugin.so ->
/etc/alternatives/firefox-javaplugin.so

This was a broken symlink.

2. ls -al /etc/alternatives/firefox-javaplugin.so

gave

lrwxrwxrwx  1 root root 58 2005-06-07 01:47
/etc/alternatives/firefox-javaplugin.so ->
/usr/lib/j2sdk1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

3. cd /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/

gave

bash: cd: /usr/lib/j2sdk1.5-sun/plugin/i386/ns7/: No such file or
directory

4. dpkg -L sun-j2sdk1.5 | grep libjavaplugin_oji.so

gave

/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
/usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

5. Conclusion: the directory jre, sandwiched between j2sdk1.5-sun and plugin was missing in the existing symlinks.

6. Solution:

sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so

7. If you wish, you can also

sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/mozilla-javaplugin.so

and 

sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/netscape-javaplugin.so

8. Check that symlinks are not dead; restart mozilla-firefox, type about:plugins and confirm that the Java plugin is recognized.

---

