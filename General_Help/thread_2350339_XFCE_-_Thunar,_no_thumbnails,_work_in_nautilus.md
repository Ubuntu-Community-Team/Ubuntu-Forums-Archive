---
title: "XFCE - Thunar, no thumbnails, work in nautilus"
date: 2017-01-23
forum: General Help
---

### Post by designsedge on 2017-01-23
Greetings Fellow Ubuntu Users
Using 16.04 ubuntu studio x64.

Recently my thunar (and by extension tumbler) has stopped creating thumbnails. I've checked permissions, removed the ~/.thumbnails directory and all the tips and tricks google-fu has brought to me.
When I load Ristretto - all of the panel thumbnails are the blocked symbol.
Opened a Nautilus session via terminal and wha-bam, thumbnails - though ristretto still doesn't show the other thumbnails.

So, not sure where to even begin troubleshooting a half-fixed, half-broken issue like this.
Any and all help appreciated.

---

### Post by gdesilva on 2017-01-23
Hmmm....interesting. I have both nautilus and thunar working fine but have an issue very similar to yours with dolphin. When I run dolphin from command line, I can see heaps of pixmap errors saying 

QPixmap::scaled: Pixmap is a null pixmap

16.04 Ubuntu Studio 64bit as well.

---

### Post by designsedge on 2017-01-24
Now getting the same result in Dolphin, starting to think this is a core KDE issue or similar.
So Dolphin and Thunar and Ristretto = fail
Nautilus = joy

Edit - Update information

---

