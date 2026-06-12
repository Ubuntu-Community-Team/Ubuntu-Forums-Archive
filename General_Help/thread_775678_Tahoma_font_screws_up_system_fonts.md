---
title: "Tahoma font screws up system fonts"
date: 2008-04-30
forum: General Help
---

### Post by Arrdee on 2008-04-30
Hi all!

I just did a clean install of Hardy (boy was it nice after using it since Alpha 2 or so). Anyways, the fonts on the system were fine until I tried installing Tahoma as a font. Here's what I did:

- Copied tahoma.ttf and tahomabd.ttf into their own folder (/usr/share/fonts/truetype/tahoma/)
- ran sudo fc-cache -f -v
- rebooted

Looks like Tahoma installed, but now in Firefox and on the graphical login screen, a lot of text is abnormally large (about twice as large as it normally is). At this point, I really don't care about having Tahoma on my system, I just want this fixed, as it's really irritating. Steps I've taken to try and remedy it:

- removed /usr/share/fonts/truetype/tahoma/
- ran sudo fc-cache -f -v again
- cleared ~/.fontconfig/

It's still happening, and I'd really like not having to reinstall the system again just to get the fonts back to how they were when I first installed. Any ideas would be greatly appreciated. Thanks!

---

