---
title: "[SOLVED] flash issues in Firefox only"
date: 2016-05-14
forum: General Help
---

### Post by argonvegell on 2016-05-14
I have Flash Player installed via the adobe-flashplugin, which installs the regular adobeflashplugin and the pepperflashplugin.

On Firefox, when I tried to play one of the flash games I tend to play, the sounds of the game is heard, but there's no flash animation, the box where the flash animation is suppose to appear, appears invisible, and also, when I went to [www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/"), the area where it's suppose to tell you what version of Flash is running is invisible.

However, when I tried it on Chromium, Flash player works, my game works, animation and audio, the Adobe Flash about page tells me which version of Flash is being used by Chromium.

So the problems seems to be with Firefox. I've tried refreshing Firefox and I've tried reinstalling adobe-flashplugin, but still, Flash doesn't want to work on Firefox.

Please see attached image.

[ATTACH=CONFIG]269036[/ATTACH]

---

### Post by ajgreeny on 2016-05-14
Are you using 16.04 as I am also unable to get the version 21 of flash to work in FF using 16.04 using the freshplayerplugin package which has worked in previous Ubuntu versions?

If you remove the **browser-freshplayer-plugin-pepperflash** package which I assume you must have installed, you may find that flash will work but it will be version 11, not 21.

---

### Post by argonvegell on 2016-05-14
Thanks for the reply, I'm using Xubuntu 14.04, I'm planning on upgrading to 16.04 next year.

I'm using Fresh Player to use Pepper Flash on FIrefox, but Flash doesn't function correctly on Firefox, it shows a blank box where the Flash animation is supposed to be, but Flash works fine on Chromium.

I've tried to remove Fresh Player to see if it changes anything, but all I got was the same result as seen on the attached picture.

---

### Post by ajgreeny on 2016-05-15
Very strange.

I have the following packages installed and get flash version 21 working fine in both chromium and firefox:-
adobe-flashplugin
adobe-flash-properties-gtk
browser-plugin-freshplayer-pepperflash
pepperflashplugin-nonfree
freshplayerplugin (this is now a dummy package)

See if you have all those; if not remove any that are not listed above and install any missing from the list.

I am still having problems in 16.04 but will keep trying to get flash version 21 to work in that as well.

---

### Post by argonvegell on 2016-05-15
I've uninstalled and reinstalled Firefox via Synaptic Package Manager, I've even deleted the contents of '.mozilla' on my home folder, and I didn't install any addons, but still the problem remains, Flash version 11.2.202.621 and 21.0.0.242 doesn't function properly on Firefox, it leaves a blank box where the Flash animation is supposed to be, however the sounds are working.

Looks like I'm stuck with Chromium if I want to run my Flash games.

---

### Post by argonvegell on 2016-05-16
I was able to fix the issue by doing this;

```
sudo apt-get purge adobe-flashplugin
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper*flash*so
rm -f ~/.mozilla/plugins/*flash*so
```

Then I reinstalled Adobe Flash Player;

```
sudo apt-get update
sudo apt-get install adobe-flashplugin
```

So now, the About Adobe Flash Player page shows this message, "You have version 21,0,0,242 installed".

Not sure why this happened though? Any ideas on what happened?

---

### Post by ajgreeny on 2016-05-16
Do you still have the **browser-plugin-freshplayer-pepperflash** package installed?

That is normally what is needed in 14.04 to get flash version 21.0.0.242 to run properly.  I can only think that with all the attempts you have made to get this working properly you have somehow managed to get a lot of conflicting plugin-modules (those *name*.so files) scattered about the filesystem, and they were confusing things.

If you get around to upgrading to 16.04 soon you may, however, find it is not so easy to get FF to run flash 21; this is the problem I am still having.

Please mark as SOLVED from the Thread Tools menu up top.

---

### Post by argonvegell on 2016-05-16
Yes, I have browser-plugin-freshplayer-pepperflash installed via the webupd8 PPA, because AFAIK, freshplayer isn't available in the 14.04 repos.

Thanks for the help, and can you link me to the topic discussing the problem with freshplayer and 16.04, I'd like to read up on it before upgrading, thanks. :)

---

### Post by ajgreeny on 2016-05-18
> **argonvegell said:**
> Yes, I have browser-plugin-freshplayer-pepperflash installed via the webupd8 PPA, because AFAIK, freshplayer isn't available in the 14.04 repos.

Thanks for the help, and can you link me to the topic discussing the problem with freshplayer and 16.04, I'd like to read up on it before upgrading, thanks. :)
I have not yet found any helpful discussion of using flash with freshplayerplugin in 16.04 which is why I am still searching for an answer.

I will keep trying to find out what is going on and I'll report back here if I get an answer.

---

### Post by ajgreeny on 2016-05-19
OK argonvegell, I have now figured out how to get flash 21 working in firefox; it was purely by trial and error, and a lucky chance.

First you need to make sure that you are installing packages without the recommended packages being considered as dependencies; I do this using synaptic package manager which I believe is the best GUI application available.  Install it if you don't already use it as it makes life much easier for you, and in its preferences, set it to not install recommended packages.

Now install only the **adobe-flashplugin** and **browser-plugin-freshplayer-pepperflash** packages are installed; just those two, none of the others.  You should then find that flash version 21.0.0.242 works fine in FF as well as chromium.

Good luck.

EDIT:
An update approx 2 hours later.

I think the above may actually be incorrect.

I was having problems running chromium browser in my virtual installations of 16.04 (Xubuntu and Ubuntu) and this has been solved by not using 3D display acceleration in the VM settings.  This may also have the effect of allowing flash 21 in firefox to run as I expected, so it may not be the extra packages that cause the problem at all; perhaps just the 3D display settings.

I have not had time yet to thoroughly test this hypothesis but will do so when time allows.

Whatever is the answer, I suspect it may be more related to the virtual installation rather than a norma direct installation to a computer.

Watch this space!

---

### Post by ajgreeny on 2016-05-20
I have now tested all these hypotheses, and it was indeed the 3D acceleration in my VMs which was stopping flash 21 from working in firefox.

Now I can run the virtual installs of Ubuntu and Xubuntu 16.04 and get FF to use flash 21 as I wanted.

---

