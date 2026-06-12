---
title: "Harddrive specific config files?"
date: 2006-12-26
forum: General Help
---

### Post by Rizado on 2006-12-26
I just got two new drives installed in my main computer and now have two spare drives that I don't like because they are too noisy. I also have a computer in a closet as a server/router with a small kinda old 10gb drive. I'd like to remove that one and put in a third computer that have to little space. The idea is to have my two spare drives (120gb and 160gb) in the closet computer and keep movies and such things on. (Accesible from everywhere!)

Now to my question, can I just repartition one of the drives and transfer all the files and boot sector etc from my 10gb disk to my 160gb disc, rip 10gb away and everything's fine OR are there  any important config files (I'm thinking hdparm or similar stuff, not fstab) that I should be aware of? I'd rather not reinstall because I don't have the time (or will) to set it up properly.
Maybe this's a bit confusing, what I want is to do is basically transfer everything from a 10gb drive to a 160gb (and replace it) but not keep any speed settings or anything that could harm my new drive.

Thanks in advance!

---

### Post by Rizado on 2006-12-29
Well it's done! I just used the cp command in parted and everything went real smooth.

---

