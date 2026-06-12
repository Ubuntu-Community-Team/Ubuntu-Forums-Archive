---
title: "[SOLVED] Video File Converter"
date: 2008-07-05
forum: General Help
---

### Post by Dyffo on 2008-07-05
I am now 100% Ubuntu - Microsoft is a forgotten word. Only one problem remains from the switchover - can anyone tell me of a software package for Video File Conversion from and to the various formats. I have an online version but the capacity is limited and certainly not large enough for a Full Video.When I solve this my new package is complete.:confused:

---

### Post by dentaku65 on 2008-07-05
Hi,
I don't know if I undestood well your needs; I suggest to take a look of pyTube (not in the repos), it has a very nice video converter for the videos downloade from youtube and for the videos in general.
[http://www.bashterritory.com/pytube/]("http://www.bashterritory.com/pytube/")

---

### Post by BlueSkyNIS on 2008-07-05
For simple and fast video conversion I use user friendly Avidemux. If you need something more sophisticated you may try mencoder. I'm sure there are many other programs, but I can't recall their names now :(

---

### Post by Dyffo on 2008-07-05
You have my needs exactly and I now have PyTube it is fantastic THANK YOU.

---

### Post by Linux&amp;Gsus on 2008-07-05
OK, that pytube thing looks really cool. I downloaded it but would someone be so kind telling me how I can install that from command line, incl dependencies? I know I could do right mouse click and from there somewhere install it but entering my password doesn't work. So, no Adept Manager for me :) But still not savvy enough with the CLI for things like this. :D

---

### Post by Dyffo on 2008-07-05
I just went straight to DOWNLOADS Left hand column, then to pyTube for LINUX, then scroll down to UBUNTU/DEBIAN, then hit download - hey presto it installs itself in Applications :- Sound & Video . Just open in the normal way.Very Simple no need for all tghis command line stuff !!!

---

### Post by Linux&amp;Gsus on 2008-07-05
Well, I downloaded a .deb file. Nothing is installed automatically. At least I can't find anything in the menu. So, I guess I need to install it. And I know that there are most likely dependencies that need to be installed as well.

---

### Post by Dyffo on 2008-07-05
You need to have installed G.Debi Package Installer. This is located in Applications/System Tools. If you dont have it go to Add/Remove in Applications - then type in G.Debi Package Installer - this will install to your system.

---

### Post by Linux&amp;Gsus on 2008-07-05
OK, maybe I didn't make myself clear. I don't need any installer application. I quickly checked; On the file mouse right click -> Open With -> GDebi Package Installer. It's all there.
Actually it says that it wants to install 8 dependencies. As I said earlier, I need some. So here we go.

But when I click install it's asking me for my (sudo) password. For some reason , however, my system is messed up and providing that password just doesn't do anything. And yes, I'm sure it type it in correct.

Anyways, I can install from command line. But since I'm not the big guru I keep forgetting how that works, unless I do it frequently. And as of now I only installed once a .deb file before.
So, what I need is the command for the terminal to install the .deb file incl check/install the dependencies.

Then rock'n'roll is upon me... :guitar:

Cheers.

---

### Post by Dyffo on 2008-07-05
Good Luck !!! I have never installed from a command line. At the moment I am struggling trying to install two programmes which are .bin files - any ideas ?

---

### Post by jualin on 2008-07-05
> **Dyffo said:**
> Good Luck !!! I have never installed from a command line. At the moment I am struggling trying to install two programmes which are .bin files - any ideas ?

Check this out! [How to install anything in Ubuntu.]("http://monkeyblog.org/ubuntu/installing/") And this for a [manual install (.bin, .tar ...)]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually")

---

### Post by dentaku65 on 2008-07-05
> **Linux&Gsus said:**
> Well, I downloaded a .deb file. Nothing is installed automatically. At least I can't find anything in the menu. So, I guess I need to install it. And I know that there are most likely dependencies that need to be installed as well.

You can try like this:
```
sudo dpkg -i filename.deb
```

Filename.deb is the deb file downloade from bashterritory; if installs ok, otherwise you will see which packages you need it to install.

---

### Post by Linux&amp;Gsus on 2008-07-06
Thanks guys, worked like a charm. Looks a very hot app, 3 thumbs up for that.

---

### Post by Dyffo on 2008-07-06
> **jualin said:**
> Check this out! [How to install anything in Ubuntu.]("http://monkeyblog.org/ubuntu/installing/") And this for a [manual install (.bin, .tar ...)]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually")
Hi Jualin - these have to be the most useful links ever !! - thank's - now it all seems so easy.

---

### Post by jualin on 2008-07-06
You are welcome pal! I had the same problems when I first started using Ubuntu. I was used to the "double click the .exe file" Windows approach, :lol:. Welcome to the community, and feel free to ask anything you want, even if it sounds dumb or silly. :guitar:

---

### Post by aktiwers on 2008-07-06
I love WinFF
[http://www.winff.org/](http://www.winff.org/)

Its ffmpeg with GUI!! :) Its the best.

---

### Post by jualin on 2008-07-06
> **aktiwers said:**
> I love WinFF
[http://www.winff.org/](http://www.winff.org/)

Its ffmpeg with GUI!! :) Its the best.

Looks like an Awesome application (with a capital A)lol, I personally find Avidemux to sophisticated for most video converting tasks. Thank you!

---

