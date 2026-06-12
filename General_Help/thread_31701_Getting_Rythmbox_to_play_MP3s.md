---
title: "Getting Rythmbox to play MP3s"
date: 2005-05-04
forum: General Help
---

### Post by triskele on 2005-05-04
So I've noticed that Rythmbox lacks the plug-in to play MP3 files by default. I found a post that said I should install libmad and the appropriate -dev and I did that, but it still won't accept MP3s. What do I have to do to make this work. I'd like to give this music management software a shot before going and installing XMMS. What do I have to do to make this thing work? Thanks

---

### Post by markr on 2005-05-04
I think you need to install w32codec and gstreamer0.8 as well.

Mark.

---

### Post by triskele on 2005-05-04
From what I can tell from the Package Manager, gstreamer is installed and I see nothing regarding w32codec. I know what it is I just don't know where it is.

While I'm on the topic... how do I get Totem Movie Player to play AVI files?

---

### Post by Bob D. on 2005-05-04
[QUOTE=triskele]From what I can tell from the Package Manager, gstreamer is installed and I see nothing regarding w32codec. I know what it is I just don't know where it is.

While I'm on the topic... how do I get Totem Movie Player to play AVI files?[/QUOTE]
To get Rhythmbox to play MP3 and other file types such as Flac, just install the 'gstreamer0.8-plugins' package. This is a meta package that will install all the Gstreamer plugins.

Regarding Totem, most people have better luck uninstalling the default Totem-gstreamer and installing Totem-xine (looks the same, just a different engine underneath). The W32codecs will allow you to play AVI files.

Note, that to obtain the gstreamer-plugnis and Totem-xine you will need the Ubuntu repository activated (it isn't a default). For the W32codecs the best place is to add the repos for the Backports project. Info on adding repositories is here: [http://ubuntuguide.org/temp/#extrarepositories]("http://ubuntuguide.org/temp/#extrarepositories")

Bob

---

### Post by triskele on 2005-05-04
OK, I got Rythmbox working, but I'd rather use XMMS. Now how exactly do I get Totem to play AVIs. Right now it just plays a graphic visualization of the audio. You mentioned totem-xine  but I don't see that anywhere in the package manager or add/remove programs dialogues. Thanks.

---

### Post by Bob D. on 2005-05-04
[QUOTE=triskele]OK, I got Rythmbox working, but I'd rather use XMMS. Now how exactly do I get Totem to play AVIs. Right now it just plays a graphic visualization of the audio. You mentioned totem-xine but I don't see that anywhere in the package manager or add/remove programs dialogues. Thanks.[/QUOTE]
 In my last post, I provided a link on how to add extra software repositories so you can access them. Only add the _Ubuntu Universe, Multiverse,_

deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse AND

 _Backports_ repositories

deb  [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-backports main universe multiverse restricted

deb  [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-extras main universe multiverse restricted

for right now. You can get into trouble if you click the 'Mark All Upgrades' button with the Marillat repositories added.

Follow those instructions first, then lanuch Synaptic from System drop down menu (System>Administration>Synaptic Package Manager). In Synaptic, click on the Reload button in the menu. This will refresh your package list and add info from your newly added repositories.

Now if you search in Synaptic you will be able to download Totem-xine (search on 'Totem') and the W32codecs. The W32codecs package will allow you to play AVI files in Totem.

I gotta run but I'll check back on this thread later this afternoon.

Bob

---

### Post by triskele on 2005-05-04
Thanks... I had all the right repositories, I guess I just had to hit reload or whatever it is. Now if I could only get my palm to connect I'd be set. If yo could look at my post in the hardware section I'd really appreciate it.

---

### Post by DutchLau on 2005-05-04
Hello triskele!

There are a number of things you can do. 

First add the extra repositories to your cache like this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Now get your codecs (& DVD playback capability if you want) like this:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

You can get many better movie players than Totem (Which usually doesn't work from what I see around here) such as Mplayer ([http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer) - remember to have firefox off during the install), VLC (sudo apt-get install vlc), Gxine (sudo apt-get install gxine), Xine-UI ([http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)) and a bunch of others. I like Gxine myself, but don't get it just because I do. 

Good luck,

DutchLau

EDIT: You can also get XMMS like this: [http://ubuntuguide.org/#xmms](http://ubuntuguide.org/#xmms)

---

### Post by triskele on 2005-05-04
I got XMMS and Totem working, but I'll work on mplayer later so I can use the firefox plugin. Thanks.

---

