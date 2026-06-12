---
title: "Firefox maxmium filesize of cache entries"
date: 2008-06-03
forum: General Help
---

### Post by &#923;&#926;&#915; on 2008-06-03
Hello everyone.

Does anyone know how to set up the maximum Filesize of entries in the Cache?, now it's limited to 64 MB in my installation.

when there is no option to config it, please tell the location in the source code which determines this issue

---

### Post by y-lee on 2008-06-03
I think you can change it in preferences.
In your firefox menu under Edit-->Preferences and then in your preferences window click on Advanced and then Network Tab. You should have an option to change cache size.

Note I am using FF2 but FF3 should be similar i think.

---

### Post by crossedout on 2008-06-03
I'm a little unclear as to whether you mean the cache file size or each entry in the cache.  Assuming you mean the cache file size:
In the address bar type about:config, then type browser.cache.disk.capacity into the search field.  Right click the entry and choose modify, enter the value you wish to use.

-Xout

---

### Post by &#923;&#926;&#915; on 2008-06-03
I mean the maximum filesize of a single entry in the cache - not the size of the cache - the cache is no file - it's a directory

---

### Post by scribu on 2008-06-23
> **&#923 said:**
> I mean the maximum filesize of a single entry in the cache - not the size of the cache - the cache is no file - it's a directory

I would also like to know if this is limited and if so, how can it be changed.

---

