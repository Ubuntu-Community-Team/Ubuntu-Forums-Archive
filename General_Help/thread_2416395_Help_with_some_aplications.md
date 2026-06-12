---
title: "Help with some aplications"
date: 2019-04-09
forum: General Help
---

### Post by radu19842 on 2019-04-09
Hello to all , hope all is good . I started using Xubuntu from
some time now , i had a desktop pc but the mother board "died" so as i am short on money i bought a a laptop , not high performance at all , its **ASUS 15.6'' X541NA, HD, Procesor Intel® Celeron® Dual Core N3350 (2M Cache, up to 2.4 GHz), 4GB, 500GB, GMA HD 500** i have xubuntu  18.04 LTS , instead of photoshop i use Gimp 2.10 and Pinta , allmost all software works good but i have a problem , i cant run (i guess so) inkskape instead of illustrator , or Krita . I did not installed it as i don't know if it works on my system . So what do you think will inkskape or krita work slow , medium or "great" ? Instead of inskape or Krita what other vector graphic software from the library or on the web installed trough terminal or other way that could work decent ? Thank you so much , sorry to bother you and i must have to say i will never use microsoft windows or paid software anymore , ubuntu/linux (xubuntu in my case) . Good job and all my respect to all of you who work hard for us to enjoy free software . A good evening !  :)

---

### Post by Rubi1200 on 2019-04-09
Hi and welcome to the forums :-)

