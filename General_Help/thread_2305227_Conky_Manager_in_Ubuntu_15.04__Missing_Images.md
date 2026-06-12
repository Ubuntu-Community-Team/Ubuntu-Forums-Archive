---
title: "Conky Manager in Ubuntu 15.04 | Missing Images?"
date: 2015-12-03
forum: General Help
---

### Post by neu5eeCh on 2015-12-03
Just installed Conky Manager on my daughter's 15.04 Ubuntu install -- at her request. She was excited then bummed that only a few of the themes actually worked. The  problem is that none of the background images appear. All the conky config files seem to be looking for images in non-existent directories, such as ./conky_images...  Do the themes just not work in Conky Manger without major tweakage, or is this a bug? Or should I uninstall Conky  Manager and send her in a different direction?

---

### Post by SlidingHorn on 2015-12-04
Most themes will come with instructions on where to place any related images, scripts, etc.  At this point, there are two basic options:

1.  Move the necessary images to the directory (if not-existent, just make one - mkdir <dirname>)

2.  Make edits to the config file(s) so that they point to the proper directories

While I wouldn't necessarily recommend it, you could do a mass edit using sed to change any instance of its asking for ./conky_images to whichever directory actually contains the images you're looking for.  The reason I'd advise a lot of caution here, is that you could make changes in files you don't want to change.  That warning being given, you can run the following:

```
sed -i 's/\.\/conky_images/<ActualPath>/g'
```

You'll need to be sure to properly escape the slashes, etc in the corrected path using backslashes (e.g.  \/home\/user\/conky)

---

