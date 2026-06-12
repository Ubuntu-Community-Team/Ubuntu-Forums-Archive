---
title: "Java Plugin for Firefox"
date: 2005-10-06
forum: General Help
---

### Post by Coriander on 2005-10-06
Hi there,

I want to install the java plugin for firefox. I know apt-get has the jre - but I have j2sdk installed and so it seems to make more sense to use the JRE that comes with it...
I've done this:

sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

which gives this error when I try to start the browser.

$ firefox
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success


Any ideas what i'm doing wrong?

Thanks!

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=Coriander]Hi there,

I want to install the java plugin for firefox. I know apt-get has the jre - but I have j2sdk installed and so it seems to make more sense to use the JRE that comes with it...
I've done this:

sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins

which gives this error when I try to start the browser.

$ firefox
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success


Any ideas what i'm doing wrong?

Thanks![/QUOTE]
My guess is that "ns7-gcc29" is the culprit - this shows that the plugin was compiled with gcc2.9. Hoary uses GCC 3.x 

Use "ns7" instead - it works for me.

---

### Post by Coriander on 2005-10-07
[QUOTE=Alexander Kirillov]My guess is that "ns7-gcc29" is the culprit - this shows that the plugin was compiled with gcc2.9. Hoary uses GCC 3.x 

Use "ns7" instead - it works for me.[/QUOTE]

Good guess. :)
That makes sense, and it worked, thanks!

---

