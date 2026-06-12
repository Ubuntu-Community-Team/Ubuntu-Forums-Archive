---
title: "Flash plugin Hardy Heron"
date: 2008-05-21
forum: General Help
---

### Post by eeried on 2008-05-21
Hello,

I don't install the flash-plugin-non-free package from the Ubuntu repos because I don't want to **install** Flash. 

What I do is download the tar.gz file from the Adobe web site. This is actually necessary if you have a blog on wordpress.com as the lastest flash plugin is required.

Then I decompress the archive and copy one file ```
libflashplayer.so 
``` to /usr/lib/firefox/plugins

This worked fine in Gutsy. Now I can see the file in /usr/lib/firefox/plugins but the plugin doesn't show when you type  about:plugins in Firefox.

I tried the Gnash plugin and it works on some flash.

So what's your experience? In the meantime I'll try copying libflashplayer.so  in the mozilla plugins dir

BTW it is a pity Firefox3 won't support SVG animation (unless my information is outdated) since SVG is the thing as it is based on XML, just like ODF or XHTML. Flash is a thing of the past even if it'll go on being used on the web for the next 100 years or so.

---

### Post by eeried on 2008-05-21
As Tom--d says here [http://ubuntuforums.org/showthread.php?t=802047&goto=newpost](http://ubuntuforums.org/showthread.php?t=802047&goto=newpost)

Firefox3b5 plugins dir isn't in  /usr/lib/firefox/ as I thought  but quite logically :) /usr/lib/firefox-3.0b

---

