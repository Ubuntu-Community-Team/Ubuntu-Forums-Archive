---
title: "Google Picasa doesn't work on edgy?"
date: 2006-11-05
forum: General Help
---

### Post by chombee on 2006-11-05
I installed Google's .deb package for Picasa on edgy, but when I run picasa nothing happens. Tried running it from a terminal, no error or anything, just nothing happens.

Are other people experiencing this problem and does anyone know how to get Picasa working on edgy?

thanks

---

### Post by charles nicholls on 2006-11-05
I have just checked this out and it's ok on Edgy, does take a while to load (about 20 sec's) but no problems after that, try the Ubuntu deb at [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)
hope it works

---

### Post by chombee on 2006-11-05
You're right, it just takes about 30 secs (on my system) to start.

It's a pretty damn impressive looking app that appears loaded with features, I have to admit. 

I'm recommending it to a friend who just moved to Ubuntu from Windows. Photos are one of his big things, and he was using iView on Windows to manage them. I showed him F-Spot but he didn't like it and asked for something 'more professional' that would let him see the filenames of the images and do batch edits. I guessed Gthumb would not be enough for him either, and Picasa was the only other thing I could think of. Not sure how Picasa compares to iView, but it looks pretty good so hopefully he'll like it. It's not free software, but he has taken the step of moving away from Windows, and I want him to be happy with his Ubuntu setup.

---

### Post by tajreed on 2006-11-05
Picasa uses 100% of my processor time. So I had to quit using in in Edgy. Anyone else with this outcome?

---

### Post by testube_babies on 2006-11-05
There seem to be a lot of complaints about Picasa in Edgy.  It works fine for me, but here are some more people who have problems:

[http://www.ubuntuforums.org/showthread.php?t=262335](http://www.ubuntuforums.org/showthread.php?t=262335)
[http://www.ubuntuforums.org/showthread.php?t=288696](http://www.ubuntuforums.org/showthread.php?t=288696)
[http://www.ubuntuforums.org/showthread.php?t=286316](http://www.ubuntuforums.org/showthread.php?t=286316)

...among others

---

### Post by fragos on 2006-11-05
I suggest you look at F-spot.  It has basic editing that's very intuitive and has a grat export feature which douwnloads to Picasa on the web.  I will also save your album in the form of a very attractive web page which you can ftp to your personal site.  I prefer F-spot because its a native application and doesn't require a Google modified version of Wine.

---

### Post by chombee on 2006-11-05
Agreed, using f-spot is preferable when possible. I just tried out the export webpage feature of picasa, and the web pages it makes are not as cool as the f-spot ones. Picasa is a lot flashier and has more features than f-spot though, and I think f-spot uses quite a lot of system resources.

---

### Post by tajreed on 2006-11-05
Picasa uses 100% of my processor time. So I had to quit using in in Edgy. Anyone else with this outcome?

---

### Post by maniacmusician on 2006-11-06
> **chombee said:**
> You're right, it just takes about 30 secs (on my system) to start.

It's a pretty damn impressive looking app that appears loaded with features, I have to admit. 

I'm recommending it to a friend who just moved to Ubuntu from Windows. Photos are one of his big things, and he was using iView on Windows to manage them. I showed him F-Spot but he didn't like it and asked for something 'more professional' that would let him see the filenames of the images and do batch edits. I guessed Gthumb would not be enough for him either, and Picasa was the only other thing I could think of. Not sure how Picasa compares to iView, but it looks pretty good so hopefully he'll like it. It's not free software, but he has taken the step of moving away from Windows, and I want him to be happy with his Ubuntu setup.
If he's into photo editing, I would recommend Lightzone for him. Discussion about it [here]("http://ubuntuforums.org/showthread.php?t=290340") What I love most about this app is that windows users have to cough up $150 bucks for it (and it is worth every cent of that money), but us Linux users get it for free! Quite an impressive app, too.

---

### Post by mjreged on 2006-11-10
I now realize that when you install picasa DEB from google website Wine is also included inside the package, and the provided script that initaites picasa2.exe uses the inluded WINE.. That's bad because i causes my CPU usage 100%

so i went into the picasa folder :
/opt/picasa/wine/drive_c/Program Files/Picasa2

and executed :

wine Picasa2.exe

in this case i am running picasa with WINE that was installed by ubuntu repositories and now my problem is gone. Now Picasa is usuable again

Thank you

---

