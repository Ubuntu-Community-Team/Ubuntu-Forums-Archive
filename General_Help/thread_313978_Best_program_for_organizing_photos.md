---
title: "Best program for organizing photos"
date: 2006-12-06
forum: General Help
---

### Post by rpkehoe on 2006-12-06
So after dual booting for a few months, I mind myself hardly ever going into XP anymore, and I have replaced most of the programs I use with counterparts in Linux.  One program that I do have in XP that I really love in Adobe Photoshop Elements 5 which I use to extensively organize about 4k photos.  Unfortunately, I have had no success getting elements up under wine, so I need something else.  I think I have most of the programs out there, digikam, gthumb, f-stop, and picasa, but I would like to get some suggestions before I start investing a lot of time into this.  


What do you guys use?

---

### Post by gunksta on 2006-12-06
From your profile I see that you use Kubuntu. Based on this fact alone, I would recommend you look at Digikam and Kimdaba. These are native KDE apps, and are supposedly quite nice. If you use either of these make sure you have all of the kipi plugins installed.

Another good option, although it integrates with Ubuntu better than Kubuntu is F-Spot. Personally, I wouldn't even take a look at Gthumb and some of the others. If you are used to Adobe Elements, I think the other programs would really disappoint you.

I don't really know how fast digikam and kalbum are, but I have around 5 gigs of photos and F-Spot doesn't seem to mind at all. I just wish the search functions were more developed.  :-)

Oh yeah, another program I do like is Album Shaper. I don't use it to really organize anything, because it doesn't work well with my brain (my problem, not the application's) but It can do some terrific web albums and editing. This is also a QT app, so it would mix in well on kubuntu.

--andy

--andy

---

### Post by lemonsCC on 2006-12-06
F-Spot drove me nuts... digiKam however =) !!

---

### Post by ddumanis on 2006-12-06
I like Google Picasa. It's a free download, it's really slick, has lots of editing/printing features, and it installs its own version of Wine automatically so you don't have to mess with the settings. :cool:

---

### Post by raveneffct on 2006-12-06
> **lemonsCC said:**
> F-Spot drove me nuts... digiKam however =) !!

Whats wrong with F-Spot? (new to linux) I opened it up and it seems to be pretty well designed.

---

### Post by rpkehoe on 2006-12-07
Picasa does have a nice interface, but I hate the way it wants to organize everything around folders.  I keep about 4-5gigs of photos in a single folder and keep them organized.  I don't want to change that structure, because that will mess up elements.

---

### Post by gunksta on 2006-12-07
How you organize your photos is entirely your choice, but I will warn you, F-Spot is going to want to move all of your photos to 

~/Photos

If you play with it, you will need to import all of your photos before it will recognize them. In the import dialog there is a checkbox at the bottom, that asks if it is OK to COPY the photos. Un-check this or you will be really annoyed when F-Spot gets done importing/copying your photos.

If you want to keep that file structure, F-Spot probably won't work well for you because it automatically decides where to put your photos when you import them from a digital camera. The Structure looks like this.

~/Photos/Year/Month/Day/

I think Digikam might work better for you.

--andy

---

### Post by anomalous_underdog on 2008-05-09
> **gunksta said:**
> How you organize your photos is entirely your choice, but I will warn you, F-Spot is going to want to move all of your photos to 

~/Photos

If you play with it, you will need to import all of your photos before it will recognize them. In the import dialog there is a checkbox at the bottom, that asks if it is OK to COPY the photos. Un-check this or you will be really annoyed when F-Spot gets done importing/copying your photos.

If you want to keep that file structure, F-Spot probably won't work well for you because it automatically decides where to put your photos when you import them from a digital camera. The Structure looks like this.

~/Photos/Year/Month/Day/

I think Digikam might work better for you.

--andy

I have tried out digiKam, and I'm afraid, like F-spot, it copies all the imported files to its own folder (~/Pictures by default), but unlike F-spot which gives the user the option to copy or not, digiKam forces this (I have version 0.9.3).

This article also says the same: [http://www.linux.com/articles/58887](http://www.linux.com/articles/58887)

From that article too, I read that [KPhotoAlbum]("http://kphotoalbum.org/") functions better. I haven't tried it yet though.

---

