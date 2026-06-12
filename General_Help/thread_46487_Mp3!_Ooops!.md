---
title: "Mp3! Ooops!"
date: 2005-07-05
forum: General Help
---

### Post by Shinitenshi on 2005-07-05
Ok i am a first time ubuntu user and I have a windows 2003 server hosting all my mp3's and videos but every time I connect to it and try to view a video or mp3 it wont let me! It says:

Totem could not play 'smb://server/My Documents/MoisesTadeo/My Music/Drowning Pool/Drowning Pool - Bodies.mp3'.

There were no decoders found to handle the stream in file "smb://server/My%20Documents/MoisesTadeo/My%20Music/Drowning%20Pool/Drowning%20Pool%20-%20Bodies.mp3", you might need to install the corresponding plugins

Do i need to install somthing in order to get this working?

I use a cd and it play's it perfectly Hmmmm....

Thnx

---

### Post by codejunkie on 2005-07-05
you have to install mp3 dvd playback suppport in ubuntu because of copyright restrictions go to [www.ubuntuguide.org](www.ubuntuguide.org) and it should help you get it lined out.
Edit: i dont see it there anymore so you have to add these repositories to your /etc/apt/sources.list file by opening a terminal and typing 
```

sudo gedit /etc/apt/sources.list

```
and add these by deleting everything under the first line which should be your ubuntu cd or dvd leave that alone and paste this in there.
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```
save the file and type 
```

sudo apt-get update
```
then
```

sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins

```
once that finishes you should have dvd mp3 playback playback installed hope this helps.

---

### Post by Adrenal on 2005-07-05
Rtfm

---

### Post by Shinitenshi on 2005-07-05
w00000t worked perfectly thank you very much0 :) <3

---

### Post by nocturn on 2005-07-05
[QUOTE=Adrenal]Rtfm[/QUOTE]

rtfm is very rude.  If you do not want to answer a repeated question, just don't anwer.

---

### Post by Shinitenshi on 2005-07-06
[QUOTE=nocturn]rtfm is very rude.  If you do not want to answer a repeated question, just don't anwer.[/QUOTE]

>.< did i miss somthing? rtfm stands for?

---

### Post by codejunkie on 2005-07-07
[QUOTE=Shinitenshi]>.< did i miss somthing? rtfm stands for?[/QUOTE]
yes unfortantly someone here made a very stupid remark> rtfm and there post was deleted because we don't treat people like that here so just ignore people like that, the mods take care of them pretty quick, so welcome to the ubuntu community and feel free to ask anything you have a question about thats what this forums for.

---

### Post by Shinitenshi on 2005-07-07
Ah i see, lol its ok i should have read the manual tho >.<

---

### Post by M0ngr3l on 2005-07-19
[QUOTE=codejunkie]yes unfortantly someone here made a very stupid remark and there post was deleted because we don't treat people like that here so just ignore people like that, the mods take care of them pretty quick, so welcome to the ubuntu community and feel free to ask anything you have a question about thats what this forums for.[/QUOTE]


Codejunkie you're fantastic!

#1. Your help was to the point and accurate

#2. You swated away the forum troll

#3. You encouraged the new guys  (of which I'm one)


I've tried several different distros of linux, and Ubuntu is the one that felt most comfortable. But what really made me pull the trigger and make my XP partition just the one I play games on, is this FANTASTIC user community.

You are a shining light.. Keep up the good work.

---

### Post by HeyDriver on 2005-07-25
As a ubber noobie to the 'nix world I'd like to give my heartfelt thanks to codejunkie.  This was concise and accurate info that did the trick for me.  

It seems that with "sound card issues" that seem to plague the Hoary 5.04 release that this may be a good thread for "Tips and Tricks"?

It appears to me that an opportunity to learn coding from with in the "terminal" is at hand.

Thanks again...
HeyDriver

---

### Post by Jaymoid on 2005-08-02
[QUOTE=codejunkie]you have to install mp3 dvd playback suppport in ubuntu because of copyright restrictions go to [www.ubuntuguide.org](www.ubuntuguide.org) and it should help you get it lined out.
Edit: i dont see it there anymore so you have to add these repositories to your /etc/apt/sources.list file by opening a terminal and typing 
```

sudo gedit /etc/apt/sources.list

```
and add these by deleting everything under the first line which should be your ubuntu cd or dvd leave that alone and paste this in there.
```

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```
save the file and type 
```

sudo apt-get update
```
then
```

sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins

```
once that finishes you should have dvd mp3 playback playback installed hope this helps.[/QUOTE]
 Awesome, worked straight away, now chilling out to the beastie boys!

Props to codejunkie.

---

### Post by multipunto on 2005-08-21
[QUOTE=codejunkie]you have to install mp3 dvd playback suppport in ubuntu because of copyright restrictions go to [www.ubuntuguide.org](www.ubuntuguide.org) and it should help you get it lined out.
Edit: i dont see it there anymore so you have to add these repositories to your /etc/apt/sources.list file by opening a terminal and typing 
```

sudo gedit /etc/apt/sources.list

