---
title: "[SOLVED] Editing html for gthumb web albums"
date: 2007-10-16
forum: General Help
---

### Post by angryhomer17 on 2007-10-16
I use gthumb's web album creation tool for my club's website and have been able to create a custom theme for it. The site is based off of a skidoo too [http://webhost.bridgew.edu/etribou/layouts/skidoo_too/index.html]("http://webhost.bridgew.edu/etribou/layouts/skidoo_too/index.html")
layout. I am figuring out how to insert the main index page in the middle content column (using a #include virtual) and it seems to be working how I would like it. 

So here's my question. How can I edit the html gthumb produces for each image so that the rest of the site layout surrounds the image. I am trying to get a more consistent look for the site and the ability to keep my navigation bar and left hand column on each page.

I think I could use an iframe, but I would rather not. 

[edit] This is the final look of the album after I mad the necessary changes: [http://campus.udayton.edu/~oac/pastevents/20071011-smokymountains/bradley.peters/album/index.shtml]("http://campus.udayton.edu/~oac/pastevents/20071011-smokymountains/bradley.peters/album/index.shtml")

Thanks for any help.

---

### Post by angryhomer17 on 2007-10-17
Well, this was much simpler than I thought. It appears that all I had to do was edit the same files I had been editing before. Just had too add my code around the code gthumb uses for the pictures. 

So, like I said, everything to modify web albums with gthumb should be contained in ```
/usr/share/gthumb/albumthemes/
```

I just copied all the data from the Flicker album theme and created a new dir for my theme and started messing around with the code.

---

