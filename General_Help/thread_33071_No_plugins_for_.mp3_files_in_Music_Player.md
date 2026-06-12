---
title: "No plugins for .mp3 files in Music Player"
date: 2005-05-09
forum: General Help
---

### Post by migo on 2005-05-09
I'm running Hoary 5.04-i386 live on an Acer TMC303XMi-G.

I opened Music Player and attempted to add my library on an external USB 2.0 HD to it, I got an error message saying that it didn't have the plugins to support my entire library. I have a few .wma songs on there but the majority are .mp3 (VBR) and a few .mp3 (CBR). Where do I get the plugin to work it on the LiveCD?

---

### Post by dodger on 2005-05-09
ubuntu does not contain support for mp3 playback out of the box. due to licensing problems I suppose.
with an installed version, this is no problem because you can apt-get the necessary files, but of course this is not possible with a live-cd.

so, how about installing ubuntu?  ;-) 

dodger

---

### Post by migo on 2005-05-09
Well, I was actually using a live CD so I could copy my Windows directory to my external hard drive so I could try converting it to an install with nLite.

But installing Ubuntu is something I plan to do eventually, I was impressed with what it did handle well (configuring my keyboard to Dvorak and Wireless) and apparently it handles Tablet PCs better than most distros.

---

### Post by dnix71 on 2005-05-09
Yeah, I noticed no mp3 support, too.
Everybody is getting scared of the chaos that licensing and software patents is causing. I posted a suggestion in another forum that there should be an mp3 to ogg converter with Ubuntu. When you try to play an mp3 it should tell you that Linux music is "ogg." 
Linux has a tremendous opportunity here to make ogg the preferred format for music and increase the market share of Linux in general.

---

### Post by migo on 2005-05-10
Huh? How would saying ogg is the linux format increase its market share?

---

### Post by davidgypsy on 2005-05-10
[QUOTE=migo]Huh? How would saying ogg is the linux format increase its market share?[/QUOTE

Well, if there was a simple way to convert from mp3 to ogg, I for one would convert in a flash. Times that by a few million Linux users around the world, and you get a LOT of people, and hence more market share. It just has to be made easy for dummies like me, and marketed the right way. :)

---

### Post by xristos on 2005-05-10
[QUOTE=dodger]ubuntu does not contain support for mp3 playback out of the box. due to licensing problems I suppose.
with an installed version, this is no problem because you can apt-get the necessary files, but of course this is not possible with a live-cd.[/QUOTE]

What packets should I install to support mp3 playback ?

---

### Post by Lowe on 2005-05-10
apt-get install gstreamer0.8-mad

---

### Post by xristos on 2005-05-10
[QUOTE=Lowe]apt-get install gstreamer0.8-mad[/QUOTE]

I installed the above packet but I have the same problem even after a reboot .
When i try to play an mp3 with totem it crashes and in Rythmbox all my mp3 files cannot be selected . 

What should I do ?

---

### Post by Lowe on 2005-05-10
Sorry, no idea why it's not working. Run "gstreamer-properties" and make sure you have the correct sound driver selected.

---