```
and add these by deleting everything under the first line which should be your ubuntu cd or dvd leave that alone and paste this in there.
[code]
## Uncomment the following two lines to fetch updated software from the network



Thanks a lot! it works perfectly! :)

---

### Post by 67735 on 2005-08-21
I tried this trick to the best of my ability and still no luck playing mp3.

Sigh.

I really want to like Linux, and I've loaded many different versions.  Ubuntu has a great feel and a very supportive community but I am always wondering why the Knoppix live cd can work playing movies and mp3 with no apparent problems across many different platforms, but Ubuntu has problems even with everything installed on a hard drive.

Please tell me the next version of Ubuntu will just plain work after it's installed for doing the most basic things computer owners take for granted.  I would gladly give up my (dirty word coming up) Windows box if I could surf the internet without having to install many different extra programs (Flash and Acrobat come to mind right off the top of my head), and be able to play DVDs and listen to my mp3s without fussing about in the heart of the operating system.

Linux seems to be a great idea whose time has come for the above-average computer user.  It seems to me that the Linux community needs to put out an EXTREMELY user friendly package which NEVER requires you go into the root terminal to get it to do the simple things you want it to do.

Realizing I'm missing the whole point of Linux, to be able to control every last detail of what's going on in the background, I'm still your target audience.  Make an operating system which anyone can use like the (dirty word) machine and Linux WILL take over the world.

---

### Post by sneax on 2005-08-22
[QUOTE=M0ngr3l]But what really made me pull the trigger and make my XP partition just the one I play games on, is this FANTASTIC user community.[/QUOTE]

I agree. My laptop's now 100% Ubuntu (WITH games through Cedega).

---

### Post by sneax on 2005-08-22
I'm just wondering, if I install all those repositries - it suggests me a lot of updates - is it safe to install them? Is it safe to install? Not realy security wise but I just don't want things to break!

---

### Post by Tiede on 2005-08-22
[QUOTE=67735]I tried this trick to the best of my ability and still no luck playing mp3.

Sigh.

I really want to like Linux, and I've loaded many different versions.  Ubuntu has a great feel and a very supportive community but I am always wondering why the Knoppix live cd can work playing movies and mp3 with no apparent problems across many different platforms, but Ubuntu has problems even with everything installed on a hard drive.

Please tell me the next version of Ubuntu will just plain work after it's installed for doing the most basic things computer owners take for granted.  I would gladly give up my (dirty word coming up) Windows box if I could surf the internet without having to install many different extra programs (Flash and Acrobat come to mind right off the top of my head), and be able to play DVDs and listen to my mp3s without fussing about in the heart of the operating system.

Linux seems to be a great idea whose time has come for the above-average computer user.  It seems to me that the Linux community needs to put out an EXTREMELY user friendly package which NEVER requires you go into the root terminal to get it to do the simple things you want it to do.

Realizing I'm missing the whole point of Linux, to be able to control every last detail of what's going on in the background, I'm still your target audience.  Make an operating system which anyone can use like the (dirty word) machine and Linux WILL take over the world.[/QUOTE]
 It is too sad that you cannot play mp3s after following this Howto, hopefully, we'll get it working.
[This little how to ](http://ubuntuguide.org/#codecs) taken from [ the Unofficial Ubuntu Starter Guide ](www.ubuntuguide.org[/url) might be albe to help you  out, you can also tty the other multimedia related How Tos in the page if needed.

Unfortunately, however, what you are asking in your post is impossible. Ubuntu being a free operating systeml, it cannot, out of the box, support the playback of proprietary formats like mp3, wma and the likes. What is a good idea however and one that someone could point to the Developpers would be to have a help page linked to the problem on the sound apps (when the apps crash because of this, the error message could contain a link to have more info on why the problem) and also in the Multimedia Section of the Help Program. But that is about all we in the free software community can do, I am afraid :-?

---

### Post by bonjun on 2005-08-26
thanks codejunkie.........

faaaaaaaaaaaannnnnnnntastic...:)

---

### Post by jared85 on 2005-08-30
[QUOTE=bonjun]thanks codejunkie.........

faaaaaaaaaaaannnnnnnntastic...:)[/QUOTE]
 I did all this.
I am using the exact source.list (with resps) from the ubuntuguide.org (64 edition).

I did sudo apt-get update
then sudo apt-get install gstream0.8-plugins

then it does
reading package lists... done
building dep. tree... done
E: couldn't find package gstream0.8-plugins.

I dont know what the hell is going on here. I have been search through the forums for the past 45 mins but nothing sheds any insights.

Any help would be appreciated. Thanks

---

### Post by jared85 on 2005-08-30
[QUOTE=jared85]I did all this.
I am using the exact source.list (with resps) from the ubuntuguide.org (64 edition).

I did sudo apt-get update
then sudo apt-get install gstream0.8-plugins

then it does
reading package lists... done
building dep. tree... done
E: couldn't find package gstream0.8-plugins.

I dont know what the hell is going on here. I have been search through the forums for the past 45 mins but nothing sheds any insights.

Any help would be appreciated. Thanks[/QUOTE]
 very strange, i tried it ove rand over with no success.

then I was looking around un kubuntu and read to use this first

sudo apt-get install akode-mpeg

it installed some stuff.. THEN i was able to do 

sudo apt-get install gstream0.8-plugins

strange i never read anyone else having to do this, oh well maybe this will help some other people :D

cheers

---

### Post by Tiede on 2005-09-06
I think the right command is
```
apt-get install gstreamer0.8-plugins
```
You forgot the -er in gstreamer ;)

---

### Post by 101010 on 2005-09-12
I have tried exactly what is shown here (64 edition) and I keep on getting

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


I get this also for the libdvdcss2.

Any clue on how to get this to work?


101010

---

### Post by codejunkie on 2005-09-12
[QUOTE=101010]I have tried exactly what is shown here (64 edition) and I keep on getting

Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


I get this also for the libdvdcss2.

Any clue on how to get this to work?


101010[/QUOTE]
i don't use the 64 bit distro but the w32codecs package is in the backports repo so this might help, you have to add extra repos to your /etc/apt/sources.list you can do that by following this guide here [http://amd64.ubuntuguide.org/#extrarepositories](http://amd64.ubuntuguide.org/#extrarepositories) hope this helps.

---

### Post by oprogue on 2005-09-18
ok ... this is the error I'm getting:


tank@ubuntu:~$ sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs


any suggestions?

Thanks,

op.

---

### Post by codejunkie on 2005-09-18
[QUOTE=oprogue]ok ... this is the error I'm getting:


tank@ubuntu:~$ sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs


any suggestions?

Thanks,

op.[/QUOTE]
you need to add the extra repositories to your /etc/apt/sources.list file this should help you do that [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) then run 
```
sudo apt-get update
```
then
```

sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins

```

---

### Post by chess007 on 2005-10-01
sudo apt-get install w32codecs won't work for me. :P It says,"

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not avaliable, but isreferred to by another package. This may mean that the package is missing, has been obsoleted, or is only avaliable from another source.
E: Package w32codecs has no installation candidate


How can I get this to install? I have updated the apt sources list according to the ubuntu starter guide.

---

### Post by AgenT on 2005-10-02
[quote=chess007]sudo apt-get install w32codecs won't work for me. :P It says,"

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not avaliable, but isreferred to by another package. This may mean that the package is missing, has been obsoleted, or is only avaliable from another source.
E: Package w32codecs has no installation candidate


How can I get this to install? I have updated the apt sources list according to the ubuntu starter guide.[/quote] 
A lot has changed in the last week or so in the backports project. One of which is the deletion of certain packages due ot legal concerns. One of those packages is w32codecs. Also, the guide is outdated as of today (or yesterday) because they have deleted the mirror servers (actually, they are still up but empty). See the Backports forum for more details.

---

### Post by iwan13 on 2007-08-01
ok.. i have no idea if this is old guide .. nor how to lay mp3... but this guide is the most understandable .. but ... it dosent work for me :(
after the step  update i get a whole load of not found(404) thignies.. k 
now i have no idea to play mp3 .. i tried installing codecs but ... one by one system isnt prooving much of a fruiful work... and at one point one of required packs had broke during install and had caused even more head aches .. i realy like ubuntu and i hate windows 

can someone direct me to a guide SIMPLE as thins one .. i am an UTTER NOOB to ubuntu :( so bear with me ... and seeing how this community is great i want to be a part of it :D 
in words of a noob talk.. HALP MEH PLZ! :KS

---

### Post by Shib on 2007-08-01
quickest way to play mp3's?

apt-get install vlc

although, that means that you can just use vlc to play your mp3s... whereas the technique of getting the actual w32codecs package will give you the ability to play mp3's with any program.

here's the location of a .deb with the codecs:

[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.1_i386.deb)

then do a "sudo dpkg --install w32codecs*" in the directory where you downloaded that (or you could click on it... not sure if that'll work... I don't really "click" things too much :P)

anywho, that should work one way or the other :)

---

### Post by iwan13 on 2007-08-03
i phail ubuntu :( 
> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libdc1394-13 but it is not installable
       Depends: libdvdnav4 (>= 0.1.9) but it is not installable
       Depends: libdvdread3 but it is not installable
       Depends: libgsm1 (>= 1.0.10) but it is not installable
       Depends: libid3tag0 (>= 0.15.1b) but it is not installable
       Depends: libmad0 (>= 0.15.1b) but it is not installable
       Depends: libmpcdec3 but it is not installable
E: Broken packages

the heck is wrong with me ? i cant even set up ubuntu :((((

k.. im downloading the file .. hoping for the best >.<
99...100% DONE!
IT'S INSTALIIING~~~~DOONE~! ... is that it ???
HHAHAHAHHAHHA THANK YOU!!! :DDDDDD

---

### Post by strabes on 2007-08-03
If you have feisty all you have to do is ```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by iwan13 on 2007-08-09
sorry for late response ... having fun with ubuntu :) 
dapper is me ubuntu :)

---

