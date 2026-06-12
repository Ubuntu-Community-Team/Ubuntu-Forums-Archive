---
title: "Gparted taking too long to resize"
date: 2008-05-25
forum: General Help
---

### Post by WanderingKnight on 2008-05-25
I'm trying to resize a 50-something GB ext3 partition on an IDE drive with gparted, leaving like 25 GB as unallocated space. However, when I tell gparted to start resizing, it just sits there doing nothing. It's been like this for 20 minutes or so. With top I can see that resize2fs is taking a steady amount of CPU (20% or so), but absolutely nothing happens. Trying to cancel it brings up a rather scary message, so I don't know what to do.

Any ideas? Should I just wait more?

Note: this is on a Feisty system.

---

### Post by forestpixie on 2008-05-25
Do not turn it off - it will take as long as it takes - if after a day or two it's still going you might need to make decision - there is a thread here by billgoldberg - he had to turn it off after 2 days.

The scary message did it's job then  :)

Just wait and it will finish.

---

### Post by WanderingKnight on 2008-05-25
Thanks, now it finished. I was getting nervous because I didn't get any feedback from the interface, but then I discovered that the thing had a little arrow at the side which gave you more details about what it was doing. Thanks :D

---

