---
title: "[SOLVED] Weird Firefox amnesia"
date: 2008-05-13
forum: General Help
---

### Post by jhmiller42 on 2008-05-13
Running Hardy, Firefox 3b5 is doing some really odd things. First, it's not paying attention to my cookies. When I go to my Google homepage, I'm greeted by the 'login' page. Yahoo mail and the Ubuntu forums do the same thing, even though checked the "remember me" box. I checked the two most obvious problems: FF preferences are indeed set to keep cookies until they expire; and cookies are properly kept, or at least they show up under *Edit>Preferences>Privacy>Show Cookies*. So it seems like FF is just ignoring them.

Second, when I start FF, it takes me to the last page visited, even though the preferences are set to start with my home page.

Ideas?

---

### Post by jhmiller42 on 2008-05-18
Bump.

---

### Post by hakazvaka on 2008-05-18
I am a new Ubuntu user (from this morning =), and I am plesently suprised. I am from BiH so sorry on bad English.

I have just the SAME problem. SAME

Any solution? (maybe it's because of it's beta version)

---

### Post by Arwen on 2008-05-18
I have the same problem too 
> when I start FF, it takes me to the last page visited, even though the preferences are set to start with my home page.
 (in ubuntu 8.04) with the beta version.Also it loads pages too slowly while my internet connection is OK(epiphany and opera both load faster).
I think I'll go back to 2.0.0.14,I've generally been unlucky with beta versions..

---

### Post by jhmiller42 on 2008-06-05
Fixed. I'm not sure about the details, but apparently the default Firefox profile was looking for my preferences/cookies/etc. in the wrong place. 

Solution:

Launch Firefox's Profile Manager:

```
firefox -profilemanager
```

Create a new profile and select it as default. You'll have to rebuild your bookmarks and plugins, which can be a pain in the ****. I'm sure there's a cleaner way to do it -- editing the default profile to look in the right place -- but this works and it's quick.

---

