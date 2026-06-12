---
title: "Firefox problems!"
date: 2006-12-01
forum: General Help
---

### Post by championchap on 2006-12-01
Hey guys! 
A problem im coming across when using firefox is really starting to irritate me.. wonder if any of you could give me a hand?

I'm running a fully updated Dapper box at the moment.. but a while back i installed firefox 2.0 following some guide i found online.

Trouble is, now whenever i go onto a site with an embedded flash on it, firefox just closes itself without warning.. this is especially irritating considering all those flash banner ads and embedded youTube videos out there!

Any suggestions would be appreciated.. this is really starting to get to me!

---

### Post by cleentrax on 2006-12-01
This is a flash problem. Have you installed the non-free plugin for firefox? You might try the beta of version 9, which, in my experience, is less buggy and plays more content than v7.

---

### Post by SyvanX on 2006-12-01
Try going to the Macromedia Site and getting [Flash for Linux]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4").  If you install to your firefox directory it might fix the flash plugin.  I think the site has installation instructions.

---

### Post by championchap on 2006-12-01
> **cleentrax said:**
> This is a flash problem. Have you installed the non-free plugin for firefox? You might try the beta of version 9, which, in my experience, is less buggy and plays more content than v7.

Well, i just tried to view a flash 7 file (I know because i made it myself some time ago)
but the browser crashed again.. thing is, im sure ive installed the flash player 7 plugin before now!

Ill try reinstalling it, but could there be a chance that i somehow have the two browsers installed? 1.5 and 2.0?

---

### Post by cleentrax on 2006-12-01
I'm running Firefox2 in Edgy, not Dapper. I don't know whether installing plugins through apt will apply to Firefox2 or just v1.5.

Do you have the same problem in both, or just v2?

---

### Post by championchap on 2006-12-01
Well, im not even sure if thats what ive done
i followed a guide on some site, and if that is what has happened, then it must have removed 1.5 from my applications menu and replaced it with a 2.0 shortcut.

But its the only thing i can think of..

---

### Post by AndyCooll on 2006-12-01
This is a known bug. If you do a search for Firefox 2.0 problems you'll find there are a number of workarounds.

The one that worked for me was:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down and make sure the ColourDepth is set to 24. FF works fine for me now.

:cool:

---

