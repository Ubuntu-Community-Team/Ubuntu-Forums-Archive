---
title: "permission denied to SD card"
date: 2008-04-24
forum: General Help
---

### Post by zachthejones on 2008-04-24
I've got a 2 GB mini SD card (in an SD adapter) in my card reader on my laptop. I've used a regular SD card with no problems, so I know it's not my hardware. When I try to copy files to the SD card, I get > Error while copying to "/media/disk".
with this underneath:
> You do not have permissions to write to this folder.

I'm not sure why this is occuring, but I figured there has got to be some way for me to activate permission to copy/delete (whatever I want to) on this SD card.

Note: This card just came from my wife's Vista laptop where we were trying to use it with Readyboost to make it run faster, which didn't work (to my wife's satisfaction). So I get the card. In looking over the "properties" I noted that it is formated in vfat - would that have something to do with the problem?

---

### Post by justleen on 2008-04-24
give your user ownership of the disk
```

sudo chown <yourusername>:<yourusername> /media/disk

```

vfat is natively  supported by linux, so your fine there..

---

