---
title: "Mplayer Proxy - I'd like to get rid of Windows, but.."
date: 2006-07-15
forum: General Help
---

### Post by T-Stone on 2006-07-15
Dealing with proxies in Ubuntu has not been easy, with many config files to create or edit. The latest problem I have is that I can not view any video embedded video online because of proxy problems. I have inslalled mplayer with Automatix, but it will not play them.

Because of this I have to boot my computer each morning with Windows so that I can check out some news video. Please help me avoid starting my day with Windows!

Is there a way to get mplayer to work with a proxy?

---

### Post by sdowney717 on 2007-01-25
you can try

export http_proxy=http://ipadress:portnumber

I still cant get it to work on some streaming microsoft stuff like at cnn.com either

Let me know if you can get it working with socks and if so how you did it.
Enough people are behind proxies, you would think they would let you configure mplayer with a proxy configuration.

You can also type in 'about:config' in mozilla browser address bar and add 2 line to hand off mms, but it still doesnot help the proxy problem.


[http://mplayerplug-in.sourceforge.net/faq.php](http://mplayerplug-in.sourceforge.net/faq.php)

Does the plugin work with proxies?
Updated 10/3/2003 As of version 1.0pre2 all supported Mozilla protocols (http,https,ftp,file,etc) are handled through Mozilla. So if Mozilla is configured to use a proxy the content should be able to be downloaded. The only exception to this is mms:// streams which are not a supported Mozilla protocol. However, proxy support via mplayer may solve the problem. I have been told that mplayer respects the HTTP_PROXY variable.

HTTP_PROXY=http://your.proxy:80
export HTTP_PROXY

http_proxy might need to be in lower case for some configurations.

Also if you write a script to encapsulate mplayer it might work. For example: something like this might work with a socks proxy

#!/bin/sh
LD_PRELOAD=/usr/local/lib/libtsocks.so
export LD_PRELOAD
/usr/local/bin/mplayer.orig

copy mplayer to mplayer.orig
Name that script /usr/local/bin/mplayer

---

### Post by sdowney717 on 2007-01-25
export http_proxy=http://192.168.0.2 then colon then 8118
colons become smileys and this messes it up.

---

### Post by sdowney717 on 2007-01-25
also, if you want to see what it currently is set to, then in terminal type set or env

---

### Post by sdowney717 on 2007-01-25
you can also edit the etc/profile file and put this in here using quotes

#proxy var
HTTP_PROXY="http://192.168.0.2:8118"

---

### Post by viduliya on 2008-01-25
Oh my god this is such an unexpected problem.  I was using Ubuntu smoothly from home and decided to install it at work.  I was totally surprised to find that I can no longer listen to my favorite radio station with streaming audio from mplayer as I do from home.

I have tried every thing and just can not get mplayer to work with a proxy that require authentication.  I have tried setting environment variables like http_proxy and HTTP_PROXY with the following:  

"http://myuserid:mypasswd@myrproxy:myport".

I have no luck so far.  :confused:

Is it even possible to get mplayer working with a proxy with authentication?  If someone got this going please let me know how.   

Thank you.

---

