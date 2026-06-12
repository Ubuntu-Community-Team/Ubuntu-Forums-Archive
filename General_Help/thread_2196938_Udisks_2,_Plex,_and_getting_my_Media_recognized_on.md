---
title: "Udisks 2, Plex, and getting my Media recognized on Multiple USB drives"
date: 2014-01-01
forum: General Help
---

### Post by bmcgonag on 2014-01-01
I've been reading the forums about similar issues, and the only answer I've found that seemed half way useful was to mount my two USB drives in /mnt, then point to them wtih Plex.  The issue I ran into was that with each reboot, sdc and sdd were occasionally swapped out, so if I had the 2TB drive set as a certain mount point for movies, and the 1TB drive set as another mount point for TV Shows, then in Plex they suddenly didn't work again.

I've removed those fstab entries, and gone back to allowing them to auto mount by volume name under /media/<my user>/, but now I'm back to not being able to dig any further into the drive than the main level.  

For instance my TV Shows are on the 1TB drive at a path like

/media/brian/1TBShows/TV/TVShows/

but I can only get to 1TB. 

The same for the 2TB drive and the movies.  Even if I added the shows to the 1TB level, Plex wouldn't be able to see them. 

So far I've chown'd the drives, and the /brian folder.  chmod'd everything to 755, and still can't get to the folders inside the drives.  

Any help or suggestions would be greatly appreciated.  Particularly a better way to add these to /mnt so they won't swap with reboots.  

Thanks, and Happy New Year to you all!

---

### Post by bmcgonag on 2014-01-01
Okay, we'll see if this lasts. 

I did

sudo chown -R brian:users /media

then did 

sudo usermod -G users plex

Now I see my shows in Plex server.  It's a bit of a pain, adn I have a feeling changing /media owner from root may not be the best plan.

---

