---
title: "Reorganise photos out of existing folder structure into new structure"
date: 2015-02-07
forum: General Help
---

### Post by Zebla on 2015-02-07
Dear Ubuntu-Community,


  I am a bit embarrassed to ask, because I am quite certain that in  some ways this has been asked and answered but apparently I don't know  enough about computers to google the right words on this problem and I  have tried for hours on multiple occasions and am quite helpless. So  please, if you know about or find helpful forum discussions, just post  the link and that could also help me a lot.


  To my problem: 


  I left mac a while back to change to Ubuntu and the probably  shittiest thing has been to get out of IPhoto, which saves all the  pictures in it's own formate or mysterious file. I exported those  pictures back then using some programme that was provided somewhere on  this forum and it took all my pictures out of the mac directory and  saved them in the following structure:  Year/Month/Day. This might be a great structure for a computer, it's not  for a human that just wants to find those funny picture you took that  one weekend, when was it again. 
  Also, there is errors in it. For example, in my folder of 2007 there  is pictures that say in their settings (correctly) that they were taken  in 2010. 


  I know there is some programmes that are supposedly similar to  IPhoto, such as Shotwell, but they struggle with the amount of pictures I  have and also they all start of with the existing file structure, it  seems.


  So what I would like to do is get all the pictures out of their  folders and reorganise them correctly according to the take that they  were taken on in the following structure: Year/Month (leaving out the days). That at least would make it easy  enough for me to go in and then put them together in albums.


  Would there be an idiot proof way of doing this?


  Thank you so much for your help!

---

### Post by dragonfly41 on 2015-02-07
I have no experience with iPhoto but since your post has no replies yet I'll chip in.

From digging around this might be the export script you refer to

[https://raw.githubusercontent.com/BMorearty/exportiphoto/master/exportiphoto.py](https://raw.githubusercontent.com/BMorearty/exportiphoto/master/exportiphoto.py)

derived from here ..

[http://www.adventuresinoss.com/?p=2471](http://www.adventuresinoss.com/?p=2471)

This suggests that iPhoto files are in XML format ...

One XML editor you can try is XMLCopyEditor found in Ubuntu Software Centre.

But on your particular problem of rearranging your exported library.

From your explanation I think that you want to **merge** the 28-31 or so subfolders in each year/month folder.

Probably someone else can advise on a script for this. If I find one I'll add a postscript.

Incidentally look at Darktable Photo Workflow Software in Ubuntu Software Centre.

**[later edit]**

I found this which might be a start.

[http://www.pythoncentral.io/how-to-recursively-copy-a-directory-folder-in-python/](http://www.pythoncentral.io/how-to-recursively-copy-a-directory-folder-in-python/)

---

