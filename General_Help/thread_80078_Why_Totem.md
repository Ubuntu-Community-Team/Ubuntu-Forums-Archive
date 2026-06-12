---
title: "Why Totem?"
date: 2005-10-21
forum: General Help
---

### Post by avc on 2005-10-21
What good is Totem? What is it supposed to play? I can't seem to use it for anything. Xine and mplayer with proper codecs work for most of the videos I find on the internet. Perhaps Totem's inclusion in Ubuntu as the default media player has something to do with open source purity? Someone enlighten me.

---

### Post by shakin on 2005-10-21
[QUOTE=avc]What good is Totem? What is it supposed to play? I can't seem to use it for anything. Xine and mplayer with proper codecs work for most of the videos I find on the internet. Perhaps Totem's inclusion in Ubuntu as the default media player has something to do with open source purity? Someone enlighten me.[/QUOTE]

Totem is Gnome's official media player, so that's why it's included in Ubuntu.

---

### Post by Stormy Eyes on 2005-10-21
[QUOTE=shakin]Totem is Gnome's official media player, so that's why it's included in Ubuntu.[/QUOTE]

Epiphany is GNOME's official web browser, but Ubuntu uses Firefox by default. Making an app an official part of GNOME is no guarantee that it is a good app. As evidence I offer Totem, and the Metacity window mangler.

---

### Post by Kyral on 2005-10-21
Install totem-xine to allow totem to use Xine as a backend, so it can do most of what Xine can

---

### Post by avc on 2005-10-21
I'm just curious what benefits Totem has over the other common media players.

---

### Post by tanari on 2005-10-21
I like totem. It's nice, I like it's interface more than skinable MPlayer. Very clear and simple fullscreen mode, supports drag 'n' drop from nautilus.

Use MPlayer if you don't like it. But try to install totem-xine first! I don't have any troubles with playing movies.

---

### Post by Kyral on 2005-10-21
[quote=avc]I'm just curious what benefits Totem has over the other common media players.[/quote]

Like many things in Linux, its all a matter of personal preference. Being such, Flamewars easily errupt (Search Wikipedia for the "Editor Wars" to see what I mean)

---

### Post by Master Shake on 2005-10-21
[http://ubuntuforums.org/showthread.php?t=78622](http://ubuntuforums.org/showthread.php?t=78622)

In short, I got the DVD codecs installed, and the xine, and I can play DVD's with minimal problems.

Also, you can do a screen capture wit htotem...  Something I've never been able to do with any media player in Windows.  My avatar was taken from an Aqua Teen Hunger Force DVD last night.

---

### Post by clparker on 2005-10-21
Imagine Totem Kinda being like the nipples on a male dog...completly useless, they dont really dont do anything, they're there as an artifact of some genetic trait, no longer needed, but remains for a reason only god will know.

Make Sense?

---

### Post by objorkum on 2005-10-21
Totem is a great player, but it's just a front-end, to gstreamer or xine-lib. Don't blame Totem itself.

totem-gstreamer is the default, and you have to install the gstreamer-plugins to watch most videos. However, totem-xine is just easier to deal with.

Install the "totem-xine" package, and then download the essential codec pack from MPlayer's homepage and put the codecs  in /usr/lib/win32, and voila, you can play most videos.

---

### Post by aysiu on 2005-10-21
Totem may not work for you, but it works for me. I think it's included not because it's the best but because it's Gnome's movie player--just as Rhythmbox isn't the best, but they're not going to make AmaroK the default music player in Gnome. You can install something else yourself... that's the beauty of apt-get/Synaptic.

---

### Post by avc on 2005-10-22
Didn't mean on starting a flame war here, just wanted some ideas of how to best utilize the default software on gnome. Thanks for the xine-totem tip. I'm gonna try it. ;)

---

### Post by aysiu on 2005-10-22
[QUOTE=avc]Didn't mean on starting a flame war here, just wanted some ideas of how to best utilize the default software on gnome. Thanks for the xine-totem tip. I'm gonna try it. ;)[/QUOTE] You may have better luck installing *totem-xine* than *xine-totem*.

---