I can't answer your question directly since I do not use Xubuntu or vector graphics software but this link might help lead you in the right direction:
[https://itsfoss.com/vector-graphics-editors-linux/](https://itsfoss.com/vector-graphics-editors-linux/)

Good luck!

---

### Post by radu19842 on 2019-04-09
Thank you **Rubi1200** i apreciate it , i will look at the system requirements for the programs on that list ! Other tips/advices are welcomed !

---

### Post by radu19842 on 2019-04-09
I need an alternative to **Inskape/Krita **witch demands a **"monster" of a pc" **, at least **on windows 7,8,10** cause i dont know if witch are the system requirements on **xubuntu 18.04 LTS** , so i need an alternative witch can work on my system !
All the best and good evening ! :KS

---

### Post by DuckHook on 2019-04-09
> **radu19842 said:**
> …will inkskape or krita work slow , medium or "great" ?…
Your laptop is not underpowered at all. It's pretty middle-of-the-road. However, it has an integrated GPU that is not high-powered, and vector graphics rely on the GPU more than anything, especially if you are thinking of animation.

So the answer to your question depends on what you want to do in Inkscape. Drawing simple vectors won't tax your machine. Even moderate svgs will be fine. Very complex vector manipulation in real time? That will range from very sluggish to unbearable. The same applies to CAD work.

Then again, heavy graphics are not meant to be handled on laptops of any kind. That's usually workstation territory. You can always try Inkscape to see how it works on your machine. It's free and can be purged if you don't like it.

Incidentally, Krita is a lot lighter than Inkscape (meaning it won't do as much), but it will drag in lots of Qt libraries that are not part of a standard Xubuntu install. Might want to think about whether you want that, or just Inkscape alone.

---

### Post by radu19842 on 2019-04-09
> **DuckHook said:**
> Your laptop is not underpowered at all. It's pretty middle-of-the-road. However, it has an integrated GPU that is not high-powered, and vector graphics rely on the GPU more than anything, especially if you are thinking of animation.

So the answer to your question depends on what you want to do in Inkscape. Drawing simple vectors won't tax your machine. Even moderate svgs will be fine. Very complex vector manipulation in real time? That will range from very sluggish to unbearable. The same applies to CAD work.

Then again, heavy graphics are not meant to be handled on laptops of any kind. That's usually workstation territory. You can always try Inkscape to see how it works on your machine. It's free and can be purged if you don't like it.

Incidentally, Krita is a lot lighter than Inkscape (meaning it won't do as much), but it will drag in lots of Qt libraries that are not part of a standard Xubuntu install. Might want to think about whether you want that, or just Inkscape alone.
Good evening and thank you for the reply , i just want to create logos , drawings (not complicated and stuffed up drawings ) simple illustrations . I don't want to work with animations and 3D stuff at all , do you think it will work ok ? All the best ! :)

---

### Post by Holger_Gehrke on 2019-04-09
A small hint to enhance performance while working with Inkscape: "View"->"Display Mode"->"No Filters". On my netbook (Asus EEE R101, <2GHz, 2GB RAM, dual core Intel Atom) it was quite possible to do simple work in Inkscape as long as I didn't forget to deactivate the filters ...

Also, there's a vector-graphics package that is part of LibreOffice: LibreOffice Draw. I don't know if it's installed by default or if you have to install it separately from the rest of LO. I remember it being less capable than Inkscape but working quite nicely on the netbook I mentioned.

Holger

---

### Post by radu19842 on 2019-04-09
> **Holger_Gehrke said:**
> A small hint to enhance performance while working with Inkscape: "View"->"Display Mode"->"No Filters". On my netbook (Asus EEE R101, <2GHz, 2GB RAM, dual core Intel Atom) it was quite possible to do simple work in Inkscape as long as I didn't forget to deactivate the filters ...

Also, there's a vector-graphics package that is part of LibreOffice: LibreOffice Draw. I don't know if it's installed by default or if you have to install it separately from the rest of LO. I remember it being less capable than Inkscape but working quite nicely on the netbook I mentioned.

Holger
Good evening , thank you si much for your reply , all the best ! :)

---

### Post by DuckHook on 2019-04-09
> **radu19842 said:**
> …i just want to create logos , drawings (not complicated and stuffed up drawings ) simple illustrations . I don't want to work with animations and 3D stuff at all , do you think it will work ok ?…

> **DuckHook said:**
> …Drawing simple vectors won't tax your machine. Even moderate svgs will be fine…

…You can always try Inkscape to see how it works on your machine. It's free and can be purged if you don't like it…;)

---

### Post by dragonfly41 on 2019-04-09
You can play with svgedit ..

[https://svg-edit.github.io/svgedit/releases/latest/editor/svg-editor.html](https://svg-edit.github.io/svgedit/releases/latest/editor/svg-editor.html)

and install it locally if you like it.
But Inkscape is good.

[P.S.]  I forgot to add this one too.

[http://snapsvg.io/](http://snapsvg.io/)

It comes from the author of Raphael.js.

---

### Post by radu19842 on 2019-04-09
> **DuckHook said:**
> ;)

So my future work will work quite smooth , and i will ad the advice of **Holger_Gehrke **and based on your advice ill try it out and hope for the best !
Thank you all , means allot for me !
Have a great evening !

---

### Post by radu19842 on 2019-04-09
> **dragonfly41 said:**
> You can play with svgedit ..

[https://svg-edit.github.io/svgedit/releases/latest/editor/svg-editor.html](https://svg-edit.github.io/svgedit/releases/latest/editor/svg-editor.html)

and install it locally if you like it.
But Inkscape is good.

[P.S.]  I forgot to add this one too.

[http://snapsvg.io/](http://snapsvg.io/)

It comes from the author of Raphael.js.
Good evening and thank you allot for your reply , ill see about those aplications ! :)

---

### Post by radu19842 on 2019-04-09
I want to tank you all so much for your help and advices,helps allot and means allot , you are all awesome!
Have a great evening and all the best from Romania ! ;) 
P.S.-Long live free , open source software and ubuntu alike ! ;) ;) ;)

---

### Post by radu19842 on 2019-04-13
Hello , since i don't want to open a new thread i have one or two questions . In my **Xubuntu 18.04 LTS Bionic** **Beaver[COLOR=#444444][FONT=&amp] [/FONT][/COLOR]**i  have both **2.8** and **2.10** versions of **Gimp** and also two versions of** Inkscape** **0.92.3-1 **and **0.92.4.**Is a problem if i install both versions , will it work , will it be apearing problems ?
Thank you and happy weekend !  ;)

