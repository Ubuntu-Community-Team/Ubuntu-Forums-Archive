---
title: "Problems copying wallpaper to /usr/share/backgrounds"
date: 2014-05-22
forum: General Help
---

### Post by Hewjr100 on 2014-05-22
Tried to copy image like I did in previous versions of Ubuntu but someting is wrong.  See attached image.  Used the following command to copy image:

"sudo cp Lake\ 4.jpg usr//share/backgrounds"

But image cannot be opened, or used as background.  Works fine in Pictures/Wallpaper folder.

Henry

---

### Post by Vaphell on 2014-05-22
look at the properties of the file, maybe it's a permission issue.

btw, why do you bother moving the pic to /usr/share/backgrounds? you can use wallpapers from your home no problem, just click the + button

---

### Post by Hewjr100 on 2014-05-22
Pics in usr/share/backgrounds appear on login screen. At least they used to.

Henry

---

### Post by coldcritter64 on 2014-05-22
Run a check on the file permissions for Lake 4.jpg, to ensure your user account has permissions set to be able to open the file,
```
ls -la /usr/share/backgrounds/Lake\ 4.jpg
``` post back results if you need help resetting or interpreting the files ownership and permissions.
> 
you can use wallpapers from your home no problem, just click the + button 		 	  	 		

 		+1, this will avoid permissions problems.

---

### Post by Hewjr100 on 2014-05-22
Here are the results:

ls -la /usr/share/backgrounds/Lake\ 4.jpg
-rw------- 1 root root 1120054 May 22 19:50 /usr/share/backgrounds/Lake 4.jpg

Henry

---

### Post by coldcritter64 on 2014-05-22
This should fix it 
```
sudo chmod 644 /usr/share/backgrounds/Lake\ 4.jpg
```

---

