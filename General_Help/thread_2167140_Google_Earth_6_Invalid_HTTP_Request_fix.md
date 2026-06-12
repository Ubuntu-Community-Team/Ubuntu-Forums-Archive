---
title: "Google Earth 6 Invalid HTTP Request fix"
date: 2013-08-12
forum: General Help
---

### Post by PocketDog on 2013-08-12
The web service that Google Earth 6 uses has been turned off. I can't use Google Earth 7 (incompatible GFX - it won't display satellite images, only roads).

Here's the fix: 

Rename **/opt/google/earth/free/libcurl.so.4** as **/opt/google/earth/free/libcurl.so.4.bak** (backing up original file, just in case)
Copy **/usr/lib/i386-linux-gnu/libcurl.so.4.2.0** to **/opt/google/earth/free/libcurl.so.4.2.0**
Rename **/opt/google/earth/free/libcurl.so.4.2.0** as **/opt/google/earth/free/libcurl.so.4**

(sudo required)

Works on Ubuntu 12.04 Precise 32bit - libcurl.so.4.3.0 may be the newer version on your system. If you're on a 64 bit system a simple upgrade to Google Earth 7 will probably fix the Invalid HTTP Request problem

---