---

### Post by dragonfly41 on 2019-04-13
You could use update-alternatives to switch between two or more installed versions of applications.

[http://manpages.ubuntu.com/manpages/trusty/man8/update-alternatives.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/update-alternatives.8.html)

I have not used it with Inkscape and Gimp but certainly with PHP, and Java.

---

### Post by DuckHook on 2019-04-13
> **radu19842 said:**
> … if i install both versions , will it work , will it be apearing problems ?…

You are probably seeing the repo version and the snap version of these apps. While it is possible for these apps to exist side-by-side, I do not recommend this.

[LIST=1]
[*]It is confusing
[*]You are new to Ubuntu and Linux in general
[*]You already have concerns about using too much resources
[/LIST]
Therefore, if I were you, I would keep things simple and install the repo version of these apps alone. Do not install the snap version since snap introduces further complexities that are not needed while you are in learning mode. The snap version is not appreciably superior to the repo version. It is marginally newer and may have a few more features, but this is not a good enough reason to live with the added complexity.

As a new user, it is always advisable to keep things as simple as possible and only add apps/services/functionality as you become more proficient and confident with the OS.

---

### Post by radu19842 on 2019-04-13
> **DuckHook said:**
> You are probably seeing the repo version and the snap version of these apps. While it is possible for these apps to exist side-by-side, I do not recommend this.

[LIST=1]
[*]It is confusing
[*]You are new to Ubuntu and Linux in general
[*]You already have concerns about using too much resources
[/LIST]
Therefore, if I were you, I would keep things simple and install the repo version of these apps alone. Do not install the snap version since snap introduces further complexities that are not needed while you are in learning mode. The snap version is not appreciably superior to the repo version. It is marginally newer and may have a few more features, but this is not a good enough reason to live with the added complexity.

As a new user, it is always advisable to keep things as simple as possible and only add apps/services/functionality as you become more proficient and confident with the OS.
Thank you very much , will install gimp 2.8 instead of gimp snap 2.10 and Inkscape 0.92.3-1 instead of snap version . Have a good evening !

---

### Post by radu19842 on 2019-04-14
Good evening , since i don't want to open another topic , i want to ask how can i install Gimp plugins trough terminal (for inskape too if possible) or in another way , thank you and have a good evening ! :)

---

### Post by DuckHook on 2019-04-14
> **radu19842 said:**
> …how can i install Gimp plugins trough terminal
```
sudo apt install gimp-plugin-registry
```
> …for inskape too if possible…
[Instructions here]("https://inkscape.org/gallery/=extension/").
> …or in another way…
Some websites tell you to install a PPA. For new users, I do not recommend PPAs. They often break apt and lead to dependency hell. I suggest that you stay with the commonly offered and readily available extensions for now. GIMP extensions are available from the Ubuntu repos. Inkscape extensions are available from Inkscape's official site. These are the only ones you should install until you are proficient enough with Ubuntu that you can fix dependency issues on your own that are caused by breaking apt.

---

### Post by radu19842 on 2019-04-15
Thank you very much , i opened a topic on next link [https://ubuntuforums.org/showthread.php?t=2416755]("http://ubuntuforums.org/showthread.php?t=2416755") about my new asus laptop and the hardware and integrated GPU , now i have placed some questions there but i will ask here if i can install K3D [http://www.k-3d.org/](http://www.k-3d.org/) witch i know is an old 3d modelling program , wondering if i can install , and how , from terminal or other way , and if it meets minimum requirements for my system in the first link topic ? Have a good evening ! :)

---

### Post by dragonfly41 on 2019-04-15
If you are engaged in 3D modelling then try [Blender]("http://ubuntuhandbook.org/index.php/2017/09/blender-2-79-released-install-it-in-ubuntu/") although I don't know if you will require more than your 4GB RAM.
I would limit the number of apps you have open at any time.

---

### Post by radu19842 on 2019-04-16
> **dragonfly41 said:**
> If you are engaged in 3D modelling then try [Blender]("http://ubuntuhandbook.org/index.php/2017/09/blender-2-79-released-install-it-in-ubuntu/") although I don't know if you will require more than your 4GB RAM.
I would limit the number of apps you have open at any time.

Hello and thank you for the answer , but i don't know if my system is up for it , i was thining of **K3D **&#8203;since it has lower "needs" regarding the system resources !
 
[B]System: Host: radu-X541NA Kernel: 4.18.0-17-generic x86_64 bits: 64
[B]Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.2 LTS
[B]Machine: Device: laptop System: ASUSTeK product: X541NA v: 1.0 serial: N/A
[B]Mobo: ASUSTeK model: X541NA v: 1.0 serial: N/A
[B]UEFI: American Megatrends v: X541NA.318 date: 02/27/2018
[B]Battery BAT0: charge: 17.7 Wh 51.9% condition: 34.1/34.6 Wh (99%)
[B]CPU: Dual core Intel Celeron N3350 (-MCP-) speed/max: 1083/2400 MHz
[B]Graphics: Card: Intel Device 5a85
[B]Display Server: x11 (X.Org 1.20.1 )
[B]drivers: modesetting (unloaded: fbdev,vesa)
[B]Resolution: 1366x768@60.02hz
[B]OpenGL: renderer: Mesa DRI Intel HD Graphics 500 (Broxton 2x6)
[B]version: 4.5 Mesa 18.2.8
[B]Network: Card-1: Realtek RTL810xE PCIE Fast Ethernet controller
[B]driver: r8169
[B]Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter
[B]driver: rtl8723be
[B]Drives: HDD Total Size: 256.1GB (4.2% used)
**ID-1: /dev/sda model: Micron_1100_MTFD size: 256.1GB**[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

---

### Post by dragonfly41 on 2019-04-16
> [COLOR=#000000]but i don't know if my system is up for it[/COLOR]

One way to test if it works is to install it and you can always reverse this experiment by removing later if it is not responsive.

---

### Post by radu19842 on 2019-04-16
> **dragonfly41 said:**
> One way to test if it works is to install it and you can always reverse this experiment by removing later if it is not responsive.
Thank you very much ,  have a nice day ! P.S. - Since i am new to ubuntu i want to ask you if you can help me how to install **K3D**  via terminal or in some kind of other manner . My system and os are x64  and dont know if it exists a K3D version for x64

---

### Post by dragonfly41 on 2019-04-16
I am on Ubuntu 16.04 and I used Synaptic Package Manager to look for k3d.  It is in there (and also k3d-data) so you should not need to build as is explained here.

[http://www.k-3d.org/wiki/Ubuntu_and_Debian_Build](http://www.k-3d.org/wiki/Ubuntu_and_Debian_Build).

Become familiar with Synaptic Package Manager.

---

### Post by radu19842 on 2019-04-16
> **dragonfly41 said:**
> I am on Ubuntu 16.04 and I used Synaptic Package Manager to look for k3d.  It is in there (and also k3d-data) so you should not need to build as is explained here.

[http://www.k-3d.org/wiki/Ubuntu_and_Debian_Build](http://www.k-3d.org/wiki/Ubuntu_and_Debian_Build).

Become familiar with Synaptic Package Manager.

I did not have installed** Synaptic Package Manager** but i did installed it in terminal like bellow and the i installed **K3D** and dependencies , thank you so much [COLOR=#ff0000]**dragonfly41 **[/COLOR]****, have a good evening ! :)****[COLOR=#ff0000][/COLOR]

sudo apt-get update
sudo apt-get install synaptic

---

