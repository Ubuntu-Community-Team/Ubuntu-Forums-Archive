---
title: "Usplash and partitioning question"
date: 2006-10-12
forum: General Help
---

### Post by kuja on 2006-10-12
I've got a couple of quick questions here. I recently went and installed Kubuntu Edgy. It seems like the cd I burned was slightly corrupted (even though the image I downloaded matched, no matter what I did I couldn't seem to get a good burn, tried about five times, mostly at low speeds)

Seeing as it was only slightly corrupted, I didn't encounter many problems during the install. I couldn't use the partition format I wanteed for some reason, and a couple dozen non-critical packages weren't installed (I grabbed them afterward).

Enough background, onto question #1: If I were edit my fstab's root partition line accordingly, and copy the contents of my root partition to a backup partition, delete the filesystem from the former partition, create the desired partition type (xfs in this case), and copy all of the data back, would it work? (And yes, before anyone says anything, /boot is on a seperate ext2 partition)

question #2: One of the "non-critical packages" I mentioned was usplash. Aside from readding the splash line to the kernel line in grub, what else do I need to do to get it working? If I recall it says something about not being able to find the image, even though, I have kubuntu-artwork-usplash installed.

---

