---
title: "Window theame for ubuntu S.E?"
date: 2007-05-22
forum: General Help
---

### Post by kdarkentity on 2007-05-22
I am curious if there are any window theames for ubuntu Satanic Edition yet...also are there any S.E icons yet?

---

### Post by parker13 on 2007-06-05
Hi kdarkentity,

Sorry for the late reply, I've only just noticed this thread.

There are some Gnome and icon themes which were done by Tareeq Ali (spockrock on these forums). They'll be posted on the SE site in the next day or so. If you check the news page of the site there will be a post when they're ready:

[http://parker1.co.uk/satanic/](http://parker1.co.uk/satanic/)

Thanks for the interest,
Garry.

---

### Post by kdarkentity on 2007-06-05
alright sweet

---

### Post by kdarkentity on 2007-06-05
could you tell me how to configure xflame to use the pentagram as the image?

---

### Post by parker13 on 2007-06-06
> **kdarkentity said:**
> could you tell me how to configure xflame to use the pentagram as the image?

[img]http://parker1.co.uk/satanic/wp-content/uploads/2006/12/xflame2-ss.png[/img]

Download the pentagram image from:
[http://parker1.co.uk/satanic-files/pentagram.bmp](http://parker1.co.uk/satanic-files/pentagram.bmp)

Copy the file to /usr/share/pixmaps (or wherever you'd like to keep it):
sudo cp pentagram.bmp /usr/share/pixmaps

Now we'll install the Xflame screensaver. I suggest installing xscreensaver and xscreensaver-data-extra alongside gnome-screensaver. We will still use gnome-screensaver as the default, so no functionality will be lost:

First, make sure you have the universe repository, see the following link for instructions:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then, add the packages:
sudo apt-get update
sudo apt-get install xscreensaver xscreensaver-data-extra


You change the image shown by XFlame by editing the Exec line in its config file, eg:

gksu gedit /usr/share/applications/screensavers/xflame.desktop

Change the Exec line to read:
Exec=xflame -root -bitmap /usr/share/pixmaps/pentagram.bmp


Let me know if you have any problems.

---

### Post by kdarkentity on 2007-06-06
thanks man it worked ...its freking sweet ...do u know an exact date when the window themes will be available?

---

### Post by parker13 on 2007-06-07
They're ready now, I just need to upload them to the site. Hopefully I can get it done today or tomorrow. My wife's just had a new baby, so I have zero spare time at the moment!

---

### Post by kdarkentity on 2007-06-07
lol alright sweet man ....good luck with your kid ...congrats

---

### Post by parker13 on 2007-06-08
OK, the themes are now available at:

[http://parker1.co.uk/ubuntu-se/download.php](http://parker1.co.uk/ubuntu-se/download.php)


Thanks again to Tareeq for contributing these.

---

### Post by kdarkentity on 2007-06-09
yea i like the new themes... they are pretty kewl ....the best part is the flames for the toolbar... this was the final conversion for creating a fully satanic theme for my feisty fawn distro

i have one recommendation however the gray window backgrounds are sweet and so is the red text... but when you put red text on gray it is kind of difficult to read...

but all in all good job!!!

---

### Post by parker13 on 2007-06-10
> **kdarkentity said:**
> yea i like the new themes... they are pretty kewl ....the best part is the flames for the toolbar... this was the final conversion for creating a fully satanic theme for my feisty fawn distro

i have one recommendation however the gray window backgrounds are sweet and so is the red text... but when you put red text on gray it is kind of difficult to read...

but all in all good job!!!

Thanks for the feedback. I'll have a word with Tareeq about the text visibility issue. Maybe he can correct it.

---

### Post by spockrock on 2007-06-10
yeah I will work on it as well, and am making an even fancier theme but at the same time I wanna hold off since beryl and compiz are remerging, and I dont feel releasing a new emerald theme, is emerald is scrapped, and or there are new changes to it.

But yes I will work on the gray on red text.

---

### Post by parker13 on 2007-06-11
The updated themes are now available on the site.

---

### Post by kdarkentity on 2007-06-12
Your welcome for the feedback ...i am more than happy to participate in the satanic distro ... i am going to try out the emerald theme and ill let you know what i think of it...:twisted::twisted::twisted:

---

### Post by kdarkentity on 2007-06-12
The emerald theme is sweet!! good job with the minimize and maximize icons ....lol

---

### Post by spockrock on 2007-06-13
thanks I am glad you like them, I am working on a fancier beryl theme but I am hold off on putting it out cause well beryl and compiz are re-merging and I am hold off to make sure that changes don't adversely affect the theme.

---

### Post by kdarkentity on 2007-06-13
alright man sweet ...im looking forward to it ...let me know when its are ready

---

### Post by kdarkentity on 2007-12-08
Hey do you still have the old beryl/emerald satanic theme?

---

### Post by parker13 on 2007-12-10
Hi,

Sorry, the links are back on the download page:

[http://ubuntusatanic.org/download.php#emerald](http://ubuntusatanic.org/download.php#emerald)

Garry.

---

### Post by kdarkentity on 2007-12-10
nice, amazing job on version 666.3 by the way

---

