---
title: "Tagging Images for quick searching"
date: 2006-09-07
forum: General Help
---

### Post by bluntu on 2006-09-07
My collections of images are growing and I find it very difficult to find them and so I'm wondering if there is a software that allows you to add tags to an image. I know Picasa can do this but I find it very inconvenient to tag an image on the fly.

One idea that I have is to append the tag onto the image (at the end of the file). Then later I can '$ grep' to find out. Example:

I have 3 images of different countries and they all have different names such as: Europe.jpg, Spain.jpg, USA.jpg.

However, one thing they all have in common is good lighting so I would like to search for 'good lighting' later in the future and these three images would show up. So I'm wondering if there is a nautilus script that allows you to add tags onto images? Like right-click -->Tag Image and then a dialog appears and from there you can add/modify tags.

Are there any program that does something like this that you know of?

---

### Post by soze on 2006-09-07
Many programs do.
I like MAPIVI.

---

### Post by bluntu on 2006-09-07
Thanks. Didn't know that this kind of thing is called "metadata".

Just did a few tests on my images with GQview and the metadata is saved into ~/.gqview/metadata leaving the original images untouched. It would be great if there is a way I can add and search on the fly.

---

### Post by Juippisi on 2006-09-09
Putting the images to a different directory is a good idea, but for that "good lighting" it could cause confusion. If you would start usinf F-Spot ( [http://f-spot.org](http://f-spot.org) ) your life could become easier. In the next version of F-Spot, there will be an opportunity to search tagged images. You can already  tag images in the current version. 

So, start tagging your images and wait for the next version to be released :-).

[http://f-spot.org/Main_Page](http://f-spot.org/Main_Page)
[http://gburt.blogspot.com/2006/09/tag-searching-in-f-spot.html](http://gburt.blogspot.com/2006/09/tag-searching-in-f-spot.html)

At least you should try it.

---

### Post by mazirian on 2006-09-09
Well, you should try f-spot assuming you don't mind the fact that it doesn't currently work.

---

### Post by bluntu on 2006-09-09
F-Spot looks like a very cool program (good interface). When you say it doesn't work do you mean that it has problem downloading a file at a ftp site and installing it?

Cause that's what happening here. The installation works except the F-Prot where it asks you to download and install a file fails.

[http://ubuntuforums.org/showthread.php?p=1478429#post1478429](http://ubuntuforums.org/showthread.php?p=1478429#post1478429)
post #2.

---

### Post by mazirian on 2006-09-09
It has potential but is very buggy and be prepared for what may amount to lockin. When you import photos they will be copied according to its /year/month/day directory structure, which you may or may not prefer, and it will rewrite some of the metadata.  I actually wanted the latter feature, but it doesn't save the metadata according to conventions that are, at least according to my thinking, intuitive.  For instance, tags are saved in some iptc profile that I can't access with any ruby or perl library.  Descriptions aren't saved in the EXIF entry ImageDescription but instead under UserComment, which is annoying and breaks other applications I use. But most of all it crashes regularly, is slow to browse photos, has far less editing powers (compared to, say, gthumb).  And now it fails to start altogether.  I suspect there was a recent upgrade to a mono library that's responsible the last bit.

---

### Post by lewing on 2006-09-12
> **Juippisi said:**
> Putting the images to a different directory is a good idea, but for that "good lighting" it could cause confusion. If you would start usinf F-Spot ( [http://f-spot.org](http://f-spot.org) ) your life could become easier. In the next version of F-Spot, there will be an opportunity to search tagged images. You can already  tag images in the current version. 

So, start tagging your images and wait for the next version to be released :-).

[http://f-spot.org/Main_Page](http://f-spot.org/Main_Page)
[http://gburt.blogspot.com/2006/09/tag-searching-in-f-spot.html](http://gburt.blogspot.com/2006/09/tag-searching-in-f-spot.html)

At least you should try it.

You can search based on tag in every version of f-spot.  Click the check box next to the tag or tags you'd like to search for.

---

