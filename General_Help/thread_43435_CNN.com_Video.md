---
title: "CNN.com Video ?"
date: 2005-06-21
forum: General Help
---

### Post by bored2k on 2005-06-21
[http://www.cnn.com/video/](http://www.cnn.com/video/)

It's asking for Windows Media Player :/. 
I'm sure someone could figure out a way to play these videos just like you all play Launch and Yahoo videos :D.

Anyone ?

---

### Post by clb137 on 2005-06-22
Wish i could find a way as well, its the only little irritating thing about surfing on the web, and not being able to view all the different types of vidoes media on the various sites,     would also appreciated some help here


thanks

clinton

---

### Post by doans on 2005-06-22
[QUOTE=clb137]Wish i could find a way as well, its the only little irritating thing about surfing on the web, and not being able to view all the different types of vidoes media on the various sites,     would also appreciated some help here


thanks

clinton[/QUOTE]
 Works for me using mplayerplug-in.  Have you installed Mplayer and mozilla-mplayer from synaptic?

---

### Post by clb137 on 2005-06-22
[QUOTE=doans]Works for me using mplayerplug-in.  Have you installed Mplayer and mozilla-mplayer from synaptic?[/QUOTE]


do not seem to be able to get Mplayer and its plug in working correctly, it starts then  no movie so i just download and play in Xine

clinton

---

### Post by doans on 2005-06-22
[QUOTE=clb137]do not seem to be able to get Mplayer and its plug in working correctly, it starts then  no movie so i just download and play in Xine

clinton[/QUOTE]
 Yeah, you have to edit the mplayer configuration file and change the video out (vo) and audio out (ao) preferences.  Change vo to xv and ao to esd.  Then uncomment (delete the # sign) the formats that you wish to play with mplayerplug-in.  enable-wm,enable-qt,etc.

The config file is located in /etc/mplayerplug-in.conf. Just sudo gedit /etc/mplayerplug-in.conf That should get the mplayerplug-in working correctly and then you can easily watch the videos in the browser.  Hope this helps.

Edit: Here is a link to all the steps to get mplayerplug-in working properly.  [Ubuntuguide](http://www.ubuntuguide.org/#mplayer)

---

### Post by az on 2005-06-22
Does this work for you?

[https://wiki.ubuntu.com/forum/software/FirefoxStreamingVideo](https://wiki.ubuntu.com/forum/software/FirefoxStreamingVideo)

---

### Post by sunscape on 2005-06-22
[www.ubuntuguide.org](www.ubuntuguide.org)

easy instructions to view anything

find the mplayer section

---

### Post by gil-galad on 2005-06-22
I just tried it and it worked great with mozilla-mplayer.  It says you need media player 9, but you can just bypass the warning messege by clicking "continue to video".

---

### Post by clb137 on 2005-06-23
[QUOTE=doans]Yeah, you have to edit the mplayer configuration file and change the video out (vo) and audio out (ao) preferences.  Change vo to xv and ao to esd.  Then uncomment (delete the # sign) the formats that you wish to play with mplayerplug-in.  enable-wm,enable-qt,etc.

The config file is located in /etc/mplayerplug-in.conf. Just sudo gedit /etc/mplayerplug-in.conf That should get the mplayerplug-in working correctly and then you can easily watch the videos in the browser.  Hope this helps.

Edit: Here is a link to all the steps to get mplayerplug-in working properly.  [Ubuntuguide](http://www.ubuntuguide.org/#mplayer)[/QUOTE]
#

Hi,

Sorry to tell you that it does not work at all, it say downloading then nothing it just hangs.  I cannot even see mpeg files with it, yet whne i uninstall it xine play them no problem even .wmv files  i do not unferstand it,  i have NEVER been able to get mplayet to play anthing in Ubuntu


thanks any way

clinton

---

### Post by doans on 2005-06-24
Strange, I just followed the UbuntuGuide mplayerplugin section and I was streaming videos in 5minutes time. I wish I could help you.:sad:

---

### Post by wadesmart on 2005-06-24
06242005 0856 GMT-5

I just read these posts and tried everything stated here. When I try to view any online video the MPlayer screen pops up, a blank Error Screen appears, disappears and then in the bottom right hand corner, the outline of what I believe to be the main MPlayer application appears and stays onscreen. You cant turn it off. You have to kill the process. And yes, I did do what the Unofficial Guide said. Are there any other suggestions?

Wade

---

### Post by skoal on 2005-06-24
[QUOTE=gil-galad]I just tried it and it worked great with mozilla-mplayer.  It says you need media player 9, but you can just bypass the warning messege by clicking "continue to video".[/QUOTE]
Yeppers. Same here.  All stock mplayer/w32 codec installed, running on a P4.  Just bypass the warning and off you go.  weeeeeeeee....

\\//_

---

### Post by crashtest on 2005-06-24
[QUOTE=skoal]Yeppers. Same here.  All stock mplayer/w32 codec installed, running on a P4.  Just bypass the warning and off you go.  weeeeeeeee....

\\//_[/QUOTE]

No luck here at all.  Followed all instructions that were posted, then double checked everything to make sure.  The movie playback appears to start, then the player screen turns black and nothing else happens.

---

### Post by crashtest on 2005-06-24
[QUOTE=azz]Does this work for you?

[https://wiki.ubuntu.com/forum/software/FirefoxStreamingVideo](https://wiki.ubuntu.com/forum/software/FirefoxStreamingVideo)[/QUOTE]

Here's something new:  after installing the above plugin, I can configure Firefox to play the CNN videos with xine.  When I try using mplayer it crashes.

---

