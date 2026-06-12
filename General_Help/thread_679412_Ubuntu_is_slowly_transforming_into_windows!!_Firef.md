---
title: "Ubuntu is slowly transforming into windows!! Firefox plugins..."
date: 2008-01-26
forum: General Help
---

### Post by jesushero on 2008-01-26
My ubuntu has started to become annoyingly windows-like.. I've "lost" the flash plugin!!!

I used to have flashplugin-nonfree installed. It was installed using an install script. I just kept on crashing, so I removed it (manually, since there is no real way to remove things installed with crappy install scripts). 

I tried installing gnash from the package manager. After the installation, I started firefox and tried to view a flash website. I got a plugin missing screen. I did a complete removal of gnash and installed flashplugin-nonfree again from the package manager this time. Started firefox, visited a flash page, missing plugin again!!! Complete removal, got a .deb package from someone who says it is a fix for the unstable flashplugin-nonfree. I installed that, started firefox, flash page, missing plugin!! Complete removal again. 

With no flash installed, I loaded firefox again, visited the same flash page, missing plugin, I clicked on it and the plugin search started. It found adobe flash, I started the installation, waited a bit and it returned a FAILED message. I searched for libflashplugin.so on my filesystem and found the file on my home folder (from an earlier download) and renamed it just to make sure. I checked the firefox plugins folder, no flash plugin there. I searched for the xpti.xpt or however this is called and it was not there. 

I restarted the computer, loaded firefox, and it crashed for the first 10 times... Then it started, and I loaded the flash page, and THE FLASH WAS PROPERLY DISPLAYED!!!! I checked the about:plugins screen and it tells me I have shockwave flash installed!!! I checked all firefox/mozilla/mozilla-firefox folders and plugins folders and there's NO flash plugin there!!!!! 

WHERE THE #$@% IS THE FLASH PLUGIN AND HOW DID IT GET THERE????? 

(according to package manager no flash plugin or anything like a flash plugin is installed!!)

---

### Post by AsoSako on 2008-01-26
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

This is the latest flash plugin. Simply install it and it would work.  The one in the repositories is currently broken and that is why you are having problems.

Oh and your plugins should be at:
```
/usr/lib/firefox/plugins
```

I hope this helps.  :D

---

### Post by jesushero on 2008-01-27
> **agsimeonov said:**
> [http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

This is the latest flash plugin. Simply install it and it would work.  The one in the repositories is currently broken and that is why you are having problems.

I hope this helps.  :D

Hey, thanks for replying. I've tried this, right after uninstalling the one on the repositories. It is the one I mention as the "fix". I've also searched the firefox plugins directory and there's definitely NO flash plugin there!! 

So my problem is, Firefox somehow supposes there is a flash plugin somewhere and uses it! It is crappy. I can't find it anywhere to remove it! If I don't remove it, it's not a good idea to install anything else on top of that!! I've tried all flash alternatives known to the civilised Ubuntu user since 1456 AD and they all crash, so I guess the problem is somewhere else within firefox! 

Is it about time I removed firefox to reinstall it? I guess a complete removal would fix it.. But isn't this way too Windows-like?? The Ubuntu installation is not more than a couple of months old! 

If anyone has any ideas on locating flash plugins that just aren't there, let me know!!!

---

### Post by bollix47 on 2008-01-27
Try to update your search database and search again.

```
sudo updatedb
locate libflashplayer.so
```

---

### Post by fyo on 2008-01-27
> **jesushero said:**
> If anyone has any ideas on locating flash plugins that just aren't there, let me know!!!

This is where Linux is very UNwindowslike.

A typical Firefox installation is global, but you can install plugins both locally and globally.

Local plugins are found in ~/.mozilla/plugins/

That's all good, but things get a bit messy with the global plugins. There are too many different versions of the plugins and too many different places they can reside in.

Your best best is probably:

```
/usr/lib/mozilla/plugins/
```

(mozilla instead of firefox).

Of course, this being Linux, you could always just see what flash process is taking up resources when running flash stuff and then search for it using locate or find.

---

### Post by swoop_ubu on 2008-01-28
> **agsimeonov said:**
> 
The one in the repositories is currently broken and that is why you are having problems.


This is true. If you'd expand the install log window while installing FLASH in Firefox, you'd see
something like "...flasplugin-nonfree MD5 mismatch - package *NOT* installed...".
Despite this, Firefox will say it is OK and the again report missing plugin :(

Does anyone know when will be the flasplugin-nonfree repository fixed?

Cheers
ubu

---

