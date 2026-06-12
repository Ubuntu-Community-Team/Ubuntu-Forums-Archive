---
title: "Java in hardy"
date: 2008-04-28
forum: General Help
---

### Post by theadmiral on 2008-04-28
I am unable to get the java plugin to work in firefox 3 (or other browsers but i only really care about firefox). It worked in gutsy with firefox2 i have read many instructions on here that require linking to the plugin but i have tried that to no avail. Does anyone know of a good step by step walkthrough or have any other ideas for me to try?

---

### Post by coolaj86 on 2008-04-28
Have you tried installing it through "Add/Remove..." under the applications menu?

Under "Show: All Available Applications" you should be able to find the non opensource "Sun Java 6.0 plugin". Try a simple uninstall, reinstall.

---

### Post by theadmiral on 2008-04-28
I have tried that a few times with no luck.

thanks for trying

---

### Post by TheSe7enthSin on 2008-04-28
Try this code in the terminal

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```

---

### Post by quixote on 2008-04-28
TheSe7enthSin's suggestion may be all you need.  For some reason Sun's defaults for Java are to stick it in places outside of the usual path, and then nothing can find it.  That suggestion puts a link so that other programs can find java.

If it doesn't work, then the most complete instructions I've found are here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) .  

Fair warning: they're complete, so they're long.  Search on the page for "java"  There's a bunch of stuff about 1/3 - 1/2 the way down.

---

### Post by theadmiral on 2008-04-28
Thanks, that was a long walkthrough with much excess information. It did work though so i cant complain. I think what i didn't do that i need to do was run

```
sudo update-alternatives --config java
```

i hope my code posting worked kinda new here

Thanks again and i hope anyone else having this problem can find their solution here

Anyone want to tell me how to mark this as solved?

---

