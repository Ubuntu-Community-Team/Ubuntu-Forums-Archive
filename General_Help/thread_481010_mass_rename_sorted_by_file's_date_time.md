---
title: "mass rename sorted by file's date time?"
date: 2007-06-22
forum: General Help
---

### Post by sshetye on 2007-06-22
Hi folks,

I have a unique problem. After a trip we generally have photographs from 3-6 cameras since most people in the group carry their own camera. Its next to impossible to have a designated camera! There is no global ascending filenames between those cameras and the only global refence is the file's timestamp (which are thankfully accurate).

I wanted to add a numberical prefix like "001-" to the files after putting them all in one folder and sorting them by date/time. This way when I see them in a slideshow, they are shown in chronological order and not upon each  cameras naming scheme.

eg. **I start with ...**
[camera 1]
PIC0001.jpg ........ 1/19/2007 9am
PIC0002.jpg ........  1/20/2007 3pm

[camera 2]
IMG_1.jpg   ........ 1/20/2007 2pm
IMG_2.jpg   ........ 1/21/2007 11am

**Normally I get ("incorrect", sorted by dumb filenames)**
IMG_1.jpg   ........ 1/20/2007 2pm
IMG_2.jpg   ........ 1/21/2007 11am
PIC0001.jpg ........ 1/19/2007 9am
PIC0002.jpg ........  1/20/2007 3pm

**After auto renaming I want ("correct", files renamed as per events in time)**
0001-PIC0001.jpg ........ 1/19/2007 9am
0002-IMG_1.jpg   ........ 1/20/2007 2pm
0003-PIC0002.jpg ........  1/20/2007 3pm
0004-IMG_2.jpg   ........ 1/21/2007 11am