### Post by derrick1985 on 2005-05-11
wget -c [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8

Taken straight from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by xristos on 2005-05-12
[QUOTE=derrick1985]wget -c [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install w32codecs
sudo apt-get install liblame0
sudo dpkg -i gstreamer0.8-lame_0.8.8-0.1_i386.deb
gst-register-0.8[/QUOTE]

I did all the above but with no result . 
I still am getting no mp3 in Ubuntu .

---

### Post by angrykeyboarder on 2005-05-12
[QUOTE=dodger]ubuntu does not contain support for mp3 playback out of the box. due to licensing problems I suppose.
with an installed version, this is no problem because you can apt-get the necessary files, but of course this is not possible with a live-cd.

dodger[/QUOTE]

I beg your pardon. I've been using the Hoary Ubuntu and Kubuntu Live CDs for weeks now and I apt-get up the wazoo.  The only downside of course is you have to do it after you start up each and every time.

One of the first things I download each time is gstreamer0.8-mad which  of course enables me to playback mp3s,

Actually after after about the third time I did this, I decided just to copy the debs to a USB flash drive and install them from there, saving download time and bandwidth.

But I digress.  Indeed, you can install packages if you are running the live CD.  Of course you're limited by how much RAM you have and it's certainly not as fast as installing on your hard drive with the regular distro, but it's still pretty cool.

---

### Post by angrykeyboarder on 2005-05-12
[QUOTE=xristos]I did all the above but with no result . 
I still am getting no mp3 in Ubuntu .[/QUOTE]

Just for the heck of it, try ```
apt-get install gstreamer0.8-mad
```  (it should have been installed with the gstreamer-plugins metapackage though).

[gstreamer0.8-mad](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad)  is the package you need to enable mp3 playback with gstreamer apps (such as Rhythmbox).

---

### Post by xristos on 2005-05-12
[QUOTE=angrykeyboarder]Just for the heck of it, try ```
apt-get install gstreamer0.8-mad
```  (it should have been installed with the gstreamer-plugins metapackage though).

[gstreamer0.8-mad](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-mad)  is the package you need to enable mp3 playback with gstreamer apps (such as Rhythmbox).[/QUOTE]

That was the first thing i did .
I wrote it in the previous page .
But no result....
Does anyone know what to do to locate the problem ???

---

### Post by derrick1985 on 2005-05-12
Does system sounds work in Ubuntu for you?

---

### Post by xristos on 2005-05-12
[QUOTE=derrick1985]Does system sounds work in Ubuntu for you?[/QUOTE]

Yes sound works and I can listen to mp3s through xmms .
The problem is with Music player and Totem

---

### Post by Lowe on 2005-05-13
[QUOTE=xristos]Yes sound works and I can listen to mp3s through xmms .
The problem is with Music player and Totem[/QUOTE]

They both use gstreamer, so your problem lies with gstreamer. Make sure you have the correct driver selected/installed.

---

### Post by providencia on 2005-06-02
[QUOTE=xristos]I installed the above packet but I have the same problem even after a reboot .
When i try to play an mp3 with totem it crashes and in Rythmbox all my mp3 files cannot be selected . 

What should I do ?[/QUOTE]
I had this same problem.
My solution was to run "gst-register-0.8" as root in terminal.
Well...just instead run "sudo gst-register-0.8", it's safer to play with an unloaded gun, I suppose.

If your version is different you can just type "gst" and hit tab twice to see the list of programs beginning with gst.
After that music player recognized my mp3s.

I use XMMS, but if Music Player is going to be installed, it's gonna work dangblammit!

---

### Post by xristos on 2005-06-03
[QUOTE=providencia]My solution was to run "gst-register-0.8" as root in terminal.[/QUOTE]

Thanks a lot providencia !!! 
The thing that worked for me was to run "gst-register-0.8" as normal user and not as root. And now I can listen to my mp3s from Totem and Music Player .  \\:D/

---

### Post by GalvestonDude on 2005-06-03
Well, if there was a simple way to convert from mp3 to ogg, I for one would convert in a flash. [/QUOTE]

I did it using Audacity.  Import your mp3 files into audacity, export ogg files.  Unfortunately, there's no way to do it in batches, so it's one by one.  Audacity is a good sound editor as well.

---

### Post by Zerocool10482 on 2005-07-10
I had all of those problems with mp3's are there anyone out there that can write a program that will covert to ogg without audacity. Calling all programmers. This noob is crying.  :-?  I just installed Ubuntu and I was so happy but I just want my music. I can play music cd but I can play mp3s or ogg. I go gstreamer and updated eveything with the manager.

I've installed alot of distro and Ubuntu is the only one that connected to the internet and install updates to the OS before you boot up. That is so cool. finally someone got it right. I'm happy with Ubuntu but if I could just get some music. that would be ok.

Is there another mp3 player that I could install though the update manager which is safer for me.

Thanks.

---

### Post by doom_Oo7 on 2005-07-11
to convert mp3 files to ogg files :

apt-get install mp32ogg

and then just mp32ogg [filepath] and he'll put the ogg file on your home/user/ directory..

you should all use .ogg : that's the best !  :smile:   :smile:

---

### Post by Leif on 2005-07-11
You should note that encoding from one lossy format to another is going to result in quite degraded sound quality.

---

### Post by Zerocool10482 on 2005-07-11
Thanks for the info. Can I use the manager to get it too. I would rather do it that way. I know I may have a loss in quality but I how else am I suppose to do with all this music I have. Play it on Windows.

I one thing that made me switch was that I could have freedom of changing anything I want without my PC crashing.

Thanks again.

---

### Post by UbunuAndrew on 2005-11-19
I realize that I'm not using liveCD, but rather installed Ubuntu, but this thread still helped me and I Would like to offer my thanks to those who help others. I was having the mp3 issues, and finally have that settled now. (Amazing XP didn't want to adopt my drivers, but Ubuntu didn't give a crap.. lol just took it in like a child.)

---

### Post by sinisterfuzzy on 2006-08-29
> **doom_Oo7 said:**
> to convert mp3 files to ogg files :

apt-get install mp32ogg

and then just mp32ogg [filepath] and he'll put the ogg file on your home/user/ directory..

you should all use .ogg : that's the best !  :smile:   :smile:

how come i cant find this?  or any of the apt-gets you are all posting?

---

### Post by mgmiller on 2006-09-01
> how come i cant find this? or any of the apt-gets you are all posting?

It's in the universe repository.  Do you have all your repositories turned on?  There are many threads here that discuss repositories and how to enable them.

---

