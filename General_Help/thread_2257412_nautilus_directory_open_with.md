---
title: "nautilus directory open with"
date: 2014-12-19
forum: General Help
---

### Post by JamButty on 2014-12-19
Whatever happened to nautilus directory open-with (from right click menu)? Ubuntu had it a couple of major versions back and I have never found a way to re-enable it since. Only individual files have this option, at least by default (e.g. myfile.avi - right click - open with (x,y,z programs) but directories can only be opened to display its listing. It is very tedious to open each program from unity by name, then navigate back to the directory rather than freely moving aroung in nautilus and opening from there.
I have found no other entries on this issue, also puzzling.

thanks.

---

### Post by mc4man on 2014-12-19
It was removed quite some time ago & no one officially wants to return. 
(- filed a bug 2.4 years ago, I have given up trying some time ago - 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1026254)

You could get via a ppa thru 14.04 (never bothered with 14.10
[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-open)

or a step up with some add. patches, 14.04 only - 
[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods)

or a complete load of patches & bug fixes, 14.04 only  - 
[https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1](https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1)

or patch just open with on dir. into the source & build yourself, a small little patch at that.. - 
```
--- nautilus-3.10.1.orig/src/nautilus-view.c
+++ nautilus-3.10.1/src/nautilus-view.c
@@ -4535,8 +4535,9 @@ reset_open_with_menu (NautilusView *view
 
 		file = NAUTILUS_FILE (node->data);
 
-		other_applications_visible &= (!nautilus_mime_file_opens_in_view (file) &&
-					       !nautilus_file_is_nautilus_link (file));
+		other_applications_visible &= ((!nautilus_mime_file_opens_in_view (file) &&
+						!nautilus_file_is_nautilus_link (file)) ||
+					       nautilus_file_is_directory (file));
 	}
 
 	default_app = NULL;
```

---

### Post by JamButty on 2014-12-24
Did the full nauty-hacks load, working great so far. THANK YOU!!!!

---

