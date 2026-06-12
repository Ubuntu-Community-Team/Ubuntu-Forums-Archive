---
title: "clone SSD using dd: can I copy the clone to a smaller SSD card?"
date: 2022-07-24
forum: General Help
---

### Post by Old Jimma on 2022-07-24
Hello Ubuntu Adherents from Earth:

I used dd to create an immage (.img) so that i could back up the opperating system for my raspberry pi.

THe instructions I followed are here: [HTML]https://askubuntu.com/questions/227924/sd-card-cloning-using-the-dd-command[/HTML]

The original SSD that has the operating system on it is a 128GB SSD.

Can I clone the image to an SSD that is only 64GB?

I'm pretty sure that the operating system on the 128GB SSD is pretty small, less than 32GB. Pretty sure about this because a 32GB SSD was recommended for the opperating system, and because I don't store anything in the home directory on the SSD.

THanks,
Even Older Now Jimma

---

### Post by coley9225 on 2022-07-24
Hello even older jimma.
If I understand how cloning works, the target drive has to be as big or bigger than the source. I think(and I may be wrong) if you resize the current source partition to 64GB or less, then clone the partition to your smaller drive, it should work. You can always increase the source partition to full drive later, if needed.
Again,I'm fairly new to 'buntu, but I think that this method should work. There may be a better solution that I'm unaware of, maybe clonezilla or something.
Good luck.

---

### Post by #&amp;thj^% on 2022-07-24
Yes, as long as the partitions will fit, so that it doesn't need to be resized by dd.
Just be sure your not using dd on mounted devices. unmount all the partitions first

---

### Post by Impavidus on 2022-07-24
If the last 64GB of the source drive is unallocated, you could clone it to the 64GB drive. Even then, on GPT drives you'll miss the backup partition table at the end of the drive, so you may have to fix that. I don't know the details. If the last 64GB isn't unallocated, some (parts of) files will be there and won't be copied and your backup will be useless.

---

### Post by Old Jimma on 2022-07-24
Hi coley9225,

Thanks for your reply. Your advice was concordant with the next person responding, 1fallen, who is an absolute Ubuntu genius!

You are gonna love Ubuntu: lots of things to like about... first it linux that can be installed on everything probably, and second... lots and lots over really great free software.

Have fun, and thanks!
Older than the Oldest

---

### Post by Old Jimma on 2022-07-24
Hi 1fallen:

Thanks for your reply! Very grateful for it.

I understand the part: "Just be sure your not using dd on mounted devices. unmount all the partitions first." THe second part to that is to go away after dd starts and have a cup of coffee, or better yet, take a nap: Wait 'til its done.

Very grateful for a prevous query you responded to a while ago about being certain that my USB devices were really mounted. That has helped ALOT. If you haven't started fooling around with PI OS (debian) on a pi, you'll learn that you have to keep on eye on stuff and make sure it works. PI OS seems to be tempermental.

Old^3

---

### Post by Old Jimma on 2022-07-24
Thanks Impavidus. I'll keep an eye on that!

---

### Post by #&amp;thj^% on 2022-07-24
> **Old Jimma said:**
>  1fallen, who is an absolute Ubuntu genius!
Have fun, and thanks!
Older than the Oldest

Cough Cough, That's a bit lofty, no genius, just been around the block a time or two.
I don't want to fall off that stage again>>>2fallen just doesn't work. :lolflag: 
Take Good care Older than the Oldest Jimma. ;)

---

