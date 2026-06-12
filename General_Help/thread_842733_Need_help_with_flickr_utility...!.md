---
title: "Need help with flickr utility...!"
date: 2008-06-27
forum: General Help
---

### Post by plantboy1 on 2008-06-27
I am currently in the process of moving from Yahoo to Google since Yahoo has given me nothing but problems.  I'm currently trying to move my flickr photos to Picasa.  I downloaded a utility called "flickrfs" from the repositories that is supposed to mount your flickr account like any other removable media so you can copy files to and from it.  It runs, and it works up to a certain point.  It gets to where it says that "Sets have been populated.  Done" and then i get this whole "fuse: missing mountpoint
Please make sure that user is added to the fuse group.
Unhandled exception in thread started by 
Error in sys.excepthook:"  

Help?!?:confused:

---

### Post by zeezam on 2008-07-25
> **plantboy1 said:**
> I am currently in the process of moving from Yahoo to Google since Yahoo has given me nothing but problems.  I'm currently trying to move my flickr photos to Picasa.  I downloaded a utility called "flickrfs" from the repositories that is supposed to mount your flickr account like any other removable media so you can copy files to and from it.  It runs, and it works up to a certain point.  It gets to where it says that "Sets have been populated.  Done" and then i get this whole "fuse: missing mountpoint
Please make sure that user is added to the fuse group.
Unhandled exception in thread started by 
Error in sys.excepthook:"  

Help?!?:confused:


I have installed flickrfs and python, python-fuse and libfuse.
I succedeeded with the mount

```

Authorization complete.
Sets are being populated in the background. Please wait...
Sets have been populated. Done.

```

This isn't going to be any visible read and write munt disc. You must add the user to the fuse group.
Simply go to System > Admin > Users and group.

To make all the pictures visible copy them to your Pictures folder in your home dir.

```

cp -R /mntpoint/* ~/Pictures

```

---

### Post by Akt on 2008-12-15
I'm in the same bunch.  This is what I got when I opened a terminal and typed, "flickrfs":

me@me-desktop:~$ flickrfs
Authorizing with flickr...
Authorization complete.
Sets are being populated in the background. Please wait...
Sets have been populated. Done.
fuse: missing mountpoint
Please make sure that user is added to the fuse group.

What user do I need to add to the fuse group?

Talk in baby talk, I'm a newbie...

---

### Post by mlissner on 2009-05-18
Well, I just added myself to the fuse group, and still I'm getting this error. I think I'm going to write a script myself to do the flickr thing I needed...alas.

---

### Post by neurostu on 2009-07-14
you have to tell flickrfs where you want to mount your flickr account.
```

flickrfs /path/to/mount/point

```
This should fix the error.

---

