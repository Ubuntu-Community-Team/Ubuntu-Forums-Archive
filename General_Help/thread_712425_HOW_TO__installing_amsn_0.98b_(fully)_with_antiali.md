---
title: "HOW TO : installing amsn 0.98b (fully) with antializing fonts"
date: 2008-03-01
forum: General Help
---

### Post by Claus7 on 2008-03-01
Hello,

after my first installation of amsn which took me about four days almost one and a half year ago, I wanted to upgrade my version of amsn to 0.98b version. Ubuntu is an open source operating system, so the libasound2 library that was desperately needed for the new version to work in Ubuntu Dapper Drake 6.06, I thought that it should be a minor issue to be solved. It wasn't so because it took me two days, yet I have made an improvement! 
In the begining I tried the deb packages which even though they are easily installed, they are not easily modified so as one to change some things according to one's needs. So the installation might fail. This was my incentive so as to install amsn sub version (Latest development version-SVN) in Ubuntu Dapper Drake.

So leaving out the theoretical parts aside that might be a nice post for Community Cafe, let's start on the installation procedure :

We want to install amsn 0.98b (the latest one up to the time I was writing this post) to Ubuntu Dapper Drake 6.06. The version of Ubuntu in question doesn't support the latest version of two important libraries that are needed in order for amsn not only to work but also to look nice. These are :

[LIST]
[*]Tcl 8.5.1
[*]Tk  8.5.1
[/LIST] 

