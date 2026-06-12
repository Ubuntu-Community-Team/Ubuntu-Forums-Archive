---
title: "A question about mounting a subdir on a different partition"
date: 2007-01-18
forum: General Help
---

### Post by richardq on 2007-01-18
I use F-Spot to import photos from my camera into my /home/myname/Photos directory (I like the way it names/numbers the folders by date). My hdb2 partition is mounted as /home.

I've created a new partition hdb5 on the same drive and I'd like the photos imported by F-Spot to be put onto that partition. I don't see any option in F-Spot to change where it puts the photos, so my question is this:

Can I mount the hdb5 partition as /home/myname/Photos ? (after moving or renaming my current /home/myname/Photos directory). So I would propose doing this:

1. Move my /home/myname/Photos folder to /home/myname/temp/bakPhotos.

2. Delete the /home/myname/Photos folder (although I guess moving it in step 1 would make this step unnecessary).

3. Modify my fstab file to mount hdb5 as /home/myname/Photos

4. Move all the subdirectories and files from bakPhotos into the /home/myname/Photos folder.

5. F-Spot shouldn't care where the /home/myname/Photos folder actually is on the drive so nothing should work differently from before - except that the photos will be on a separate partition. 

Does this sound right? I'm pretty much a newb when it comes to partitioning so I'm not completely sure if I can mount /home on one partition and then a subdirectory of /home on another.

---

### Post by mcduck on 2007-01-18
yes, that should work exactly the way you want :)

---

