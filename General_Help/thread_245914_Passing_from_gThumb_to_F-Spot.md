---
title: "Passing from gThumb to F-Spot"
date: 2006-08-28
forum: General Help
---

### Post by Nonno Bassotto on 2006-08-28
I'm currently using gThumb to keep my photos organized, and I've added comments and categories to all my pictures, so I can now use these metadata to search my collection.

The problem is that I'd like to try out some other photo management utility, with better photo editing capabilities. I'm considering F-Spot, Picasa is also good but it seems to me it lacks on the organizing photos side.

Is there any way to convert my data, in such a way I won't have to tag every single photo again in F-Spot?

By the way, if the answer is no (and I fear it is), this is a big problem, since one gets tied to a particular graphic program very soon.

---

### Post by soze on 2006-08-28
That's exactly why you should use a program which stores the metadata in the image's file (as either EXIF or IPTC records).

I've been using MAPIVI for awhile, and while it does not have a very slick interface like some of the other applications you mentioned, it's very functional and most importantly will store keywords, descriptions, etc. in the image files themselves.

---

### Post by Nonno Bassotto on 2006-08-29
Storing information directly in the image file is a way to go, but it is not necessary. For example gThumb stores the relevant information in a hidden .xml file in the same folder as your image (actually in a subfolder called .comments). So, the data is not stored in a gThumb database, but remains with the photos even if I move it, ecc.

The question is: can F-Spot or Picasa read and import the information in this xml files? If not, does it exist a tool to convert this data into something that F-Spot can read?

---