and can be downloaded from here :
[http://www.tcl.tk/software/tcltk/8.5.html](http://www.tcl.tk/software/tcltk/8.5.html)

For amsn to work you have to install _**first**_ Tcl 8.5.1, **_secondly_** Tk  8.5.1 and **_thirdly_** amsn.

After you have downloaded the packages of the libraries unzip the tcl package and go inside the folder which is called unix. There as you are in a terminal type the following :

```
./configure
```
```
sudo make
``` (and give your password)
```
sudo make install
```

If all dependencies are ok (and I think that they should be ok) the installation is complete and nice. Go now to the tk package and do exactly the same thing as above. That way you have finished installing the libraries that are needed.

Now the installation of amsn is a little bit tricky. Unzip the file and remove the snit folder that you will find. If you do not do so, you might come accross this message :
[http://www.amsn-project.net/forums/viewtopic.php?p=25821&highlight=tkcximage](http://www.amsn-project.net/forums/viewtopic.php?p=25821&highlight=tkcximage)

Also in order to avoid this message :
[http://img254.imageshack.us/img254/5816/screenshotjv1.png](http://img254.imageshack.us/img254/5816/screenshotjv1.png)
that has to do with : Loading TkCximage failed
go to amsn script and change the third line which is :
exec wish $0 $@
with this:
exec wish**8.5** $0 $@

After that open a terminal inside amsn folder and type the following : 

```
./configure --with-tk=/usr/local/lib/ --with-tcl=/usr/local/lib/
```
```
sudo make
```
```
sudo make install
```

Now if you type amsn, msn should lanch properly.
YET, you might not be able to connect or if you prefer you might not be able to log in. There are two reasons why you can't do that. The one might be because of problems that the msn server network might face and secondly because your firewall doesn't allow you so. In the second case you need to open ports TCP 443 and TCP 1863.

Hope this helped. I provide links that were useful:
[http://ubuntuforums.org/showthread.php?t=649364](http://ubuntuforums.org/showthread.php?t=649364)
[http://www.amsn-project.net/forums/viewtopic.php?t=4738](http://www.amsn-project.net/forums/viewtopic.php?t=4738)
[http://suseforums.net/index.php?showtopic=10031](http://suseforums.net/index.php?showtopic=10031)
and
[http://rmbernardes.wordpress.com/2008/02/20/amsn-098svn-com-antialising-no-ubuntu-710/](http://rmbernardes.wordpress.com/2008/02/20/amsn-098svn-com-antialising-no-ubuntu-710/)

Regards!

---

### Post by Claus7 on 2008-03-03
Hello,

while I was using amsn I saw some things that needed refinement so I post them here:

In case you have slow transfer rate you should also check to forward port 6881 both in your firewall and your router. If you check also in preferences of amsn you will see that this is the port that amsn uses.

Now in case you face problems with sound there are a couple of things you have to adjust. The first error message I got and had to do with sound was that libsnack library 2.2.9 version or above was needed. I had this library installed, yet it didn't seem to be recognised. So I went there :
[http://www.speech.kth.se/snack/download.html](http://www.speech.kth.se/snack/download.html)
and downloaded the source release for all platforms version 2.2.10 (the size is 1.7MB). In order to install it I typed the following :

```
./configure --prefix=/usr/lib --with-tk=/usr/local/lib/ --with-tcl=/usr/l ocal/lib --enable-alsa
```

```
make
```

```
make install
```

In case you have an error while you execute configure, see what file is needed in the error log, find the folder that is in and give the right path after with-tk and with-tcl. Following the above you should have no problem, yet if you have installed tk and tcl in different folders you will have.

After that you have to type the following :

```
sudo ln -s /usr/lib/snack2.2 /usr/local/lib
```

Normaly you should have sound every time you open your amsn. In case still you cannot use your microphone you have to open amsn and then do CTRL+N.
Configure your camera and microphone (test the different options to see with which you hear sound and which is the right option for your microphone). If you still have problems with your microphone check your sound settings and see that your microphone is enabled. Even doing that I have to say that sometimes I have to redo the configuration with the microphone and choose different settings because I could not send sound clips via CTRL+N. I think that that's all. Any remarks are welcome. Enjoy amsn!

Regards!

---

### Post by Claus7 on 2008-05-01
Hello,

I automated the whole procedure so if someone wants to install amsn svn (end of April 2008 ), someone can do so only by typing :

```
./amsnsvn_098b_25_4_08.sh
```

You do not have to download any package for yourself and you can lanch the above command anywhere you have downloaded the script itself. It will take you 5-10'. If things go ok you have to give your password only once and in your /home/*username*/ you will see an amsn_svn directory.

I inform you that the whole procedure took place in Dapper Drake 6.06. The packages that are downloaded are source ones and compiled simultaneously. I do not think that you will have problems in other distributions of ubuntu, yet you never know. If something goes wrong remove the aforementioned directory and restart again.

I'm working also in compiling farsight and its dependency -glib- from source in order to have audio (and video simultaneously?) support, yet I get that error :> configure: error: This package requires GLib >= 2.12 to compile
The versions are glib-2.16.3 and farsight2-0.0.2
Probably I do not give the right paths when I compile...

Regards!

I attach the script file:

---

### Post by Claus7 on 2008-05-03
Hello,

FYI I should tell you to avoid messing with the installation of farsight in dapper because it needs a lot of dependencies that most of them must be compiled from source (not an easy task). For someone who is still interested I needed the following (and I didn't finish the process):

[LIST]
[*]glib from here [http://ftp.acc.umu.se/pub/GNOME/sources/glib/2.16/](http://ftp.acc.umu.se/pub/GNOME/sources/glib/2.16/) 
Doing in the end inside /lib directory the link ```
sudo ln -s /usr/local/lib/libglib-2.0.so.0.1600.3 glib
``` I was able to avoid the glib dependency issue. I could also avoid it if while configuring farsight I was typing ```
./configure glib=/usr/local/
```
[*]gst-plugins-farsight-0.12.7.tar.gz from [http://farsight.freedesktop.org/releases/gst-plugins-farsight/](http://farsight.freedesktop.org/releases/gst-plugins-farsight/)
[*]gstreamer-0.10.19.tar.gzht/ from [http://gstreamer.freedesktop.org/src/gstreamer/](http://gstreamer.freedesktop.org/src/gstreamer/)
[*]gst-plugins-good-0.10.8.tar.gz from [http://gstreamer.freedesktop.org/src/gst-plugins-good/](http://gstreamer.freedesktop.org/src/gst-plugins-good/)
[*]liboil-0.3.14.tar.gz	from [http://liboil.freedesktop.org/download/](http://liboil.freedesktop.org/download/) (for gstreamer plugins)
[*]gst-plugins-base-0.10.19.tar.gz from [http://gstreamer.freedesktop.org/src/gst-plugins-base/](http://gstreamer.freedesktop.org/src/gst-plugins-base/)
[*]pygtk-2.12.1.tar.gz from [http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/](http://ftp.gnome.org/pub/GNOME/sources/pygtk/2.12/)
[/LIST]

also from synaptic someone has to download bison, flex, libxml2, libxml2-dev (for gstreamer)

and the list goes on for someone who wants to experiment more...

Also here someone should find a solution to the headers dependency I faced during the pygtk installation.

[http://ubuntuforums.org/showthread.php?t=225309](http://ubuntuforums.org/showthread.php?t=225309)

Regards!

---

### Post by Xmister on 2008-06-05
> **Claus7 said:**
> ...

In line 62, I think it should be
```
./configure --with-tcl=/usr/local/lib/ --with-tk=/usr/local/lib
```
instead of 
```
./configure --with-tcl=/usr/lib/ --with-tk=/usr/lib
```

---

### Post by Claus7 on 2008-06-07
Hello,

> **Xmister said:**
> In line 62, I think it should be ...


thank you for the feedback. If you see in my first post the command I use is the one you propose. Wrong typing there then, yet now I think that it is ok.

Regards!

---

