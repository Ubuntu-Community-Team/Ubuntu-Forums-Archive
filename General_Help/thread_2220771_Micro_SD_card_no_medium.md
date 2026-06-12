---
title: "Micro SD card no medium"
date: 2014-04-29
forum: General Help
---

### Post by alistiarhighwind on 2014-04-29
Hey, can anyone help with this problem?

I got a micro SD card for use with my phone. I formatted it using linux and chose the slow option of formatting.
When I tried remounting my SD card in my phone there was it wouldn't mount, even though it recognised it.
When I mounted the SD card to my laptop again the name wasn't "8GB Phone Flash" which I set it too, instead it was "Drive" as a "Linux File CD-Drive"
I also formatted my phone's internal SD card and the same has happened. Although it seems the apps that were already on there are intact and working. However I can't download anything to either SD cards.

I can't format either drives either.

Hope you can help!

Here's a link to screenshot of what it says in Disks as I can't seem to insert an image (The top is my SD, the bottom is the phone's SD)
[http://screencloud.net/v/tEUb](http://screencloud.net/v/tEUb)
[IMG]http://screencloud.net/v/tEUb[/IMG]

---

### Post by Mark Phelps on 2014-04-29
You should always format the SD card using your phone.  Try that to see if it works, then.

---

### Post by alistiarhighwind on 2014-04-29
> **Mark Phelps said:**
> You should always format the SD card using your phone.  Try that to see if it works, then.

I can't even mount at all. Meaning I can't do as you suggested.

---

### Post by Mark Phelps on 2014-04-29
> I can't even mount at all.

Can't mount in the phone, too?

OK, then, unmount it from your PC, install GParted, and use that to format the SD card.

---

### Post by alistiarhighwind on 2014-04-29
It's not coming up on GParted Partition Editor either.
Only disks seems to be reading it at all. When I tried fdisk in terminal it said something about "No DOS or Linux Partition" but I think it only read my phone's internal memory drive.

---