PS: Something better would be a tool that can read the "extra" imformating within JPEGS (like camera model, exposure time, _date and time of photograph_, etc etc and use the date and time from that field. Somewhat like mp3's ID3 tags but for JPEG files. This way one can even touch up/rotate  some photos which would affect the filesystem's date and time but would leave the embedded date and time intact for future processing.

---

### Post by yabbadabbadont on 2007-06-22
I think that digikam includes an option to rename the images as it transfers them from the camera using the date-time stamp.  I don't know if that is what you are asking, or if you want a script/program to rename files that have already been transferred.

---

### Post by sshetye on 2007-06-22
> **yabbadabbadont said:**
> I think that digikam includes an option to rename the images as it transfers them from the camera using the date-time stamp.  I don't know if that is what you are asking, or if you want a script/program to rename files that have already been transferred.

I've already transferred all the photos onto my hard drive (after having everyone send me giant attachments and for the technically versatile friends, via my ftp server). So I don't have the option of collecting everyone's camera and then directly offloading them onto my PC.

Anyway, digikam appears promising. I'm installing digikam right now to see if it works so even if I supply it photos from a local directory or copy to sd -> put in my camera -> "fake" a download. Thanks for the tip!

---

### Post by stylishpants on 2007-06-22
"renrot" looks promising.

```
fhanson@fhanson:~$ apt-cache search exif | grep -i rename
renrot - Rename and rotate files according to EXIF tags

fhanson@fhanson:~$ apt-cache show renrot
Package: renrot
Priority: optional
Section: universe/graphics
Installed-Size: 168
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Andy Shevchenko <andy@smile.org.ua>
Architecture: all
Version: 0.25-1
Depends: perl, libimage-exiftool-perl (>= 5.72), libjpeg-progs (>= 6b)
Filename: pool/universe/r/renrot/renrot_0.25-1_all.deb
Size: 48066
MD5sum: ec8f956eb195cd28865e0869fc896f6e
SHA1: a13a883cab2532bdf77efb9e398cf485c380d416
SHA256: a4c95a02e1e4698f87d7cfe32e4b4b9a1be63507fe265eb0b725917b75521eaa
Description: Rename and rotate files according to EXIF tags
 RenRot renames files according the DateTimeOriginal and FileModifyDate
 EXIF tags, if they exist. Otherwise, the name will be set according to
 the current timestamp. Additionally, it rotates JPEG images and their
 thumbnails, using the Orientation EXIF tag.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


```

---

### Post by yabbadabbadont on 2007-06-22
> **stylishpants said:**
> "renrot" looks promising.

Hey!  That does look promising.  Thanks for the tip.

---

### Post by sshetye on 2007-06-22
Thanks folks. Ok, here is the lowdown.

**digikam** : GREAT piece of software for keeping a photo library. Like iTunes manages a song library, but only more intuitively (if you're willing to poke around the menus). HOWEVER, using the menu options to set EXIF tags sorta screws you up because there are 3-4 EXIF date tags (creation date, digitized date, original date and something else date). digikam alters just the "creation date" creating a furthur mess since other apps use the "original date". Not uniform, not good.

Oh by the way, in case you're womdering what EXIF tags are, EXIF tags at to JPEGS as ID3 tags are to .mp3 : They keep additional information like time, camera make etc inside the jpeg photo itself (i.e. metadata).

**exiv2**
So how do you alter EXIF tags in a more predictable manner ?? I used the command line tool "exiv2". I wish there was a gui since I wasted  some time constructing the command line for me to use. Unfortunately that's the state of the art today. doing "man exiv2" in one terminal window and constructing the command line in another helps. I'd also recommend making a backup just in case you screw up (I did, backup hooray!). To jump start,

# prints the EXIF tages to screen (can then grep for whatever)
```
exiv2 pr *jpg
```

# adjusts EXIF tags by 24 hours, 1 min and 2 seconds.
```
exiv2 -a ad 24:1:2 *jpg 
```

**renrot**
Once you have the EXIF tags in place, use the tool renrot (thanks to this thread!). Again renrot is commandline based so here is the quick and direct command line (try "man renrot" for details)
# This renames as per EXIF tags' date and time
```
renrot -n %Y-%m-%d-%H-%M-%S *jpg
```

I'm hoping future revisions of digikam put this functionality inside digikam itself, so it's a lot easier.

---

### Post by AirOnSkin on 2007-07-15
Hey there :)

I'm starting to use RenRot too and I'm quite successful with it. However there is something I don't get to work...

I would like to add a numeric counter as a suffix (that works) and have it everytime with 3 digits (eg: filename_001). As for now I'm using the following code to rename the files:
```
renrot -n %Y-%m-%d_%H-%M_%c *.JPG --counter-fixed-field --counter-start 0

```
and I get filenames like that:
```
2007-06-30_11-00_00.JPG
```
I would like to have it like this (no matter how many pictures I'm renaming at one time):
```
2007-06-30_11-00_000.JPG
```

Does anyone know how to achieve this?

Thanks!

Air

---

### Post by stylishpants on 2007-07-15
As far as I can tell, renrot doesn't provide this option.

Here are two ways you can get this behaviour:

1. Modify renrot.
It's just a perl script, and it's a simple one-line change.
```

# Change line 1524 in /usr/bin/renrot from this:
    my $size = length((scalar(@filenames) - 1) * $countStep + $countStart);
# To this:
    my $size = 3;

```

If you're feeling more ambitious, spend the time to add it as a proper command line option  and submit your patch upstream.  Isn't free software great? :)

2. Clean up the filenames after you run renrot.
You could do it with rename (aka. prename, comes with the 'perl' package) like this:

```
rename 'if(/_(\d+).jpg/i){ my $c=sprintf("%03d",$1); s/_\d+\.(jpg)/_$c.$1/i; }' *.jpg *.JPG
```


Doing it in plain perl would be only slightly more verbose;

```
perl -e 'for(@ARGV){ if(/_(\d+).jpg/i){ $c=sprintf("%03d",$1.to_i); $name=$_; s/_\d+\.(jpg)/_$c.\1/i; rename($name,$_); } }' *
```

This solution (both code examples are the same thing, really) is safe to run multiple times, and handles either case (jpg or JPG) without changing it.  

BTW the %03d in the 'sprintf' statement is what defines the 3 character width of the counter field, so change that 3 to something else if you want a different width.

---

### Post by AirOnSkin on 2007-07-16
Hey stylishpants

Thanks for that! :) I'll try it out (both) as soon as I'm home.

