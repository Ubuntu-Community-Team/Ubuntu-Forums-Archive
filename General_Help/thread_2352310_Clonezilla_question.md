---
title: "Clonezilla question"
date: 2017-02-11
forum: General Help
---

### Post by ra7411 on 2017-02-11
Three months ago I made an image of my o/s partition w/ Clonezilla (~4gbs); it went into a 50 gb partition I created just for that purpose. A few weeks ago I had to do a restore and it went fine, so the image created was ok.

Today, I figured I'd create a new image, and sent it to the partition where the one from three months ago is stored. After the operation, I checked the partition expecting to see the old image, and a new image named according to today's date. Instead, just the image dated 3 months ago. I tried again, same result.

I looked at the storage partition and saw that it now held 12 gigs instaed of the original 4 gigs from the original o/s image done 3 months ago. Apparently, Clonezilla is feeding stuff into the old image, even though I know during the process it said it would create a new image dated for today.

I have no idea what's going on, and I thinking of re-formatting the partition to get rid of whatever it is that's in there, and then do a new o/s image.

Any ideas on what's going on?

Thanks

---

### Post by howefield on 2017-02-11
Sounds more like you have saved the image to a different location to the one you intended ?

---

### Post by ra7411 on 2017-02-11
> [COLOR=#000000]Sounds more like you have saved the image to a different location to the one you intended ? <

I looked for new images, none around.
As mentioned, the contents of the repository partition has increased by 3x.[/COLOR]

---

### Post by leunam12 on 2017-02-11
Did you choose to save to the root of the partition?

---

### Post by howefield on 2017-02-12
> **ra7411 said:**
> 

Thing is, if you used the same name as the previously saved image you would be prompted to overwrite it, it wouldn't start "*feeding stuff into the old image*". If you used a different name then you would have a new image. Something changed fairly recently in Clonezilla with regards choosing the destination folder, making it "easy" to get it wrong (imho).

As leunam12 said above, try the root of your destination disk/partition.

---

### Post by ra7411 on 2017-02-12
> **howefield said:**
> Thing is, if you used the same name as the previously saved image you would be prompted to overwrite it, it wouldn't start "*feeding stuff into the old image*". If you used a different name then you would have a new image. Something changed fairly recently in Clonezilla with regards choosing the destination folder, making it "easy" to get it wrong (imho).

As leunam12 said above, try the root of your destination disk/partition.

I didn't use the same names for the two images - I amended the Clonezilla name for the 2nd image.

I cured the problem by creating separate partitions for sda1 and sda.
Clonezilla created sda1 and sda images in those separate partitions w/ no problems.

---

### Post by howefield on 2017-02-13
> **ra7411 said:**
> I didn't use the same names for the two images - I amended the Clonezilla name for the 2nd image.

The you would have a separate image.

> I cured the problem by creating separate partitions for sda1 and sda.
Clonezilla created sda1 and sda images in those separate partitions w/ no problems.

Glad you found a way that works for you.

---

