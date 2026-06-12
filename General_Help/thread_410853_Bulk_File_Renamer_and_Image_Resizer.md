---
title: "Bulk File Renamer and Image Resizer"
date: 2007-04-16
forum: General Help
---

### Post by wizzkid on 2007-04-16
Hi Guys,

Is there application in Kubuntu (or that can be install in ubuntu), that rename multiple files, because I have 1,000  images from my Digicam that I would like to rename its filename from default camera filename to a custom one, eg, IMG_04367.JPG to HKVacation_001.JPG and so on... I guess it would be very difficult to rename 1 by 1 :)

Also, I need software that can resize multiple images, same as above , I have 1,000 images from my Digicam that is 2272x1704 in size and I want to resize it to 1024x768 or 800x600. 

Your response to this matter is highly appreciated!

---

### Post by Subban on 2007-04-16
I believe there is Krename
```
sudo aptitude install krename
```

 I don't use KDE and didn't get on with krename either, I have been using Thunar solely for its renaming for a long time now,  
Thunar is the XFCE filemanager, its light and fast, and the rename dialog can be opened up separately to the actual manager.

Install Thunar from Synaptic or
```
sudo aptitude install thunar
```
To open the rename dialog alone:
```
Thunar -B
```
or
```
/usr/lib/thunar/ThunarBulkRename 
```
Obviously the latter is best suited to residing on a launcher

---

