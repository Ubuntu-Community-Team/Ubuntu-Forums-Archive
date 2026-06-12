---
title: "SD cards..can gutsy read em?"
date: 2008-01-14
forum: General Help
---

### Post by Meow27 on 2008-01-14
hi im using gutsy and im trying to access data thru my micro sd->SD adapter->SD card Port and im having trouble browsing it.
i have checked my desktop. i have checking 'my computer. i have checked thru the media folder and could not find any method of accessing it besides using a usb connection via my mp3 player using an MSC connection which is very uncomfortable for me.

im sure im not the only one that encountered this problem but i did have trouble searching for it here

anyhow do you guys know how to solve this problem? 

thanks

---

### Post by Keith_Beef on 2008-01-15
I've used two card readers with my computer. The first is an external reader, that connects through a standard USB cable.

The second is a Rosewill internal reader, in a 3.5" bay, connected through a cable to the header on a PCI USB card that I added last week.

Both work.

Is the 'SD card Port' you mention built-in, did you add it yourself?
Try looking at how your computer reacts as you plug in the reader or as you insert the card.

```
$ watch tail /var/log/messages
```

Beef.

---

### Post by Meow27 on 2008-01-16
well i did enter that code in terminal, and ubuntu has been able to read my SDs. i dont know what happened but i give you my thinks :)

---

### Post by fragos on 2008-01-16
If this is an SD port on laptop it may be proprietary and not use USB.  All USB connected readers seem to work properly.

---

### Post by Meow27 on 2008-01-16
on my comp its a SD card port (PC not a laptop)

im not sure what the reason was but im glad its working right now

---

### Post by ~LoKe on 2008-01-16
I plugged my brothers new blackberry into my computer and it detected the SD card.  So I imagine it should work...

---

