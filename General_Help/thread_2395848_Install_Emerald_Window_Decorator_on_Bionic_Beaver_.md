---
title: "Install Emerald Window Decorator on Bionic Beaver 18.04 LTS"
date: 2018-07-07
forum: General Help
---

### Post by Cavsfan on 2018-07-07
I had been looking at how to do this and usually just find old .deb files but, I don't like using 5 year old .deb files that are for another version of Ubuntu.
So here is an easier way:
```
sudo apt update

sudo apt install git libtool pkg-config libwnck-dev libwnck-3-dev debhelper gtk3-engines-xfce libcairo2-dev libdecoration0-dev libxrender-dev libx11-dev gettext intltool intltool-debian libltdl-dev libtool autopoint automake build-essential libxi-dev

*g++-aarch64-linux-gnu --- this package may not be required to compile I leave it at your discretion whether to install it or not. 
(I left this out of the above command because I had to remove it afterwards but, it's up to you to install it if you want.)

(You may want to create a directory for these if you want, It will create 2 directories one **emerald** and the other **emerald-themes**. I created a folder in my Downloads directory called emerald that had both directories in it.)

git clone [https://github.com/compiz-reloaded/emerald](https://github.com/compiz-reloaded/emerald)

git clone [https://github.com/compiz-reloaded/emerald-themes](https://github.com/compiz-reloaded/emerald-themes)

Change directories were the emerald source is, then do the following commands, the same applies for the emerald-themes directory:

./autogen.sh

*Optional step - Configure after autogen.sh is done configure with:
./configure --prefix=/usr

make

sudo make install
```

Here is the YouTube video I got this from: I mainly just went by the commands but, feel free to listen to the video as there is some explaining of what is going on in the video.

