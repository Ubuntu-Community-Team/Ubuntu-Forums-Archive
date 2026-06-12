---
title: "Making java plugin work with mozilla firefox"
date: 2005-06-30
forum: General Help
---

### Post by adwait on 2005-06-30
Hello,

I have been trying to get the java plugin to work with firefox but to no avail. I dowloaded the rpm file from the java site, used alien to convert it to deb and then installed it. I copied the file libjavaplugin_oji.so to ./mozilla/plugins but nothing!

Adwait

---

### Post by bored2k on 2005-06-30
[QUOTE=adwait]Hello,

I have been trying to get the java plugin to work with firefox but to no avail. I dowloaded the rpm file from the java site, used alien to convert it to deb and then installed it. I copied the file libjavaplugin_oji.so to ./mozilla/plugins but nothing!

Adwait[/QUOTE]
 Try this method:
[http://www.ubuntuforums.org/showpost.php?p=235934&postcount=30](http://www.ubuntuforums.org/showpost.php?p=235934&postcount=30)

---

### Post by wellery on 2005-06-30
if that doesn't work then try this. I use this method:

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

### Post by adwait on 2005-06-30
I have tried the second method but nothing....

The first method Ill try later as a last resort, because my day time downloads are limited and I have downloaded java about 3-4 times today itself!

I also tried [http://ubuntuforums.org/showthread.php?t=44414&highlight=firefox+java](http://ubuntuforums.org/showthread.php?t=44414&highlight=firefox+java). When I type java -version I get the proper output. I then created the proper links mentioned in that posts, but firefox keeps telling me I don't have the plugin installed.

---

### Post by adwait on 2005-06-30
Nevermind, I got it to work. I just had to remove the libjavaplugin_oji.so file I had copied into ~/.mozilla/plugins as part of my previous attempts to get java started. Thanks to all who tried helping :)

---