[QUOTE="stylishpants"]If you're feeling more ambitious, spend the time to add it as a proper command line option and submit your patch upstream. Isn't free software great?[/QUOTE]
oO you know, I'm using Linux now since 3 weeks and I have no idea how to do this ... :confused: I'm quite new with all that stuff... but if you give me a hint I'd love to support renrot with that new option :)

So far...

Air

---

### Post by stani on 2008-01-23
> **sshetye said:**
> Hi folks,

I have a unique problem. After a trip we generally have photographs from 3-6 cameras since most people in the group carry their own camera. Its next to impossible to have a designated camera! There is no global ascending filenames between those cameras and the only global refence is the file's timestamp (which are thankfully accurate).

I wanted to add a numberical prefix like "001-" to the files after putting them all in one folder and sorting them by date/time. This way when I see them in a slideshow, they are shown in chronological order and not upon each  cameras naming scheme.

eg. **I start with ...**
[camera 1]
PIC0001.jpg ........ 1/19/2007 9am
PIC0002.jpg ........  1/20/2007 3pm

[camera 2]
IMG_1.jpg   ........ 1/20/2007 2pm
IMG_2.jpg   ........ 1/21/2007 11am

**Normally I get ("incorrect", sorted by dumb filenames)**
IMG_1.jpg   ........ 1/20/2007 2pm
IMG_2.jpg   ........ 1/21/2007 11am
PIC0001.jpg ........ 1/19/2007 9am
PIC0002.jpg ........  1/20/2007 3pm

**After auto renaming I want ("correct", files renamed as per events in time)**
0001-PIC0001.jpg ........ 1/19/2007 9am
0002-IMG_1.jpg   ........ 1/20/2007 2pm
0003-PIC0002.jpg ........  1/20/2007 3pm
0004-IMG_2.jpg   ........ 1/21/2007 11am

PS: Something better would be a tool that can read the "extra" imformating within JPEGS (like camera model, exposure time, _date and time of photograph_, etc etc and use the date and time from that field. Somewhat like mp3's ID3 tags but for JPEG files. This way one can even touch up/rotate  some photos which would affect the filesystem's date and time but would leave the embedded date and time intact for future processing.

Phatch can do all of this and much more with an easy gui:
[http://photobatch.stani.be](http://photobatch.stani.be)

You can add a rename action, and type in the filename field:
<####>-<filename>
[http://photobatch.wikidot.com/action-rename](http://photobatch.wikidot.com/action-rename)

Everything what is between <> is a variable. You can also use any variable from the "extra" imformation within JPEGS (like camera model, exposure time, date and time of photograph, etc etc and use the date and time from that field). You can just copy & paste from the image inspector:

[IMG]http://photobatch.wikidot.com/local--files/image-inspector/image_inspector_exif.png[/IMG]

For better exif support, you should install pyexiv2, although Phatch provides some basic support already:

[http://packages.ubuntu.com/hardy/python/python-pyexiv2](http://packages.ubuntu.com/hardy/python/python-pyexiv2) (hardy, but also works on gutsy)

Good luck!
Stani

---

### Post by stani on 2008-01-23
Be sure the download Phatch 0.1.bzr245 or later to use this functionality. You can find the rename action by pressing '+' and selecting 'file' with the top right button. Maybe you better try with copy first or make a copy of some pictures to do a test.

Stani

---

