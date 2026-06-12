---
title: "manual install of flash..."
date: 2007-12-18
forum: General Help
---

### Post by sethfc on 2007-12-18
installing flash 9 maually for linux (as my firefox doesnt prompt me for it).

i've unpacked the .tar form the website, and i'm in the console, browsed to desktop, and i'm in the installation.


its askin for the installation path of mozilla.

i type

```
/usr/lib/mozilla
```

just as my address bar says when i go lookin for the folder via interface.  the installation says that is not a valid installation path.

wtf o_0

---

### Post by ubuntu27 on 2007-12-18
What version of Ubuntu Linux are you using? If it is the latest version (Ubuntu 7.10 - Also known us Gutsy Gibbon) then it should prompt you to install Flash player when visiting a website with Flash content.

Well, either way. Open-up the terminal (It is located at Applications menu/Accessories/Terminal)

and type the following (or simply copy and paste them)

```
sudo apt-get install flashplugin-nonfree
```

press enter and type you password. Don't worry that it doesn't show what you type. It is a security feature ;)   then press enter again on your keyboard.

with that command, it will download restricted (non-free) Flash player from Adobe.com and install it automatically.


You should visit the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page to learn more about formats&codecs and how to install them.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sethfc on 2007-12-18
i know about gnash, and it works hideously in my opinion, so i was going with the straight adobe. =/

---

### Post by aysiu on 2007-12-18
> **ubuntu27 said:**
> What version of Ubuntu Linux are you using? If it is the latest version (Ubuntu 7.10 - Also known us Gutsy Gibbon) then it should prompt you to install Flash player when visiting a website with Flash content. Yes. More details (with screenshots) here: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by sethfc on 2007-12-18
yes i have 7.10

yes firefox prompted me for gnash and adobe install when i visited youtube.

i installed both.

it was very jenky.

i uninstalled gnash, now i see no flash even at you tube.

firefox now does not prompt me for a plugin

so i'm doing a manual install.

EDIT: i misspelled ''no'', so i changed it from ''now'' to ''no'' =p

---

### Post by ubuntu27 on 2007-12-18
The install instruction that I gave you is for **Adobe's** Flash.


You probably need to remove both Flash players, and then install Adobe's flash again.

---

