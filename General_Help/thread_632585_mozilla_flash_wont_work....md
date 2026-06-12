---
title: "mozilla flash wont work..."
date: 2007-12-05
forum: General Help
---

### Post by illbashu on 2007-12-05
i installed flash through the mozilla by clicking on get plug in,i restarted mozilla and it said get plugin again, when i tried installing it again it said flashplugin-nonfree is already installed or something like that :/ and help guys...

---

### Post by jespdj on 2007-12-05
There's an annoying bug with installing Flash.
Try installing it on the command line with:
```
sudo apt-get install flashplugin-nonfree
```
You'll probably see a message about an md5sum that's not correct. (If it says the plugin is already installed, try to uninstall it first with "sudo apt-get purge flashplugin-nonfree").

Try searching the forums for "flashplugin" and you'll find more posts about the problem, for example:

[http://ubuntuforums.org/showthread.php?t=632322](http://ubuntuforums.org/showthread.php?t=632322)
[http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)
[http://ubuntuforums.org/showthread.php?t=631998](http://ubuntuforums.org/showthread.php?t=631998)
[http://ubuntuforums.org/showthread.php?t=631887](http://ubuntuforums.org/showthread.php?t=631887)

I think this happens because Adobe released a new version of Flash and when that happens, Ubuntu has to update a checksum in their Flash installer package somewhere. Try waiting until tomorrow or the day after and try installing Flash again - maybe then it will work without problems (because the checksum will have been updated).

---

