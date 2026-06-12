---
title: "Photo Album manager"
date: 2005-08-28
forum: General Help
---

### Post by Calgarian on 2005-08-28
I am looking for a tool like lPhoto that will manage a large number of digital photos and support the creation of CD or DVD albums with menus and music that can be viewed on a TV with the appropriate DVD player. I tried getting an lPhoto SuSE .rpm and creating a .deb package with no luck. I looked at F-Spot, but it doesn't seem to have all the functions and I'm a little leary of Mono as I've not heard a bunch of good stuff about it.

Is DVD-Slideshow the only solution? QDVDAuthor doesn't seem to offer captions capability on a slideshow unless I'm not understanding it.

---

### Post by mort1 on 2005-08-31
you can try digikam, with plugins, its in synaptic and kpackage.. lphoto its based on digikam..

---

### Post by Perfect Storm on 2005-08-31
If you are using Gnome desktop. Go to the tabs Application --> Graphics an choose **gThumb Image viewer**.

---

### Post by Calgarian on 2005-09-02
Thanks for the extra info on Digikam. I did look at it, but some how I missed the Kipi Plugin part. It appears to offer what I want. Now all I need to do is find them. Do you know which repository the kipi's are in? They are not on my machine or in my repository list right now.

---

### Post by Nightfall on 2005-09-02
[here](http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php) 

Link directly coming from [www.digikam.org](www.digikam.org), download section.
It works successfully on my hoary, have fun!

---

### Post by Calgarian on 2005-09-02
Once again the Ubuntu/Kubuntu community is amazing. Thanks for all the help. I managed to get this repository to find the latest Digikam and Kipi-plugins and it looks like it will do what I need. I'm studying docs right now. Once again, thanks a whole bunch.

deb [http://www.mpe.mpg.de/~ach/kubuntu/hoary](http://www.mpe.mpg.de/~ach/kubuntu/hoary) ./

---

### Post by jbinc1 on 2005-09-11
Did you have any luck with the digikam repositories? When I try to install the kipi-plugins in synaptic, I keep getting a software not autheticated error.

---

### Post by irish rebel on 2006-01-02
Actually lphoto is not based on digikam, I have tested digikam on 4 differant boxes with 4 differant distros none of which would let me create a vcd or dvd .
Lphoto is a completely homegrown app , it is written in python and was designed to mimic iphoto from apple it works good but is near impossable to get running on anything other than Suse. qdvdauthor does allow to make a dvd with music in background but like digikam it crashes on the imagemagick library . I have posted on differant forums the problem and have not recieved a satifactory responce.
The best I can come up with is to install picasso2 with wine it works.

---

### Post by anil_robo on 2006-01-02
Also see [this]("http://ubuntuforums.org/showthread.php?t=102405"). Worth a view.

---

