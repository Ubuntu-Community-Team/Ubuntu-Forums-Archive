---
title: "MPlayer problem in Firefox (need more help)"
date: 2005-05-15
forum: General Help
---

### Post by Ramon Lasa on 2005-05-15
To anyone that replied to my original thread stating my problem with MPlayer and Firefox:

How do I disable the sound server startup fo my MPlayer problem in Firefox?
How do I make sure MPlayer is set up correctly to work with Firefox?

I am a new oerson to Linux so be as specific in the instructions as you can.  Much of this is very difficult to figure out for a new person.

Thanks in advance for any help you can give.

Ramon

---

### Post by bruizer on 2005-05-15
Look in /usr/lib/mozilla-firefox/plugins for the link called mplayerplug-in.so This is the plug-in link for MPlayer within Firefox. Also check that Firefox picked it up by going into Firefox, and checking in Edit - Preferences, Downloads section, and click the plug-ins button. You should see a pile of media extensions.

If you don't see this stuff there, check to ensure that these are installed (make sure you have updated with extra repositories):
 
gstreamer0.8-plugins
w32codecs
liblame0

Once you have verified that these are installed, try running:
1. sudo apt-get -t hoary install mplayer-fonts
2. sudo apt-get -t hoary install mozilla-mplayer (Installs and updates the link and Firefox plug-in)

Once you've done this you will need to restart Firefox to see the changes. Firefox on initialization should see the link, and load the plug-ins.

I hope this helps!

---

### Post by ludi on 2005-05-15
[QUOTE=Ramon Lasa]To anyone that replied to my original thread stating my problem with MPlayer and Firefox:

How do I disable the sound server startup fo my MPlayer problem in Firefox?
How do I make sure MPlayer is set up correctly to work with Firefox?

I am a new oerson to Linux so be as specific in the instructions as you can.  Much of this is very difficult to figure out for a new person.

Thanks in advance for any help you can give.

Ramon[/QUOTE]
 " How do I disable the sound server startup fo my MPlayer problem in Firefox?"
You don't need do it. What is exacly your problem?
You can easly change the default sound system to ESD on mplayer configuration (gnome side, arts kde side).
Follow the mini how-to of Bruizer and you won't get any problems.

---

### Post by ludi on 2005-05-15
[QUOTE=Ramon Lasa]To anyone that replied to my original thread stating my problem with MPlayer and Firefox:

How do I disable the sound server startup fo my MPlayer problem in Firefox?
How do I make sure MPlayer is set up correctly to work with Firefox?

I am a new oerson to Linux so be as specific in the instructions as you can.  Much of this is very difficult to figure out for a new person.

Thanks in advance for any help you can give.

Ramon[/QUOTE]
 " How do I disable the sound server startup fo my MPlayer problem in Firefox?"
You don't need do it. What is exactly your problem?
You can easily change the default sound system to ESD on mplayer configuration (gnome side, arts kde side).
Follow the mini how-to of Bruizer and you won't get any problems.

---

