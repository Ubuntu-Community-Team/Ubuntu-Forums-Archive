---
title: "Google Earth Loads, but not really..."
date: 2008-04-27
forum: General Help
---

### Post by Norst on 2008-04-27
Ok, I've installed Google earth. Same as I had before on Feisty (now have clean inst of Hardy). Problem is, that when I launch it, the engine/interface loads but no support data seems to come in. No locations, earth model (although I see the stars and space in should be in, and I can rotate with 3d in that space). We can rule out video issues since the 3D environment loads. 
Now, when I 1st installed it, I accidentally used "**sudo** sh googleblahblah.bin", but since that I have removed all installed items that did (i think). I've also made sure that no new firewall is running (ufw). Any ideas why the data isn't loading? Thanks for any help.

Norst

 [[IMG]http://img238.imagevenue.com/loc91/th_24628_Screenshot-Google_Earth_122_91lo.jpg[/IMG]](http://img238.imagevenue.com/img.php?image=24628_Screenshot-Google_Earth_122_91lo.jpg)

---

### Post by UK-Wobbie on 2008-04-27
> **Norst said:**
> Ok, I've installed Google earth. Same as I had before on Feisty (now have clean inst of Hardy). Problem is, that when I launch it, the engine/interface loads but no support data seems to come in. No locations, earth model (although I see the stars and space in should be in, and I can rotate with 3d in that space). We can rule out video issues since the 3D environment loads. 
Now, when I 1st installed it, I accidentally used "**sudo** sh googleblahblah.bin", but since that I have removed all installed items that did (i think). I've also made sure that no new firewall is running (ufw). Any ideas why the data isn't loading? Thanks for any help.

Norst

 [[IMG]http://img238.imagevenue.com/loc91/th_24628_Screenshot-Google_Earth_122_91lo.jpg[/IMG]](http://img238.imagevenue.com/img.php?image=24628_Screenshot-Google_Earth_122_91lo.jpg)

Have you had a go reinstalling Google earth?

---

### Post by Norst on 2008-04-27
Yeah I had tried reinstalling many times. I looks like it has to do with some change in Hardy. I found this post on the google earth forums and it works now. 

> Alrighty,

Here's how I made google-earth work as user and not root:

First run the uninstaller in the directory you installed to (mine was /
opt/google-earth)

then rm -rf the empty directory

cd .config from your home directory
then do a rm -f Google/

finally, rm -rf .googleearth/

rerun the installer as root, and install to the default locations,
after it is done installing DO NOT click start, click QUIT and then
start google earth as your user, it worked for me. I guess the initial
run is a setup of the files, so if you run it as root, it sets
permissions for root only! 

Hope this helps others, and thank you for responding.

---

### Post by Julius on 2008-04-27
I'm also having problems with google earth.

I did the above (actually I just manually deleted the files as it doesnt let me run the uninstaller for some reason) and I still get the same error as before (which is:

Google Earth detected an error while trying to authenticate. Please check the following:
- your network connection (can you get to [www.gooogle.com?](www.gooogle.com?))
- your firewall settings
(are you blocking (/opt/google-earth/googleearth.bin?)

Error code: 29


Hardy 64-bit here

---

### Post by lizzard on 2008-04-27
> **Julius said:**
> I'm also having problems with google earth.

I did the above and I still get the same error as before (which is:

Google Earth detected an error while trying to authenticate. Please check the following:
- your network connection (can you get to [www.gooogle.com?](www.gooogle.com?))
- your firewall settings
(are you blocking (/opt/google-earth/googleearth.bin?)

Error code: 29


Hardy 64-bit here

I had the same issue with the 4.3 version.
Installing the lib32nss-mdns package solved it for me.
```
sudo aptitude install lib32nss-mdns
```

---

### Post by technotika on 2008-04-27
Hi guys seem to have same issue here tried all suggestions "many times" still no joy although logging in as root and running GE is all ok so for me it has to be permissions things  - any other ideas??

---

### Post by DeMus on 2009-04-26
> **lizzard said:**
> I had the same issue with the 4.3 version.
Installing the lib32nss-mdns package solved it for me.
```
sudo aptitude install lib32nss-mdns
```

Thank you so much. That did the trick. Now I see the earth again.

---

### Post by DeMus on 2009-04-26
I installed Jaunty on a clean disc, used the whole disc for it so I have a nice large home partition.
I try to install Google-Earth, but this time I am not so lucky. I get an error. (see attached picture).
I looked in Synaptic and I see that gtk2 is installed (see 2nd picture)
Why could I install it the first time, using a part of my old Hardy disc, and now when I use the complete disc I can not? What am I missing here? Both times I did a clean install, not an update from a previous version.
Who can help me?

---

### Post by ezren on 2009-05-16
```
sudo aptitude install lib32nss-mdns
```This worked for me too.

---

