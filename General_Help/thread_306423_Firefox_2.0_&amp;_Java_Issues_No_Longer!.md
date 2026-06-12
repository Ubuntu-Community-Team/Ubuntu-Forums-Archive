---
title: "Firefox 2.0 &amp; Java Issues No Longer!"
date: 2006-11-24
forum: General Help
---

### Post by klepto on 2006-11-24
I am assuming you have firefox 2.0 already installed
apt-get install sun-java5-bin 
apt-get install sun-java5-jre
apt-get install sun-java5-plugin

ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /opt/firefox/plugins

and it should work perfectly.

I noticed that linking the plugin to /usr/lib/mozilla-firefox would work for firefox 1.5
but not firefox 2.0

I have a question about the flash 9: 
When I watch google/youtube video it stops after 2 seconds of play and if I uninstall it
then all the sites nag about not having flash 8.

---

### Post by futureman on 2006-11-25
i followed these directions and it made firefox crash every time i started it.

---

### Post by hippyjim on 2006-11-27
Me too - started it from konsole, and every time I go to my favourite applet (logmein.com) I get -

```
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success
```

I figure it's not liking the jre - how do I remove it?

---

### Post by nadamsieee on 2006-12-02
I am running Ubuntu 6.10 - the Edgy Eft, Firefox 2.0, and Sun Java SDK 1.5.0.

This worked perfectly for me:

```
$ cd /usr/lib/firefox/plugins/
$ sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```

---

