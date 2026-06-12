---
title: "How to get a default kde"
date: 2006-08-28
forum: General Help
---

### Post by darkhatter on 2006-08-28
if I use the packages on the kde ftp are they stock and unchanged. I just want to get the default kde without anything changed. how it is in slackware.

what I'm trying to do is get a plain kde with out any kubuntu changes.

---

### Post by daller on 2006-10-05
Hmm... I don't know...

But would certainly wanna know!

---

### Post by aysiu on 2006-10-05
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

```
sudo dpkg-reconfigure gdm
```

---

### Post by kerry_s on 2006-10-05
Have you tried just installing kdebase or kde-core. I think as long as you don't grab kubuntu-desktop you won't get that kubuntu stuff. I'm using a server-install+konqueror+openbox and then i built up from there kdm,kwin,ksmsever,...Now i can run a kde session with no bloat and it's very fast. I'm sure on my next install i'm just going to go with kdebase instead of installing everything 1 by 1 cause i installed almost the exact same thing as that meta package. Anyways after the install you'll have stuff that looks for the kubuntu stuff but won't find it(mostly themes), so you'll have to fix that.Here's what i plan for my next server install->

sudo apt-get install x-window-system-core xterm kdebase

Okay i found one branding, it's on the stock home page of the konqueror web browser, i have mine set to google now so i didn't even remember till i started looking around, but that start up page can be disabled by following the link and then it will just show a blank page.

---

### Post by darkhatter on 2006-10-06
I just want to remove all of the ubuntu branding in kde, I found a way to do it just install kpersonalize and run it.

---

