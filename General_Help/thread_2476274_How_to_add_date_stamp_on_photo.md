---
title: "How to add date stamp on photo"
date: 2022-06-21
forum: General Help
---

### Post by satimis on 2022-06-21
Hi all,

What will be an easy adding date/data stamp on photos?

Thanks

Regards

---

### Post by pushbike06 on 2022-06-22
One way to add the date/data stamp to a photo is to use Fotoxx to modify the photo.
Open Fotoxx, select/import photo.
Select Meta from the side panel and select "Edit Any Meta Data"in the meta data list, find the original time stamp and ctrl c. 
Select Edit1 from the side panel and select "Add Text" then ctrl v into the text panel provided. Choose the location, size, colour etc for the date stamp label.

---

### Post by satimis on 2022-06-22
> **pushbike06 said:**
> One way to add the date/data stamp to a photo is to use Fotoxx to modify the photo.
Open Fotoxx, select/import photo.
Select Meta from the side panel and select "Edit Any Meta Data"in the meta data list, find the original time stamp and ctrl c. 
Select Edit1 from the side panel and select "Add Text" then ctrl v into the text panel provided. Choose the location, size, colour etc for the date stamp label.
Thanks for your advice.

fotoxx is on Ubuntu20.04 repo

Install fotoxx
Start fotoxx

But I couldn't find "import photo" on the menu. Pls refer to attached screenshot.

Regards

---

### Post by Impavidus on 2022-06-22
I use gthumb to add captions to my pictures. It also allows setting date and time, all stored in the exif data. If you prefer command line, try **exif**. I don't know more about the tool than what I read in the man page, so I suggest you read it too and experiment.

---

### Post by satimis on 2022-06-22
> **Impavidus said:**
> I use gthumb to add captions to my pictures. It also allows setting date and time, all stored in the exif data. 

Thanks for your advice.

Now I have "gthumb" installed and running on Ubuntu 20.04.

Where can I find doc/tutorial re adding text on photo?  Pls advise, thanks

> 
If you prefer command line, try **exif**. I don't know more about the tool than what I read in the man page, so I suggest you read it too and experiment.
For command line operation adding text on photo, I use "convert" of ImageMagice.  It works for me without problem.

Regards

---

### Post by pushbike06 on 2022-06-22
Satimis,

Open Fotoxx and go to left panel and click on File then select Source Folder.
The new top bar will display a path to some file(s).
If necessary backtrack along path by clicking on tab e.g home or Pictures ( both are directories). Search the selected directory for you photo and select.

Easier still find your photo via Files and right click on it and select open with Other applications then select Fotoxx from the subsequent drop down. This assumes Fotoxx is not the default Photo display application which I think is Image Viewer.

The Exif date /time data as well as a wealth of other data is available via Fotoxx/Meta(brief) or /All meta(long). If you are not aware, all Digital photos have Exif datafile within the Photo file, have look and learn.

I've never used the apps referred to by other posters. Fotoxx has a wealth of functions that can be applied to you photo(s).
I also use Thunar's Bulk Rename to change the file name of photos downloaded from my camera(s). The camera file names are non descriptive names and Bulk rename can help identify photo subject/topic for orderly filing and future access.

---

### Post by satimis on 2022-06-22
> **pushbike06 said:**
> Satimis,

Open Fotoxx and go to left panel and click on File then select Source Folder.
The new top bar will display a path to some file(s).
If necessary backtrack along path by clicking on tab e.g home or Pictures ( both are directories). Search the selected directory for you photo and select.

Easier still find your photo via Files and right click on it and select open with Other applications then select Fotoxx from the subsequent drop down. This assumes Fotoxx is not the default Photo display application which I think is Image Viewer.
- snip -

Thanks for your advice.

I have the image file opened on Fotoxx.  Please refers to attached screenshot.

But I have not idea what to do next?

Regards

---

### Post by pushbike06 on 2022-06-23
Satimis,
Go to post No.2 and follow the directions. 
Unfortunately I can't hold your hand so you are going to have to make your own way.

Note: If you do not understand anything suggested in  my post say so otherwise I do not know why you are having difficulty in following my instructions.
For example do you understand "find the original time stamp and ctrl c" and "and select "Add Text" then ctrl v into the text panel provided" ?

---

### Post by Dennis N on 2022-06-23
> Where can I find doc/tutorial re adding text on photo? Pls advise, thanks

These are digital image files? What is the end goal? To have a date on the image itself?
If so, why can't you just use a program where you type the date onto the photo where you want it? Many draw programs can easily do that.

---

### Post by Impavidus on 2022-06-23
Is this to put the date and time in the exif data, so that it's stored in the image file but not visible in the image itself, or or this about putting the date and time into the raster image data itself, like what used to be common for analogue photos when time had to be precisely recorded (but it could be put along the edge of the film, outside the negative, too)? Since we have digital pictures, we normally put such timestamps in the metadata, as this keeps the picture clean and is more computer-readable.

As I wrote, gthumb (and pretty much every other tool) stores this stuff in the exif data, not on the image. That seems a bit pointless, unless you want to emulate the pictures from specialist analogue cameras used by people like accident investigators.

---

