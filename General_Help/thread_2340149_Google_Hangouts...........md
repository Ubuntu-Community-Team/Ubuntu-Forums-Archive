---
title: "Google Hangouts.........."
date: 2016-10-16
forum: General Help
---

### Post by old_dog on 2016-10-16
Have been setting up "google hangouts" to talk to my son and family, don't know if it is relevant I'm in the UK and he is in Oz.
I'm running on ubuntu 14.04 and firefox with a "Creative camera and microphone".
My son is running on an Apple.
I can see and hear my son no problem
He can see me OK but no sound!
Both of of us, when we test locally have both video and sound. 
My test was to a Windows based laptop.
Is Ubuntu to Apple the problem as I know Apple has a reputation for being idiosyncratic  

Any bright ideas?????

---

### Post by howefield on 2016-10-16
What browser is your son using, Safari ?

Just wondering if Chrome would be better for using a google product.

Also, are you stuck on hangouts, there are several other video calling options.

---

### Post by Geoffrey_Arndt on 2016-10-16
This looks promising . . . worth a shot . . . and is Open Source too:

[https://wire.com/](https://wire.com/)

---

### Post by oygle on 2016-11-03
Installed Google talk this morning from [http://www.ubuntuupdates.org/ppa/google_talk_plugin](http://www.ubuntuupdates.org/ppa/google_talk_plugin)

Noticed these warnings after installing from Konsole

> 
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_AU) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en_AU) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/google-talkplugin.list:3 and /etc/apt/sources.list.d/google.list:1


> 
$ **cat   /etc/apt/sources.list.d/google.list**
deb [arch=amd64] [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

**cat   /etc/apt/sources.list.d/google-talkplugin.list**
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

---

