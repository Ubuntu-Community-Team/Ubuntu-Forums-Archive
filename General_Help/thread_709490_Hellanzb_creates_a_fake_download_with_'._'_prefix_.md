---
title: "Hellanzb creates a fake download with '._' prefix for each nzb"
date: 2008-02-27
forum: General Help
---

### Post by llarmakarma on 2008-02-27
Hi,

I have hellanzb 0.13 installed (only the backend, no web interface) and it is downloading items ok, but I am sometimes seeing Hellanzb create an extra download job for each NZB file I put in the daemon.queue directory.

The additional item is always named the same as the nzb filename but with an extra '._' (dot and underscore).

Here is a capture of the results of hellanzb.py status command:

Found new nzb: anotherdownload
Found new nzb: download1
Found new nzb: ._download1


Downloading: (0) anotherdownload    
             1311.0KB/s, 2001 MB queued, ETA: 00:26:03 (55%)

Processing: None
Queued: (1) download1
        (2) ._download1
 

As you can see, 'download1' is present twice. Does anyone know a fix for this?

PS the '._' item doesnt actually download anything. It just sits there!

Thanx

---

