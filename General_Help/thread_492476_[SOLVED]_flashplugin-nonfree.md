---
title: "[SOLVED] flashplugin-nonfree"
date: 2007-07-04
forum: General Help
---

### Post by YellowSnot on 2007-07-04
I'm pretty new to linux, so perhaps this is something simple, but I haven't been able to find anything on it here or on google. I have installed feisty on a few systems now, generally to get flash working I've just installed flashplugin-nonfree and it worked. On this computer however, I've installed it, uninstalled it, reinstalled etc... several times, and nothing seems to make it work? Help me please!

---

### Post by kevinlyfellow on 2007-07-04
That's interesting.  How is it not working, I'm assuming it's just not detecting the plugin?

The plugins should be install in /usr/lib/flashplugin-nonfree.  Check that they are even there.  Then, go to your firefox plugin directory, and they should be linked to the plugins in /usr/lib/flashplugin-nonfree.  To check use this command
```
ls -l /usr/lib/firefox/plugins/*flash*
```

---

### Post by az on 2007-07-04
> **YellowSnot said:**
> I'm pretty new to linux, so perhaps this is something simple, but I haven't been able to find anything on it here or on google. I have installed feisty on a few systems now, generally to get flash working I've just installed flashplugin-nonfree and it worked. On this computer however, I've installed it, uninstalled it, reinstalled etc... several times, and nothing seems to make it work? Help me please!

Do you get an error?  The flashplugin-nonfree package downloads the plugin from adobe.  If their server is down, that would cause the problem.

The plugin itself is not redistributable, so that's why you need a package to download it for you.

---

### Post by donkyhotay on 2007-07-04
Although some people consider it cheating I've found automatix2 to be invaluable for installing non-free software. Might want to check it out.

---

### Post by YellowSnot on 2007-07-04
ok, this command "ls /usr/lib/flashplugin-nonfree" returns :
flashplayer.xpt  libflashplayer.so

and "ls -l /usr/lib/firefox/plugins/*flash*" returns :
lrwxrwxrwx 1 root root 41 2007-07-04 18:18 /usr/lib/firefox/plugins/flashplayer.xpt -> ../../flashplugin-nonfree/flashplayer.xpt
lrwxrwxrwx 1 root root 43 2007-07-04 18:18 /usr/lib/firefox/plugins/libflashplayer.so -> ../../flashplugin-nonfree/libflashplayer.so

I have never received an error message when installing, and I have reinstalled it several times.

I don't have a chance to install automatix right now, but perhaps later tonight I will get a chance. Thanks for the the help.

EDIT: I'm not sure how its not working, I've only tried using it in firefox.

---

### Post by kevinlyfellow on 2007-07-04
> **YellowSnot said:**
> ok, this command "ls /usr/lib/flashplugin-nonfree" returns :
flashplayer.xpt  libflashplayer.so

and "ls -l /usr/lib/firefox/plugins/*flash*" returns :
lrwxrwxrwx 1 root root 41 2007-07-04 18:18 /usr/lib/firefox/plugins/flashplayer.xpt -> ../../flashplugin-nonfree/flashplayer.xpt
lrwxrwxrwx 1 root root 43 2007-07-04 18:18 /usr/lib/firefox/plugins/libflashplayer.so -> ../../flashplugin-nonfree/libflashplayer.so

I have never received an error message when installing, and I have reinstalled it several times.

I don't have a chance to install automatix right now, but perhaps later tonight I will get a chance. Thanks for the the help.

EDIT: I'm not sure how its not working, I've only tried using it in firefox.

Be careful with automatix, its not that its 'cheating' it's just that it confuses apt and can be difficult to unravel.  

The plugins are there, they are linked, you have all your permissions set up properly.  It should be working.  You can always try the official one from the site.  Also, just to make sure, your not trying this on 64bit ubuntu are you?

---

### Post by YellowSnot on 2007-07-05
well, I suppose I will try automatix as a last resort if we can't get anything else working today. I am on an AMD64 machine, but the 32 bit version of ubuntu is installed. Does this make a difference?

---

### Post by YellowSnot on 2007-07-05
Ok, good news, downloaded directly from macomedia as kevinlyfellow suggested and it worked right off the bat. Thanks for help guys.

---

### Post by Hraefn on 2008-01-05
MD5SUM not equal with recent attempt to download flashplugin-nonfree.

This was on 5 Jan 2008 - could be a glitch?? Figured I'd post here...

I will just download it directly from Macromedia...

---

