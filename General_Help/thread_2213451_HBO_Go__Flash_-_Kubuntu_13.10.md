---
title: "HBO Go / Flash - Kubuntu 13.10"
date: 2014-03-26
forum: General Help
---

### Post by Jonathan_Dominguez on 2014-03-26
**new install** - Acer Aspire M5-581t

Browser - prefer Chrome, will use Firefox - issue exists in both apps

Issue - HBO Go is no-go, Flash plug-in is installed. I select target, get a nice black screen

What I've tried - installed Pipelight (for Netflix) and the Flash plugin for it / no-go
- Package Manager - toggled between flashplugin-installer and adobe-flash plugin / no-go
- installing Flash via adobe site - APT for Ubuntu 10.4+ / no-go "The channel 'saucy-partner' is not known"

Any help or direction would be greatly appreciated. Thanks in advance.

Loaba
Jonathan

---

### Post by monkeybrain20122 on 2014-03-26
Works for me. Ubuntu 13.10, Firefox 28 and just flash 11.2 from the repository. 

I also installed Pipelight flash but I am not actually using it. The interesting thing is that installing  pipelight-flash brings in widevine which allows system flash(not work for pepper flash in Chrome) to decode certain drm contents, so may be flash 11.2 would not have worked on this site if pipelight-flash was not installed. [http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html](http://www.webupd8.org/2014/01/pipelight-brings-widevine-support-for.html)

Can't check if pepper flash from Chrome works because I am outside the U.S and can't access the site without some unblocker, have it in Firefox but don't bother to install it in Chrome.

---

### Post by Jonathan_Dominguez on 2014-03-26
Thanks for the response - new development

As I said before, I don't prefer Firefox but I will use it if needs be. On that note, after much monkeying (purging/reinstalling flash), I now get a new message in HBO Go/Firefox - something to the effect of "you have too many strams on this computer".

Newer development - that message is gone and I'm back to the black screen.

---

### Post by Jonathan_Dominguez on 2014-03-26
SOLUTION - installed the HAL repository and now HBO Go works.

---

