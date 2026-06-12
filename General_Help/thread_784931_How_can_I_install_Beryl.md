---
title: "How can I install Beryl?"
date: 2008-05-06
forum: General Help
---

### Post by ircmaster on 2008-05-06
Hey guys, I was trying to install the cool Beryl effects that can be seen in [this]("http://youtube.com/watch?v=xC5uEe5OzNQ") video. I'm using Ubuntu 8.04. 

I'm new to this stuff so go easy on me with all the coding stuff :D. I'll try my best to understand.

---

### Post by Go_Bucks on 2008-05-06
Beryl isn't necessary. Compiz replaces it and is built in to Ubuntu now. Go to System>Preferences>Appearance and select level of visual effects on the visual effects tab. To access settings for compiz, install compiz-config settings-manager from synaptic. It will show up as "Advanced Desktop Effects Settings" under System>Preferences.

---

### Post by ircmaster on 2008-05-06
Ah, yea I know about the visual stuff but there were some other things in there that I liked but haven't seen in the Ubuntu I have. Like the docklets and stuff, or the menu that shows up and dissapears when you right-click. Is that just extra stuff I can download? And if it is, where can I download it from and how do I install it?

---

### Post by Go_Bucks on 2008-05-06
Compiz uses desklets or something like that. I am not sure about the other thing. All I know is that Beryl is no longer supported. That project was merged with Compiz and most of the features were ported over.

---

### Post by ircmaster on 2008-05-06
Another question...how can I make the cube work? I tried alt+ctrl+left click but it doesn't show.

---

### Post by piratesmack on 2008-05-06
> **ircmaster said:**
> Another question...how can I make the cube work? I tried alt+ctrl+left click but it doesn't show.

Did you install compizconfig-settings-manager?

```

sudo apt-get install compizconfig-settings-manager

```

You can enable the cube with that

---

### Post by ircmaster on 2008-05-07
I installed the manager and I enabled the cube but it still doesn't work O_O

---

### Post by Go_Bucks on 2008-05-07
Did you enable "rotate cube" as well? Without that, you won't get the effect you are looking for.

After that, press <ctrl><alt> and then the left or right arrow keys on the keyboard.

---

### Post by hencke on 2008-05-07
> **ircmaster said:**
> Ah, yea I know about the visual stuff but there were some other things in there that I liked but haven't seen in the Ubuntu I have. Like the docklets and stuff, or the menu that shows up and dissapears when you right-click. Is that just extra stuff I can download? And if it is, where can I download it from and how do I install it?

I think the dock in the video is kiba-dock:

[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

But AWN might be easier to install. It's in the repositories (1). Open System>Administration>Synaptic Package Manager and search for avant and install the avant-window-manager.

For small desktop applications (again easy-installation) search for gdesklets or screenlets in synaptic. You might want to google a bit first to see if they're what you want.


(1) You might have to enable [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner in the "Third-Party Software" tab in System>Administration>Software Sources (at least check that you have the restricted and multiverse repositories enabled in the "Ubuntu Software" tab)

Possibly helpful links:

Most screenshots here have AWN as the dock:

[LIST]
[*][http://www.screenlets.org/index.php/Screenshots](http://www.screenlets.org/index.php/Screenshots)
[/LIST]

If you want multiple-icon-zooming of your dock icons (not provided by AWN?), another option for your dock could be Cairo-Dock:

[LIST]
[*][http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/](http://tombuntu.com/index.php/2008/05/01/how-to-install-cairo-dock/)
[/LIST]

---

### Post by mano cazalet on 2008-05-07
Maybe you missed one step to the rotate cube to work:

in compiz config settings manager there is a tab "Desktop size". There you have to change the horizontal virtual size to 4 and then I hope your cube will rotate.

---

