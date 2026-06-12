---
title: "Photos aren't seen by myspace or other photo hosting sites."
date: 2008-07-02
forum: General Help
---

### Post by Sr Juicy on 2008-07-02
Hey guys, Im bad at this msg board thing but i figured some thing out that was bothering me and that I saw some other people questioning.

So i would upload photos to my computer from my camera and then when i went to any photo uploading site it would not find the photos in the respected folder.  I would check and double check to make sure that the photos existed on the hard drive checked their permissions then i figured it out.

the various hosting sites looked for "randomphoto.jpg"

but what my camera would upload to the computer was "randomphoto.JPG" 

all you need to do to fix this problem is use bulk rename and switch all the suffix's to lowercase

TADA

took me some time well i hope this helps you guys out

---

### Post by lisati on 2008-07-02
:)

---

### Post by JGrubbs on 2008-08-21
We noticed this problem as well. Shouldn't Ubuntu be able to show the files regardless of if the extension is upper case or lower case? This seems like a bug in the OS.

---

### Post by jerome1232 on 2008-08-21
No not really. Seems like a design bug in the programers that wrote the upload program.

Linux is case sensitive, windows isn't.

The app that searches for extensions isn't searching uppercase and lowercase because it was designed with only case insensitve windows in mind.

---

