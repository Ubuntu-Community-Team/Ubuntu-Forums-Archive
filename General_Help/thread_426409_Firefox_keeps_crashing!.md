---
title: "Firefox keeps crashing!"
date: 2007-04-28
forum: General Help
---

### Post by josesanders on 2007-04-28
I tried to install some add-on or plugin or something for Firefox, and now it just closes every time I try to open a new page.  I can't even access this forum from that computer anymore.

I removed the add-on but it had no effect.  I tried uninstalling and reinstalling firefox but it still does the same thing.  I even tried upgrading from Edgy to Feisty hoping that would replace everything, but still no luck.  I'm desperate, so any help would be much appreciated.  I have a lot of files on that computer, so I don't want to have to reinstall Ubuntu.

---

### Post by josephus on 2007-04-28
which add-on was it?

try removing/renaming the ~/.mozilla folder and see if it's some remnant in your user settings

---

### Post by nontitle on 2007-04-28
i had the same problem. chances are it doesn't have anything to do with the add-ons, but in fact Java. if you can, don't use Java 1.5, instead install an older version, most (if not all) java programs should work with the older version.

your best bet is probably going to synaptic package manager and searching for java, then uninstall java 1.5 and install the older version.

also, how did you uninstall firefox without uninstalling ubuntu?

---

### Post by josesanders on 2007-04-28
> try removing/renaming the ~/.mozilla folder and see if it's some remnant in your user settings

That seems to have done it.  Thanks.  The add-on that made it crash had something to do with Rhapsody.  I should have known better.

To uninstall firefox, I just did the following:

$ sudo apt-get remove firefox

---

### Post by UbuntuKhan on 2007-04-29
I also experienced firefox problems after un upgrade from Edgy. It kept crushing. First I thought it crushed every time I opened a tab and I believed it was Firefox. I've uninstalled and reinstalled Firefox a couple of times with no luck. Then I've noticed that only those pages with flash where to blame. So I uninstalled the flash plug-in and no crashes. 
Is there a way to have the flash back (I don't want a flashback) without the crashes?

---

### Post by josephus on 2007-04-29
how did you install flash to begin with?  try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

there is a section about what to if firefox  keeps crashing with flash.

---

### Post by UbuntuKhan on 2007-04-29
I've installed Flash with the help of Automatix in Edgy and when I upgraded to Feisty it remained in Firefox. I have tried to reinstall it from automatix but I've got the same result (crushing Firefox, that is). Thanks for the link. I will look into it.

---

### Post by UbuntuKhan on 2007-04-30
Thanks josephus, it worked.
For all those who encountered the same problem:
> Note: if firefox crashes when visiting a website with flash content, do the following:
Open the firefox file  

```
sudo gedit /usr/bin/firefox
```

Add the following line as last but one line of the file: 

```
export XLIB_SKIP_ARGB_VISUALS=1
```

Now firefox shouldn't crash anymore. (Launchpad bug report: [1]) 

Source:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")

---

### Post by steveneddy on 2007-06-05
My fix for this problem was a three step process [here]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287").

-SE

---

