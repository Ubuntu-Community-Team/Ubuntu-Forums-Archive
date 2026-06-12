---
title: "F-spot and shared albums"
date: 2006-10-23
forum: General Help
---

### Post by Sonobana on 2006-10-23
Hi all!

In this computer which is my famillys computer. I have 4 users that like to share some of their photos. basicly when they add images to their albums from digital camera. the pictures shouls go straigth to share to other 3 familly members. How i dot this? 

I tryed to set same Photos-directory to all users(with ln, and nfs), but that didnt work or i didnt to something correctly.

So what is the right way to do this, or is this even possible? Thanks to all helpers.

---

### Post by nikhilk on 2006-10-23
A very quick way will be to create a shared folder somewhere with read and write permissions to everyone.
But if you are concerned about the privacy issue in that case you can go for a slightly long process of creating a group say "family" and add all the 4 users to this group and then give only that group read/write permissons on the shared folder.

---

### Post by Sonobana on 2006-10-23
it seemes to be ~/Photos where f-spot keeps its gallery. and when i add new pictures they dont appear automaticly to others gallery, and this is bad :-k

---

### Post by nikhilk on 2006-10-23
> **Sonobana said:**
> I tryed to set same Photos-directory to all users(with ln...
That is one of the possible solutions. What did you actually do? You can create an actual directory somewhere (say "/photos"). Then copy all the stuff from "~/Photos" of every user to "/photos". Delete the "~/Photos" of all users and then create a symlink to the actual "/photos" directory.

For the above example the command to create symlink will be
```

cd
ln -s /photos Photos

```
This should be done for each of the 4 users you are considering.

---

### Post by Pelekophori on 2006-10-23
I think F-Spot uses a catalogue (Sqlite database) to determine what photos to display.  Each user's F-Spot will use its own catalogue.  So even if your users place their photos in the same physical folder, the others will not automatically see the new photos until they import them to their own F-spot, thereby adding the photos to their catalogue.

The database lives in home/username/.gnome2/f-spot/.  If you want every user to see all photos automatically, I imagine you could use one database with the appropriate file links.  However your users might actually prefer to import new photos manually, since that would allow them to choose which new photos they add to their catalogue and therefore see.

---

### Post by nikhilk on 2006-10-23
Thank you Pelekophori for the info. I did not know that.

---

### Post by Sonobana on 2006-10-23
I tryed to symlink Photos direcotry but i just gettet permission problems. Then i tryed share that folder with nfs(to localhost) but ran to same problem.

---

### Post by Pelekophori on 2006-10-23
> I tryed to symlink Photos direcotry but i just gettet permission problems. Then i tryed share that folder with nfs(to localhost) but ran to same problem.

Presumably you tried using chmod to sort out the permissions problems?  

By default F-spot will create a photos directory in each users home folder.  If I understand you correctly, you originally attempted to get everyone's photos to go to your photo directory by using symlinks.  I would suggest going one step further and doing the same for each user's catalogue by creating a symlink to your F-spot catalogue (see my previous post).  You will of course need to give everyone the appropriate file permissions to read and write your photos folder and your F-spot catalogue.

So everyone's photos folder will link to your ~/photos folder, all the actual photographs will be in your ~/photos/ folder and everybody's F-spot catalogue will point to your F-spot catalogue.  They should then all see whatever photos you see.

---

