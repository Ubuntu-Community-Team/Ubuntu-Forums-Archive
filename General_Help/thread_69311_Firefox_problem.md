---
title: "Firefox problem"
date: 2005-09-26
forum: General Help
---

### Post by Christy on 2005-09-26
I had the little red circle come up in the top right of the screen to show that I had new upgrades available about an hour ago. I clicked on it and went to download and install the 5 upgrades (2 of which were Mozilla Firefox and the gnome-support Firefox one) rather than going into the terminal and manually installing the upgrades. Well the 2 Firefox upgrades didn't go through all the way, so I went into the terminal and did sudo apt-get upgrade firefox and tried that and it says that I have 3 things that aren't fully installed (I don't know specifically what they are though) with some kind of message about not being able to overwrite something already in the Firefox folder and now Firefox is not functioning. I tried multiple times to complete the upgrade the same way I just mentioned and restarted and tried again just in case if that would do anything, but I can't open Firefox now and it won't overwrite whatever files those are that need to be overwritten. Is there any way to either undo the upgrade I attempted or a way to get it to complete? I'm pretty new to Ubuntu and Linux so I'm not sure about all the tricks you can use for this stuff. Thanks.

Christy

(I have my laptop set up with a boot menu for Windows XP and Linux so I had to go on Windows to post this since I couldn't get on Firefox on Linux and I'm not at home so I can't get on my desktop.)

---

### Post by Zelut on 2005-09-26
I have the same issue on my desktop.  I have 2 updates that wont finish.  They are the firefox-gnome-common (I think) and another firefox update.  Neither will overwrite the existing and I cannot load firefox in the meantime.

Tips on a downgrade or forced upgrade would be greatly appreciated.

---

### Post by ouphe on 2005-09-26
Same here....

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Surfing the web now with wine+internet explorer.... oooh... the irony

---

### Post by Christy on 2005-09-26
I actually just found the same problem on the 2nd page of this forum so I'm going to try the solutions listed there. I guess I should've looked there first.

---

### Post by Christy on 2005-09-26
[quote=ouphe]Same here....

E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb: trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support

Surfing the web now with wine+internet explorer.... oooh... the irony[/quote]


Thanks for posting the errors though. I had already switched to XP to get on here without writing them down first.

---

### Post by arunsub on 2005-09-26
Check this
[http://www.ubuntuforums.org/showthread.php?p=367285#post367285](http://www.ubuntuforums.org/showthread.php?p=367285#post367285)

---

### Post by Christy on 2005-09-26
I just tried that now. Now it's halfway gone, but not completely I don't think. I tried sudo apt-get install mozilla-firefox and it asked for my Ubuntu cd which I've had with me EVERY day except for today because I let someone borrow it earlier so they could try it out. I hope they get it back to me tomorrow. Thanks for such quick replies guys. It's greatly appreciated.

---

### Post by arunsub on 2005-09-26
sudo apt-get upgrade didn't work for me, so i had to do sudo apt-get -f install. Firefox didn't start after that. I then opened a termilnal window, found the firefox-bin process id and killed it. I then restarted firefox and it worked.

---

### Post by Christy on 2005-09-26
Yeah, that was the last step I tried when I went through the steps you showed, but it didn't work for me. I had some sort of error or another after each step it seemed. I'll just try the CD thing when I get it back (hopefully tomorrow).

---

### Post by wadesmart on 2005-09-26
09262005 2013 GMT-5

You might read this thread:
[http://ubuntuforums.org/showthread.php?p=372101#post372101](http://ubuntuforums.org/showthread.php?p=372101#post372101)

I had horrible problems getting Forefox fixed but now its finally working. 

Wade

---

### Post by oxalá on 2005-09-26
cd /var/cache/apt/archives 
sudo dpkg -i --force-all mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
sudo dpkg -i --force-all mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
sudo apt-get install 

after that, i was all good.

---

### Post by Christy on 2005-09-27
[quote=wadesmart]09262005 2013 GMT-5

You might read this thread:
[http://ubuntuforums.org/showthread.php?p=372101#post372101]("http://ubuntuforums.org/showthread.php?p=372101#post372101")

I had horrible problems getting Forefox fixed but now its finally working. 

Wade[/quote]
I just did what beerorkid recommended in the original post in that thread and it worked for me. I'm actually still stuck in limbo if I go to the terminal and type that stuff in again. Just all sorts of errors across the board. But I just tried opening Firefox a few minutes ago after doing this and now it's working, so that's all I care about for the moment. I'll worry about other issues later. Thanks everyone for the help. I can't tell you how much I appreciate it because I'm not at a point where I can figure this out on my own  yet (I'm still pretty new to it. I've been using it since June but only general usage... no technical type of stuff really).

---

