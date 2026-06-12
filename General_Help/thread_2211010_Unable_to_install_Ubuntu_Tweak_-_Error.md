---
title: "Unable to install Ubuntu Tweak - Error"
date: 2014-03-13
forum: General Help
---

### Post by immaculance on 2014-03-13
Hello. I am attempting to install Ubuntu Tweak 0.8.6 via dpkg in my terminal. I'm receiving an error after it is attempting to process triggers for hicolor-icon-theme and am really clueless as to what could be going wrong here.

I tried deleting the .deb file and re-downloading it, but that resulted in the same issue for me.  Any clues, guys? Thanks!

[ATTACH=CONFIG]251113[/ATTACH]

---

### Post by immaculance on 2014-03-13
OK, I'm clearly a dummy... Looks like I need python.... I tried researching how to get this package, but I'm a little lost. Can someone please help me? Thanks!

---

### Post by monkeybrain20122 on 2014-03-13
Why don't you just install form ppa? [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

If you have occasion to install .debs, gdebi is handy
```
sudo apt-get install gedebi
```
dpkg doesn't pull in dependencies (right click with gdebi does)

---

### Post by immaculance on 2014-03-13
Thank-you, Monkeybrain.

OK, I got the PPA installed, and I believe it's installed now? Maybe? Uh, how do I get to the application now? I don't know where these things get installed and I don't know what command to put in to add the app to my menu. Yes, I'm a big Linux noob, so appreciate acticipating my very noobiness with this. Just would like to understand where the app goes and how I access / execute the application now. Thanks!

[ATTACH=CONFIG]251115[/ATTACH]

---

### Post by immaculance on 2014-03-13
I figured out how to launch the application by hitting ALT+F2 and entering 'ubuntu-tweak'. I pinned it to my Docky and I also added it to my application menu with just entering the command 'ubuntu-tweak', so that was easy enough.  I have a lot to learn about this OS.

---

