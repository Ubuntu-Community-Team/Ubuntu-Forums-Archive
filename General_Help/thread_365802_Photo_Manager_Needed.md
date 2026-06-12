---
title: "Photo Manager Needed"
date: 2007-02-20
forum: General Help
---

### Post by gavinjb on 2007-02-20
Hi,

I am looking for a Photo Manager for Linux, I looked at DigiKam but it is not suitable, the main reason is that you cant link to the photos and it copies them to the library (big waste of disk space).

I am looking for an app which lets me put multiple categories against an image and can deal with large quantities of images.

When I was using Windows I used an app called iMatch which had all this and more, (I might try installing this under Wine, but I would prefer an Linux app).


Thanks,


Gavin,

---

### Post by Zerocool10482 on 2007-02-20
Have you tried F-Spot?

[http://f-spot.org/Main_Page](http://f-spot.org/Main_Page)

It's really cool for a simple management program.

---

### Post by ramjet_1953 on 2007-02-20
Google's Picassa works fine in Linux.

Regards,
Roger :cool:

---

### Post by soze on 2007-02-20
Mapivi

---

### Post by aliennet on 2007-03-05
Jbrout
[http://jbrout.python-hosting.com/]("http://jbrout.python-hosting.com/")

---

### Post by ArtInvent on 2007-04-15
You might look at Gthumb. I just started using it and at first thought it looked pretty basic, but it's actually very capable. Gthumb is the only app I've found so far that is not database centric, which is pretty important for me. I've used LOTS of photo managers and editors, and I've tried really hard to use F-Spot, DigiKam, and Picasa, but I believe their over-reliance on the database concept is just plain ill-advised, and for me at least, unworkable. 

Why is the database model bad? Programs like F-Spot and DigiKam and Picasa may seem attractive and slick, but in future you may regret using them and find your image changes and painstaking organizing and tagging all lost. Here are the problems typical of these programs -
[LIST]
[*]Long import process
[*]Any changes made to actual photo files will have to be re-imported
[*]Duplication of actual photo files to the programs "Photos" directory wastes time and disk space.
[*]Not saving metadata, tags, etc. to the actual file will make that info non-searchable from other programs, and subject to loss when switching to another photo manager.
[*]It's generally difficult or impossible to see your actual photo files as they exist in directories on disk.
[*]These programs use Date as the prime organizational order, which in many cases is not the most suitable or relevant information
[*]If you start out using F-Spot and then change to DigiKam or the next great image utility, you will not be able to use all of the tags and organizing you so painstakingly added. If there are aspects or features of each program you want to use, it's very difficult to just use one occasionally, since you will have to make sure the import/database is kept up to date on each one.
[*]Difficult or impossible to quickly browse thumb drives, temporary network drives, external USB disks, CD-ROM or DVD archives etc. 
[/LIST]

I have a huge catalog of images that are mostly arranged by subject, carefully, in folders on my disc. Most of these other photo managers in Linux don't work well for me. I had a couple of favorite photo managers on Windows, namely ACDSee and Compupic. They just browsed your discs like any file manager, and had great photo-oriented tools like light image editing, slide shows, proof sheet generation, batch rename, batch re-size and more. You did not have to import anything. They did keep a database, but it was mostly just for thumbnails to make browsing fast, and they're both very fast. The nice thing about this approach is also that you can browse USB disks, thumb drives, network drives etc.  It is really much better IMO to avoid the whole 'import' and 'database' oriented programs. I want to be able to work directly with my actual files, not with facsimiles or copies or references in a database. Importing really slows me down.

Opening up Gthumb is much like opening up Nautilus. In fact, one clever thing is that Gthumb actually uses the Nautilus thumbnail cache. Why reinvent the wheel? You can immediately browse your disk,  no importing needed. Since you are working with actual files and not symbolic links, you can move and rename files and those attributes can be seen in any file browser, and vice versa. Efficiently working with groups of files is the key to a good photo manager. Say you have 8 photos you want to quickly convert from TIF to JPG, resize to something small and email-able, and rename. Gthumb can do it. There are batch resize and re-format tools. The batch rename function is excellent and can reference parts of the original filename. ("Tags" are an OK idea, but if you want to find a file now and in future years you would be well advised to give your photos actual filenames with descriptive information. Most photo managers just leave the actual file names untouched so they are something completely uninformative like "DSCN2301.JPG")  The "index image" tool, used to create 'proof sheets' is actually as good as anything I saw in Windows programs. You can move and copy and delete actual files, create real folders, etc, which you can't do easily in many of the other programs.  Very clever: the thumbnail database is the same as used by Nautilus, thus avoiding unnecessary duplication at all. 

Some things I don't like - The slide show fades to black then back up to the next slide, while I would much prefer a crossfade. 'Categories' which are like tags, are not saved to the actual file, only within Gthumb. It looks like Gthumb is under active development so I look forward to getting more up-to-date versions.

Now Gthumb still uses a database - it still relies on it's own db for cataloging and categorizing. This does make it possible to catalog non-writeable media like CD-ROMS.  But if you should happen to move a file using some other program like Nautilus, the database info for that file will not get moved and will be lost. 

Another big problem with Gthumb, maybe a deal breaker: I don't seem to be able to add directories and subdirectories en masse to a cataloge or a category. This means you will have to go into each individual directory and choose the actual photos to add them to a catalogue or category. Not really feasible on large pre-existing photo collections. Apparently in more recent versions there may be a way around this, apparently you can search for files, and then add the results to catalogs. Hopefully in subsequent versions they will add the ability to just add entire directories plus sub-directories to catalogs and categories.

The solution to all this silliness is for all such photo managers to have the ability to save all metadata with the actual file. Maybe Gthumb will add this capability in future versions, along with a better slide show, that would be about perfect. As it is, it's still for me about the only usable solution other than just browsing image thumbnails in Nautilus.

---

### Post by Martin-Herrmann on 2007-04-16
> **ArtInvent said:**
> 
[LIST]
[*]Long import process
[*]Any changes made to actual photo files will have to be re-imported
[*]Duplication of actual photo files to the programs "Photos" directory wastes time and disk space.
[*]Not saving metadata, tags, etc. to the actual file will make that info non-searchable from other programs, and subject to loss when switching to another photo manager.
[*]It's generally difficult or impossible to see your actual photo files as they exist in directories on disk.
[*]These programs use Date as the prime organizational order, which in many cases is not the most suitable or relevant information
[*]If you start out using F-Spot and then change to DigiKam or the next great image utility, you will not be able to use all of the tags and organizing you so painstakingly added. If there are aspects or features of each program you want to use, it's very difficult to just use one occasionally, since you will have to make sure the import/database is kept up to date on each one.
[*]Difficult or impossible to quickly browse thumb drives, temporary network drives, external USB disks, CD-ROM or DVD archives etc. 
[/LIST]

The solution to all this silliness is for all such photo managers to have the ability to save all metadata with the actual file. Maybe Gthumb will add this capability in future versions, along with a better slide show, that would be about perfect. As it is, it's still for me about the only usable solution other than just browsing image thumbnails in Nautilus.

I agree, but you may consider having a look at [Mapivi]("http://mapivi.de.vu"). All point above are good arguments for Mapivi. The pictures are managed in place, but additionally the metadata (EXIF, IPTC) is saved in the picture file.
There is also a database, but only to enable fast searches, the master information is always in the picture and you can recreate the database from the pictures any time.
The only drawback of this that only JPEGs are supported right now. Mapivi is able to show also other formats, but you can't write IPTC or EXIF infos to them.
When you add IPTC information (e.g. a caption or keywords) to pictures you can use e.g. Picasa or iMatch to search for these information.

Regards
     Martin

---