[https://www.youtube.com/watch?v=jFlnnWqwEqg](https://www.youtube.com/watch?v=jFlnnWqwEqg)

Then go into CCSM Window decoration and put this in the command:

[ATTACH=CONFIG]280312[/ATTACH]

---

### Post by shemhamforash2 on 2019-01-05
dude I've done it, but how do I change themes once I import them in the emerald themer? :)

---

### Post by Cavsfan on 2019-01-05
Look for Emerald them manager. On Arch Linux Xfce, it's under Settings...

---

### Post by Cavsfan on 2019-01-05
Google is your friend. :lolflag:

---

### Post by shemhamforash2 on 2019-01-16
Hey did all of that, and if google was my friend I would not be here. Not trying to be rude or anything, but such comments are not helping, of course I have googled all there is, of course I have tried and it didn't work,...
For some reason when I click on the themes they just don't change. I even deleted my Ubuntu 18 and re-installed Ubuntu Mate, because its having that old environment so that it would work better ! 

But still no luck and am also having two guys helping me over Team Viewer + Discord, and no luck... :(

---

### Post by Cavsfan on 2019-01-17
> **shemhamforash2 said:**
> Hey did all of that, and if google was my friend I would not be here. Not trying to be rude or anything, but such comments are not helping, of course I have googled all there is, of course I have tried and it didn't work,...
For some reason when I click on the themes they just don't change. I even deleted my Ubuntu 18 and re-installed Ubuntu Mate, because its having that old environment so that it would work better ! 

But still no luck and am also having two guys helping me over Team Viewer + Discord, and no luck... :(

Are you saying you could not install emerald this way or can not find where Emerald Theme Manager is?

I believe this thread did not help me on 18.04 either. Try this from an older version. I think this is what worked for me.

[https://ubuntuforums.org/showthread.php?t=2381499](https://ubuntuforums.org/showthread.php?t=2381499)

---

### Post by Cavsfan on 2019-01-17
That thread in my last post is definitely where I got my Emerald from:

[ATTACH=CONFIG]282226[/ATTACH]

I did get it from this thread at least twice because I installed 18.04 several times before it went to 18.04.1 but, now I think the links have changed or whatever.

I guess for an LTS that is why they say to wait until the 1st point release before installing it as your primary OS.

---

### Post by Cavsfan on 2019-02-02
> **shemhamforash2 said:**
> Hey did all of that, and if google was my friend I would not be here. Not trying to be rude or anything, but such comments are not helping, of course I have googled all there is, of course I have tried and it didn't work,...
For some reason when I click on the themes they just don't change. I even deleted my Ubuntu 18 and re-installed Ubuntu Mate, because its having that old environment so that it would work better ! 

But still no luck and am also having two guys helping me over Team Viewer + Discord, and no luck... :(

So, did you accomplish the goal?

---

### Post by srosh88 on 2019-07-17
muchas gracias, a mi me funciono todo muy bien, ejecute cada uno de los comandos en lubuntu 18.04, y ahora puedo ver los bordes de las ventanas.

---

### Post by wildmanne39 on 2019-07-17
Hello and welcome to the forum srosh88, you have posted in an English only forum, please translate your post into English.

Thanks

---

### Post by srosh88 on 2019-07-17
thank you very much, to me all the commands has worked very well when I executed them, on lubuntu 18.04, and now I can see the edge of each window.

---

### Post by Cavsfan on 2019-07-19
> **srosh88 said:**
> muchas gracias, a mi me funciono todo muy bien, ejecute cada uno de los comandos en lubuntu 18.04, y ahora puedo ver los bordes de las ventanas.

> **wildmanne39 said:**
> Hello and welcome to the forum srosh88, you have posted in an English only forum, please translate your post into English.

Thanks

I used Google translate and it seems like it worked for srosh88. Good deal! :D

Here's what I got in the translation: 
[FONT=Roboto][SIZE=3]thank you very much, everything worked fine for me, run each of the commands in lubuntu 18.04, and now I can see the edges of the windows.[/SIZE][/FONT]

Playing around with the new 19.10 Xubuntu and am amazed that compiz, emerald and even the fusion-icon are in the repos. Glad to see that!

---

### Post by Cavsfan on 2019-07-19
> **srosh88 said:**
> thank you very much, to me all the commands has worked very well when I executed them, on lubuntu 18.04, and now I can see the edge of each window.

You are very welcome! I didn't see there was another post with the translation. 

Glad it worked for you! :D So the commands on this thread worked for you? They would not work for me, I had to use the other thread I posted that is listed on post #6.

---

### Post by yetimon_64 on 2019-07-20
> **Cavsfan said:**
> ...Playing around with the new 19.10 Xubuntu and am amazed that compiz, emerald and even the fusion-icon are in the repos. Glad to see that!
Yes that is good to see, I first heard of, but never got around to using, emerald about the time of Jaunty/Lucid and didn't understand at that time exactly what it was all about.

I am on Xubuntu 18.04 and use compiz for the cube and effects etc, but have never had much in the way of windows decoration so this thread peaked my interest quite a bit. Noting how old it is and your comments in post 1 and post 6 I moved on again till only a few weeks ago I stumbled across [[COLOR=#0000ff]--this site--.[/COLOR]]("http://www.ubuntubuzz.com/2019/02/how-to-compile-and-install-emerald-on-ubuntu-1804.html") 

With my interest sparked by this thread and the explanation and instructions of the site linked above I built and installed emerald for the first time ... its great, love it! 
Some results ... [ATTACH=CONFIG]283643[/ATTACH]   [ATTACH=CONFIG]283644[/ATTACH]

Sure hope emerald is in the repos for 20.04 as well. Although it wasn't at all hard to build here using the site I stumbled across, it would be very nice to see it continue in the repos for Xubuntu 20.04 as well. I probably wouldn't have even noticed that site if you hadn't posted this thread and peaked my interest again since the last time I heard of emerald about 9 or 10 years ago, I'm really glad you posted this :).

Cheers, yeti.

---

### Post by Cavsfan on 2019-07-20
+1  ^

I wish they (19.10) would have went with Compiz 0.8 vs. 0.9 which they used as 0.8 has the fish tank and all of the good experimental stuff. But, I'm still happy they have it and emerald, the wobbly windows etc.

I've got all Compiz 0.8 installed in Arch Linux.

---

