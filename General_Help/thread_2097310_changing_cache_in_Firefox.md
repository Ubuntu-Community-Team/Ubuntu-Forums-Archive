---
title: "changing cache in Firefox"
date: 2012-12-22
forum: General Help
---

### Post by hunterkasy on 2012-12-22
I am trying to change my FF cache to /tmp

so I went to about:config

created
browser.cache.disk.parent_directory 
and added /tmp/ to the value

and I restarted FF

and to check I did about:cache and it still shows up in its origanal location

---

### Post by hunterkasy on 2012-12-23
help please

---

### Post by ranger1021994 on 2012-12-23
> **hunterkasy said:**
> I am trying to change my FF cache to /tmp

so I went to about:config

created
browser.cache.disk.parent_directory 
and added /tmp/ to the value

and I restarted FF

and to check I did about:cache and it still shows up in its origanal location

Did you set value browser.cache.disk.enable to true ?

---

### Post by hunterkasy on 2012-12-23
> **ranger1021994 said:**
> Did you set value browser.cache.disk.enable to true ?

it was already set to true I just got done double checking

---

### Post by ranger1021994 on 2012-12-23
Can you try writing just /tmp instead of /tmp/ ?

---

### Post by hunterkasy on 2012-12-23
> **ranger1021994 said:**
> Can you try writing just /tmp instead of /tmp/ ?

I changed it to just /tmp

the cache dir is still the same

restarted FF

and did about:cache

Information about the Cache Service
Memory cache device
Number of entries: 	155
Maximum storage size: 	32768 KiB
Storage in use: 	1538 KiB
Inactive storage: 	1538 KiB
List Cache Entries
Offline cache device
Number of entries: 	0
Maximum storage size: 	512000 KiB
Storage in use: 	0 KiB
Cache Directory: 	/home/tyler/.mozilla/firefox/zvhut0nv.default/OfflineCache

---

### Post by hunterkasy on 2012-12-25
does anyone have any other idea's?

---

