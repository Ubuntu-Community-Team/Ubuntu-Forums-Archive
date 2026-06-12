---
title: "How do I install xine ?"
date: 2005-10-19
forum: General Help
---

### Post by chetanthaker on 2005-10-19
Hey guys

I've downloaded xine-lib-1.0.3.tar.gz and xine-ui-0.99.4.tar.gz

and untarred them to my desktop in my home directory

How when i try to say 

```
$ ./configure
```  

it gives me this error

```
ceetee@CeeTee:~/Desktop/xine-lib-1.0.3$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```


Please tell me what am I supposed to do 


Thanx 

CeeTee

---

### Post by Samuel on 2005-10-19
you can install it with apt-get

```
sudo apt-get install xine-ui
```

or if you prefer you can use synaptic and search for xine-ui

---

### Post by chetanthaker on 2005-10-19
Doesnt work

This is what I get

```
ceetee@CeeTee:~$ sudo apt-get install xine-ui
Password:
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate

```

---

### Post by Syphin on 2005-10-19
sounds like you need to uncomment the 'universe' repo in your sources.list file.

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)    --Bottom half for breezy

---

### Post by chanders on 2005-10-19
As the above post says, you need to edit your sources.list file so that your computer knows where to find xine....

open a terminal and type
```
sudo gedit /etc/apt/sources.list
``` 

then remove the # in front of all the words 'deb' eg if you see 

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

remove the # so it now shows

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

save your file, run synaptic and click on 'reload' when it is finished do a search for xine-ui and install it.....

You might want to install all the other codecs too. See the Ubuntu Guide for a full explanation....

---

### Post by chetanthaker on 2005-10-21
[QUOTE=chanders]As the above post says, you need to edit your sources.list file so that your computer knows where to find xine....

open a terminal and type
```
sudo gedit /etc/apt/sources.list
``` 

then remove the # in front of all the words 'deb' eg if you see 

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

remove the # so it now shows

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

save your file, run synaptic and click on 'reload' when it is finished do a search for xine-ui and install it.....

You might want to install all the other codecs too. See the Ubuntu Guide for a full explanation....[/QUOTE]
Hey Chanders

Thanx for the help with the comments in the sources.lst file

I got the UI part working -- how do i install the codecs ?

I have downloaded the libs from xine (I hope they are the codecs) -- I try to configure them and it says that C Compiler cannot create executables

Please help 

CeeTee

---

### Post by XDevHald on 2005-10-21
[quote=chetanthaker]Hey Chanders

Thanx for the help with the comments in the sources.lst file

I got the UI part working -- how do i install the codecs ?

I have downloaded the libs from xine (I hope they are the codecs) -- I try to configure them and it says that C Compiler cannot create executables

Please help 

CeeTee[/quote] 

[http://www.ubuntuforums.org/showthread.php?p=432013#post432013](http://www.ubuntuforums.org/showthread.php?p=432013#post432013)

Scroll down to the 2nd to the last post and you will see the codecs source to add to your sources.list also, be sure to read the post of mine below it as it is very important you do those two commands in a terminal to get the gpg keys to allow the breezy packages from that server to be downloaded and installed from the server.

---

### Post by chetanthaker on 2005-10-21
[QUOTE=Steve Myers][http://www.ubuntuforums.org/showthread.php?p=432013#post432013](http://www.ubuntuforums.org/showthread.php?p=432013#post432013)

Scroll down to the 2nd to the last post and you will see the codecs source to add to your sources.list also, be sure to read the post of mine below it as it is very important you do those two commands in a terminal to get the gpg keys to allow the breezy packages from that server to be downloaded and installed from the server.[/QUOTE]
Ok Steve,

I'm downloading the tar.gz file from that website you noted ... 13MB

Ok, once I'm done downloading it, how do I install/compile it ??

Please do help me... kinda newbie to Linux

CeeTee

---

### Post by XDevHald on 2005-10-21
Wait, you want to do these following steps in a terminal

**Step 1**
>  sudo gedit /etc/apt/sources.list 

[B]Step 2

[/B]Place the deb sources at the bottom in your source.list that you have open and click **SAVE.**
> deb [http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/") breezy-seveas all
 deb-src [http://seveas.ubuntulinux.nl/]("http://seveas.ubuntulinux.nl/") breezy-seveas all 

[B]Step 3

[/B]Type these two commands seperately and you should get it to show an **OK**
> gpg --keyserver subkeys.pgp.net --recv-keys 1135D466 
  gpg --export --armor 1135D466 | sudo apt-key add - 
Good Luck :)

---

### Post by Tolomir on 2005-10-21
[QUOTE=Steve Myers]Wait, you want to do these following steps in a terminal
...
Good Luck :)[/QUOTE]

Thank you, just want to inform you that I have posted your advice on the german site: [http://www.ubuntuusers.de/viewtopic.php?p=99628#99628](http://www.ubuntuusers.de/viewtopic.php?p=99628#99628)
(translated of cause)

Tolomir

---

### Post by chetanthaker on 2005-10-21
Hey Steve, 

Thanx for the info

I finally got the video working 

Now, when i try to play a avi file, it doesnt give out any sound
and if i play a WMV, no video, but yes to audio

I downloaded the tarball from that site you suggested (13MB)

how do i extract them and where do i do it ?

Thanx

CeeTee

---

### Post by chetanthaker on 2005-10-21
Hey Steve

I got the video working for AVIs but not WMVs but then theres no sound in AVI files and there is audio in WMVs

how do i install and where do i install the tarball of win32 codecs from that site you suggested ?

---

### Post by XDevHald on 2005-10-21
[quote=Tolomir]Thank you, just want to inform you that I have posted your advice on the german site: [http://www.ubuntuusers.de/viewtopic.php?p=99628#99628]("http://www.ubuntuusers.de/viewtopic.php?p=99628#99628")
(translated of cause)

Tolomir[/quote] 
Thank You Tolomir!

Never had anyone do that for me before, so it's a really awesome to see the members take the information and place it all over the net on other forums of ubuntu, great stuff, thank you!

-------------------------------------------------------------------------------------------------------------------


Now for[B] chetanthaker

Getting sound to play on a wmv file:[/B]
  > [http://www.ubuntuforums.org/showthread.php?t=25668&highlight=playing+wmv]("http://www.ubuntuforums.org/showthread.php?t=25668&highlight=playing+wmv")  
[B]Getting wmv files to play in firefox & totem-xine:
[/B]> [http://ubuntuforums.org/showthread.php?t=3450]("http://ubuntuforums.org/showthread.php?t=3450") 
[B]Installing the codecs from Synaptic:
[/B]> sudo apt-get install w32codec Good Luck :)

**EDIT: **Make sure you have gstreamer-0.8 installed as well, this will make a difference in your sound.

---

