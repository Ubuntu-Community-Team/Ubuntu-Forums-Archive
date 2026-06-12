---
title: "Merge Folders - Large Image Preview"
date: 2017-08-28
forum: General Help
---

### Post by ndstate on 2017-08-28
I have many duplicate photos on my computer (in various folders) and I want to merge them and get rid of duplicates. I can merge folders in nautilus and it will warn me of files with the same file name, but the image preview is too small to accurately compare the images to make sure they are in fact the same image. Is there a program or file manager that will provide a larger preview or some other good way to merge folders and weed out duplicates? (I looked into Dupeguru but it doesnt have thumbnails and Geeqie isn't giving me what I want).

Thanks

---

### Post by TheFu on 2017-08-28
[https://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/](https://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/)
These are not image-specific tools. 

I wouldn't merge any files until after the program you decided is done cleaning up.  Also, be careful putting more than 500 files into a single directory.

---

### Post by HermanAB on 2017-08-29
You could also use file system deduplication, to replace duplicate files with hard links.  This can be done with fslint or dupeguru for example (also fdupes, rdfind, duff...).  That way, you don't have to actually do any cleaning up and it could be a big time saver.

---

### Post by ndstate on 2017-08-29
Unfortunately the deduplication programs are not working very well. They are either saying different photos are the same, or they don't really give good options for selecting duplicates. Apparently the programs think I have over 80,000 duplicates so I need something that works well for selecting duplicates.

Or if there is something I can use like nautilus (with bigger thumbnails) that should work since the file names are different and I can do a smaller number of folders at one time while also being able to look at the photos in question to ensure they are in fact duplicates. Thanks.

---

### Post by SunnyDaze on 2017-08-29
Yes.  Geeqie actually does do what you want.  The program **Geeqie** lets you find duplicate pictures by checksum, filename, as well as similarity.

To get **Geeqie** to show you larger images like you want, you can set the "Find Duplicates" window to "always on top," and double click the image names, and have the images appear in the background.

**Geeqie** also finds duplicate images that have been rotated, and lets you scan recursively into sub-directories for duplicate images.

As for just merging and finding duplicate any and all directories structures or files by filename, or checksum, you can use **Meld**.

If you want a program that lets you compare two very similar images and shows you the differences within the images, the non-open source program **Beyond Compare** works good.  Beyond Compare gives you two big thumbnails of the images being compared, as well as a third picture of the combined images with differences being highlighted in different colors.

For what you want to do, **Geeqie** is your best bet.  Geeqie works great for finding a bunch of duplicate images at once.

---

### Post by ndstate on 2017-08-29
I can try Geeqie again, but last time it didn't work so well. Results based on similarity is not accurate enough. Name will be hard with duplicate file names (but I can make it work). I can try checksum again, but I read that is not always accurate. Can the thumbnails be made bigger? I will also look at the other options. Thanks

---

### Post by SunnyDaze on 2017-08-29
OK, I re-read your post.  On second thought, since you are merging folders, you would be better off with **Beyond Compare**.  You open up the folder structures side by side, and if you have two images in question, you select one for compare, and then double click the question mark icon on the image you want to compare it too, and Beyond Compare will give you a very detailed comparison of the two images.

You can work your way through the directory comparisons, and merge them.

Here is an example of how **Beyond Compare** compares images:

[IMG]https://i.stack.imgur.com/NdxHZ.png[/IMG]

---

### Post by sonicwind on 2017-08-29
Nevermind

---

### Post by ndstate on 2017-08-29
> **SunnyDaze said:**
> OK, I re-read your post.  On second thought, since you are merging folders, you would be better off with **Beyond Compare**.  You open up the folder structures side by side, and if you have two images in question, you select one for compare, and then double click the question mark icon on the image you want to compare it too, and Beyond Compare will give you a very detailed comparison of the two images.

You can work your way through the directory comparisons, and merge them.

Here is an example of how **Beyond Compare** compares images:

[IMG]https://i.stack.imgur.com/NdxHZ.png[/IMG]

That looks great, thanks so much for the recommendation - I will give it a try.

---

