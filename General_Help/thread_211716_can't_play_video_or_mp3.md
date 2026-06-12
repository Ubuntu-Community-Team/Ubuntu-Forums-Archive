---
title: "can't play video or mp3"
date: 2006-07-08
forum: General Help
---

### Post by Sabrage on 2006-07-08
HI

I just installed Ubuntu 6.06 two days ago, and I love it. The only problem I have is that I can't play mp3 or video (wmv,mov, mpg, etc.) I use the mediaplayers that came with the Ubuntu CD: Rhythmbox and Totem Movie PLayer. 

With Mp3's in Rhythmbox no sound, no message, nothing. Mp3's in Movieplayer says I don't have the decoder I need.

Videos in Movieplayer says too that I need to install the decoders to play the file.

So how do I install the decoders I need for Movieplayer? And how can I play mp3? Is this some kind of DRM or what?[-o<

---

### Post by Rackerz on 2006-07-08
Go here; [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That page will tell you all you need to know ;).

---

### Post by Sabrage on 2006-07-08
Thanks Rackerz, it was spot on. Just one more thing: I couldn't find the packages in the add/remove applications menu? the packages are named > 
gstreamer0.10-ffmpeg
#

gstreamer0.10-pitfdll
#

gstreamer0.10-plugins-bad
#

gstreamer0.10-plugins-bad-multiverse
 etc.. and the applications listed have names like Kino, amaroK, etc?

---

### Post by MrMojoRising on 2006-07-08
Hi there, 

did you update your sources list for Aptitude?
If not do this - 

1.[COLOR="SeaGreen"] sudo gedit /etc/apt/sources.list[/COLOR]
2.Erase everything there and copy this into it...then save and close gedit...

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```
3. do a [COLOR="SeaGreen"]sudo aptitude update[/COLOR]
4. then search aptitude for that packages and apps...they'll be there.
5. install mplayer (it plays everything) [COLOR="SeaGreen"]sudo aptitude install mplayer[/COLOR]

---

### Post by Rackerz on 2006-07-08
To install them you just need to open up a terminal and type;

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by Sabrage on 2006-07-08
thanks MrMojoRising and Rackerz. Rackerz: I got this from the terminal:>  sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-ffmpeg is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-ffmpeg has no installation candidate


and I tried some video and mp3, still not working.

MrMojoRising, I completed steps 1,2,3, but got stuck at #4! How do I search Aptitude?

---

### Post by ubuntu27 on 2006-07-08
> **Sabrage said:**
> thanks MrMojoRising and Rackerz. Rackerz: I got this from the terminal:

and I tried some video and mp3, still not working.

MrMojoRising, I completed steps 1,2,3, but got stuck at #4! How do I search Aptitude?

Open:

System/Adminsitration/Synaptic Package Manager

And then Search tha package that you need to install.
Slect them by clicking on the white check box
then Click on Apply.

---

### Post by Sabrage on 2006-07-08
thanks ubuntu27 and everyone, I got almost everything working now- mp3 perfect and qt working. thanks.

---

### Post by ubuntu27 on 2006-07-09
> **Sabrage said:**
> thanks ubuntu27 and everyone, I got almost everything working now- mp3 perfect and qt working. thanks.

You're WElcome. :)

---

### Post by MrMojoRising on 2006-07-09
glad to hear you got everything. 
What else isn't working, i can help!

f.y.i - Using apt-get at the command line is kindof goin out of style nowadays (even thought that's in all the ubuntu how-to's). I'd recommend using aptitude instead; eg [COLOR="seagreen"]sudo aptitude install mplayer[/COLOR] as opposed to [COLOR="SeaGreen"]sudo apt-get install mplayer[/COLOR]

You can sercht the forums for reasons as to why that is : aptitude vs. apt-get

breifly though, it's because aptitude handles dependencies better.

---

