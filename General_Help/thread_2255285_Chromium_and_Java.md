---
title: "Chromium and Java"
date: 2014-12-03
forum: General Help
---

### Post by michael-piziak on 2014-12-03
I've installed every icedtea I can see in the software center.  I've also installed openjdk java 7 runtime.  I even typed this into terminal: "[COLOR=#000000][FONT=Ubuntu Mono] sudo apt-get update && sudo apt-get install default-jre icedtea-plugin"  I've probably over installed at this point.  Please advise if you think that could be the case also.

Java seems to run fine in Firefox; however, I still get messages like this with Chromium - see attached file.  Perhaps I should switch to Chrome - that worked for me before.

This may be a flash problem.  I can't finder [/FONT][/COLOR]pepperflashplugin-nonfree  in the software center - perhaps someone can give me the terminal code for that.[COLOR=#000000][FONT=Ubuntu Mono]




[/FONT][/COLOR]

---

### Post by nerdtron on 2014-12-04
I'm not sure if it already worked for you before but now I'm pretty sure the icedtea plugin for java only works for firefox.

As for flash, this is the command I used to install it and enable on Chromium.
```
 sudo apt-get install pepperflashplugin-nonfree 
```

And don't forget to install the ubuntu-restricted packages for all other codec support.
```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by michael-piziak on 2014-12-04
Thanks for your reply!

Is the Ubuntu-restricted extras the same thing I let it install during installation - the 3rd party option I believe - ?

Update:  I found the ubuntu restricted extras in the ubuntu software center also.  It gave me this message though - what do you make of it (see image)

---

### Post by michael-piziak on 2014-12-04
> **nerdtron said:**
> I'm not sure if it already worked for you before but now I'm pretty sure the icedtea plugin for java only works for firefox.

As for flash, this is the command I used to install it and enable on Chromium.
```
 sudo apt-get install pepperflashplugin-nonfree 
```

And don't forget to install the ubuntu-restricted packages for all other codec support.
```
sudo apt-get install ubuntu-restricted-extras 
```

I typed this into terminal "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install pepperflashplugin-nonfree"

[/FONT][/COLOR]Unfortunately, it couldn't find it.  Seem image below.

---

### Post by nerdtron on 2014-12-04
> **michael-piziak said:**
> Thanks for your reply!

Is the Ubuntu-restricted extras the same thing I let it install during installation - the 3rd party option I believe - ?

Update:  I found the ubuntu restricted extras in the ubuntu software center also.  It gave me this message though - what do you make of it (see image)

I think they're the same, just continue with the installation.

---

### Post by nerdtron on 2014-12-04
> **michael-piziak said:**
> I typed this into terminal "[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install pepperflashplugin-nonfree"

[/FONT][/COLOR]Unfortunately, it couldn't find it.  Seem image below.

Could be a problem on your repositories. Did you ran "sudo apt-get update" first?

Did you activate all repositories?
On the Software Center> Software Sources. On the Ubuntu Software tab, check the four check boxes, Canonical, Community, Proprietary and Software restricted.

Your software center will update in a few seconds and try searching for the plugin again.

---

### Post by carlwsnyder on 2014-12-04
Those packages included during installation _do not_ include all of the codecs included in the Ubuntu-restricted-extras, only some of the .mp3 and .mp4 plugins.  ubuntu-restricted-extras also includes the codecs required to watch commercial DVDs.

On your Software Sources enabling repositories, if you do not have the Multiverse (Software Restricted) repositories enabled, you can't find pepperflashplugin-nonfree, because it downloads pepperflash from the Google repositories for Google Chrome.

---

