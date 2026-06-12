---
title: "many folders"
date: 2018-09-21
forum: General Help
---

### Post by idkwhatimdoing1.0 on 2018-09-21
hello,
I have an issue and it is quite hard for me to solve right now. I have an external hard drive that has around 300GB of pictures. I want to scan for doubles howevere they're all in different folders. My question is how can I have every single picture in one folder? Without having to do copy and paste as there is at least 7-8 folders and they all have a minimum of three subfolders. Thank you!

---

### Post by Holger_Gehrke on 2018-09-21
geeqie has the ability to search for duplicates using various criteria (name, size , similarity) and has no problem with searching through subdirectories. Searching by similarity takes a lot of time and is not 100% reliable, so you have to check the results.

Holger

---

### Post by TheFu on 2018-09-21
Placing large numbers of objects (files or directories or pipes or ... ) into a single directory is asking for trouble and poor performance.  Somewhere around 500 objects, things start to slow.  If there is any issue with corruption of the directory, all the files can be lost (unlikely).

There are a number of file duplicate search tools.  fdup is one.  I wrote one in perl a few years ago as an exercise to see how hard it would be.  250 lines later and it works in identifying duplicates.  That includes specifying different file patterns to limit the search - so like images or videos or all files.

Just tried geeqie duplicate finder. It is a hassle, but better than pretty much any other solution when you need to visually check the files.

Regardless of what you end up doing, please, please, make a full backup of anything you don't want to loose first.

---

### Post by HermanAB on 2018-09-21
Well, it may be better to use a utility called 'hardlink', to find the duplicates and replace them with links.  That way, nothing will seem to change, except that you will magically regain gigabytes of disk space.

---

### Post by idkwhatimdoing1.0 on 2018-09-24
I tried geeqie however it didnt work really... It seems to have a lot of trouble when it's a big file because I can only do the drag and drop however it won't add the contents.

---

### Post by TheFu on 2018-09-24
Define "big file"

---

### Post by 1clue on 2018-09-24
[https://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/](https://www.howtogeek.com/201140/how-to-find-and-remove-duplicate-files-on-linux/)

fslint helps you find duplicates even if they're not named the same thing.

You REALLY don't want everything in the same folder. You end up with an unusable disaster that will take much longer to recover from than it took to get you into trouble in the first place.

My personal practice is to put photos into directories based on their creation date. I set up my destination tree like this: /path/to/photos/ and it generally makes things manageable. You could also easily break it up by day as well.

I set up a directory where my phones/cameras download to, like ~/Pictures. I have another directory where I put the master directory. I choose to have the master directory be on a different filesystem. FSLint deduplicates the files, but it doesn't do it the way you expect. It causes the data to only be stored once on the filesystem, but it makes a hard link to that same data for every duplicate you had. So if you edit one file you edit all of them. However if you delete one file, it just reduces the hard link count by one, so the data is there until you deleted the last reference.

---

### Post by Holger_Gehrke on 2018-09-24
You don't drag single files into the comparison window, you drag everything you want to compare in one action. If there's folders in there you get offered the option to recurse or disregard folders. It doesn't show the list of files, as soon as you put files in there it starts comparing according to the criterion selected from the drop-down menu at the bottom of the window. It will only show files it considers as possible duplicates once it's done comparing. I've just checked my pictures folder by similarity (~2000 images, several large scanned png of ~50mb, took about 10 minutes) and it had no problems working with these files and recognizing the thumbnails I have of some of them as duplicates.

Holger

---

### Post by idkwhatimdoing1.0 on 2018-09-24
I used fslint... It was actually just simpler to use... I don't know if I am just dumb and geequie was better than me or not but I couldn't figure it out. Fslint was quite easy I went onto the link of fslint and you just press the version you want and then you select the path and then just press the find button and thats it... Just seems easier.

---

### Post by TheFu on 2018-09-24
Choice is good.  Not all tools meet the needs for everyone. ;)  Appreciate that you found a workable answer, got it working AND let the community know!  Very helpful.

---

