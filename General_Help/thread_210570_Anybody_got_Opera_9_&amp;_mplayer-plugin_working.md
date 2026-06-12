---
title: "Anybody got Opera 9 &amp; mplayer-plugin working"
date: 2006-07-07
forum: General Help
---

### Post by hanzomon4 on 2006-07-07
I've searched around but can't get mplayer-plugin working with opera.. I compiled from source with ```
./configure --enable-x --with-gecko-sdk=/path/to/gecko-sdk
``` .. and put the files in /usr/lib/opera.. but I only get a whit box were the video should be. :confused:  

Any suggestions, or better yet does anybody have it working?

---

### Post by hanzomon4 on 2006-07-07
Bump

---

### Post by hanzomon4 on 2006-07-11
I think I found the problem "libxpcom.so" fails to load here's the output from "opera --debugplugin" ```
operapluginwrapper: [plugin probing] /usr/lib/opera/plugins/libxpcom.so
operapluginwrapper: [plugin failure] (No 'mimedescription') /usr/lib/opera/plugins/libxpcom.so
```

libxpcom is in opera's plugin path I just have no Idea why it fails

---

### Post by hanzomon4 on 2006-07-14
Bump

---

### Post by Colonel Kilkenny on 2006-07-14
I think my.opera.com/forums may be better place to ask from..
I compiled it like you and no problems.

---

### Post by grizzly on 2006-07-16
Hi! 
I do have opera and mplayer plugin working! :)

First type "opera:plugins" ( witout quotes) to see if plugins are installed properly. If they are you will get a long list of plugins.

Are you sure you have gecko-SDK installed?? Chances are if you haven't installed it seperately, then you need to. DOn't bother looking in repos, ask me and I'll upload or better you can search the forums.

and .. I assume you have the codecs installed..

---

