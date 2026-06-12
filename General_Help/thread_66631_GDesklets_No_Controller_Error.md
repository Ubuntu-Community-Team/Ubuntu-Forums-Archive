---
title: "GDesklets No Controller Error"
date: 2005-09-17
forum: General Help
---

### Post by tamarku on 2005-09-17
I installed Gdesklets and am suddenly getting this error whenever I start up my PC.  Here is the link to the pic = 

[http://img.photobucket.com/albums/v285/tamarku/NoControl.png](http://img.photobucket.com/albums/v285/tamarku/NoControl.png)  

I only installed a couple of applets so I'm not sure which one started creating this error.  

Also, I installed SideCandy PopMail and am getting an error that says something about my cursor.  

Thanks for any and all the help that anyone can offer.

---

### Post by celticmonkey on 2005-09-27
I had trouble with gdesklets too. The solution was to use synaptic to uninstall the sensors and displays that are in the respository and download them from the gdesklets website. The actual gdesklet program doesn't need to be changed from the repository version. Note: If you install sensors and displays using the program it automatically puts them into the ~/.gdesklets somewhere so that only you (and not other) users can use them. If you want other users to have access to them you'll have to move them to the another directory somewhere under /usr although I forget off-hand where.

Somebody needs to fix the sensors and displays in the repository.

---

