---
title: "Can I use the terminal to move images to specific dir's using the images 'tag'?"
date: 2016-04-23
forum: General Help
---

### Post by dave235 on 2016-04-23
I have a huge folder of images that I've collected over the years that my students use for coursework. It started off with about twenty images so I didn't really bother with file names or any kind of structure, just tagged them and chucked them in. That same folder now has about 5000 images in it and it's getting to the point where it's hard to work with.
Ideally I'd like to be able to run a command (now and in the future as more are submitted) that would look at the images tag(s) and create a directory with the name of the tag and move that image into it, or if a previous image has already created that directory simply move the image into that directory.
I'm not sure I'm doing a very good job explaining this.
The first 5 images for example are cars - BMW, Honda, Ford, Alfa Romeo and another BMW. The file names are all unique - they're all in the same folder remember. So after the running this mythical script I'd have 4 folders with the 2 images in the BMW one.
Everything is tagged in Shotwell, it's mostly JPG's with a few PNG's thrown in just to complicate things! There could be multiple tags but 95% are just single ones. I'm not sure where the tags are stored but I'm assuming in each file since the tags show up on both my computers but were only ever tagged on the main one.
Further investigation has shown that the tags are being stored against the individual image's 'keywords' so maybe I should be asking how to create directories based on it's keywords?
I'm very much learning as I go here!
If it helps, this is the output from the exiftool;
```
exiftool 010.jpg ExifTool Version Number : 10.10 
File Name : 010.jpg 
Directory : . 
File Size : 274 kB 
File Modification Date/Time : 2016:04:23 21:03:59+01:00 
File Access Date/Time : 2016:04:23 21:03:59+01:00 
File Inode Change Date/Time : 2016:04:23 21:03:59+01:00 
File Permissions : rw-rw-r-- 
File Type : JPEG 
File Type Extension : jpg 
MIME Type : image/jpeg 
JFIF Version : 1.01 
Resolution Unit : inches X Resolution : 72 Y Resolution : 72 
Exif Byte Order : Little-endian (Intel, II) 
Software : Shotwell 0.22.0 
XMP Toolkit : XMP Core 4.4.0-Exiv2 
Subject : BMW, Bell_Photography 
Current IPTC Digest : 6249bf63f46e9abb15cfe27d71a87a72 
Keywords : BMW, Bell_Photography 
Originating Program : Shotwell 
Program Version : 0.22.0 
Image Width : 936 
Image Height : 1334 
Encoding Process : Baseline DCT, Huffman 
coding Bits Per Sample : 8 Color Components : 3 Y Cb Cr Sub Sampling : YCbCr4:4:4 (1 1) 
Image Size : 936x1334 Megapixels : 1.2
```
Assuming that makes sense to anyone, is it possible?

---

### Post by TheFu on 2016-04-23
TL;DR - code tags would help readability greatly.

yes. It is possible.  Just make a little script that uses exiftool, looks at the tags, then moves the file to the folder based on the tag.  Any of the popular scripting languages can do this.  bash, perl, python, ruby would be my list.

If you are looking for something pre-made, I don't know of anything.  Shotwell might do this. I dunno. I never trust programs to manage my 50K photos.  I use a YYYY/MM/DD-event/ structure and can search by tag using the gallery tool instead. For me, date is the single, most important, metadata for any document that I know.  Photos, home videos, work documents, spreadsheets, PDF files, everything except code.

I'd guess this is about a 5 line script, but it depends on whether the tags map 1-for-1 to the target directory. That would be easiest, provided there aren't any other tags that need to be considered in the prioritization.  If that is the situation, either a bunch of if elif elif elif elif or a lookup table (think key/value) with the tag and target directory might be useful.  If this is the situation, the script becomes larger, since the table will either be DATA inside the script or a lookup from a DB, CSV, or key-value file.

If you wait long enough, someone may post the script. I will not.

And to should go without saying, but be certain that a backup is made before doing this. A tiny mistake could delete everything.

---

