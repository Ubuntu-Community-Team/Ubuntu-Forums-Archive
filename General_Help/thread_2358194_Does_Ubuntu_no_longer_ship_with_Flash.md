---
title: "Does Ubuntu no longer ship with Flash?"
date: 2017-04-10
forum: General Help
---

### Post by alexwaltz on 2017-04-10
I just reinstalled Ubuntu 14.04 on my PC after having downloading the most recent .iso file from the Ubuntu website.

Since installing it, every time I go to a website with a flash video, I am presented with a message to "get Adobe Flash" as the video doesn't play.  I know I didn't have to do this prior to reinstalling the OS.  If I follow the link to the Adobe website, the option is to download a .tar or .rpm but there is no .deb file.

I am using the Google Chrome browser if that makes a difference.

How do I go about fixing this?

Thank you

---

### Post by deadflowr on 2017-04-10
Ubuntu has never shipped with flash.

Google Chrome does ship with flash.
However the Chromium browser available in the software center does not.

If using chromium, you'll need to install the adobe-flashplugin package.
To install the adobe-flashplugin package you need to enable the Canonical Partners repository.
To enable the Partners repo, Open Software and Updates, go to Other software, check Canonical Partners, close and select reload.
then run
```
sudo apt-get install adobe-flashplugin
```

There could also be several other factors as to why flash os not working on Google Chrome.
One off the top is that the flash plugin settings are inactive.
To check open a new browser tab and put this in it:
```
chrome://settings/content
```
scroll down to Flash and see what settings it is at.

See what all that gibber gabber does.
Hope it helps

---

### Post by efflandt on 2017-04-11
Normally **flash** for Firefox is only installed if you do what deadflowr says above, or if you install **ubuntu-restricted-extras** which besides flash installs a bunch of audio/video codecs.

---

