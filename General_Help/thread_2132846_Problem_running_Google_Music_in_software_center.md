---
title: "Problem running Google Music in software center"
date: 2013-04-06
forum: General Help
---

### Post by thiesing on 2013-04-06
Pardon me, I'm pretty much a Ubuntu virgin... 
I'm trying to upload files to Google Music. I DL'ed Google Music from the Play Store, DL'ed 32bit for Ubuntu file download package, installed the package on Ubuntu Software Center...but when I open the 'Google Music Uploader' in Software Center all I see is "this program is run from a terminal: google-musicmanager". 
I have uninstalled and reinstalled several times, I'm not sure what I'm doing wrong. If I have to run this in a terminal, how do I do that? I searched for help online, this same thing has happened to others but I don't understand HOW to perform this...

[COLOR=#000000][I][FONT=arial narrow]"Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards"
[/FONT]


[/I][/COLOR]Where is ~/.config? Is that a folder, or do I type that in my terminal? Can someone take that paragraph and reword it for a beginner, or help me resolve this alternatively?

---

### Post by HiImTye on 2013-04-06
> **thiesing said:**
> installed the package on Ubuntu Software Center...but when I open the 'Google Music Uploader' in Software Center
just to be clear, are you opening it *inside software center* or are you trying to launch it from a launcher?
> **thiesing said:**
> all I see is "this program is run from a terminal: google-musicmanager".
...
If I have to run this in a terminal, how do I do that?
either hit **ctrl+c** or go to **Accessories > Terminal**. alternatively, you could hit **alt+f2** and then type **gnome-terminal** into the box that appears and then click on **run**
> **thiesing said:**
> I searched for help online, this same thing has happened to others but I don't understand HOW to perform this...

[COLOR=#000000][I][FONT=arial narrow]"Right, same problem but I think I have a fix - uninstall the music manager. Go into ~/.config and delete the google-music-manager directory then install the package all over again, when the first run wizard begins, click upload and choose an empty directory, go through all the error messages (less than 10 files found, etc) and then once that it done and the icon is in the tray, clicking on it should work. Let me know if this works for you. Regards"
[/FONT]


[/I][/COLOR]Where is ~/.config? Is that a folder, or do I type that in my terminal? Can someone take that paragraph and reword it for a beginner, or help me resolve this alternatively?

[LIST]
[*]**~** is a 'shortcut' for your home folder.
[*]~/**.config** is a hidden folder inside your home folder, named '.config' (all hidden files and folders start with a '.')
[/LIST]
to do what those instructions say, either:
[LIST=1]
[*]open **Nautilus** (Files)
[*]hit **ctrl+h** to show hidden files
[*]double click on **.config**
[*]delete **google-music-manager**
[/LIST]
or open a terminal (see above) and then type in (or middle click with this command highlighted):
```
rm -Rfv ~/.config/google-music-manager
```

---

### Post by thiesing on 2013-04-06
Thank you, seriously... thank you so much! It's working now! My phone has new music now, w00t!:)

---

### Post by HiImTye on 2013-04-06
you're welcome, I'm glad I could help :D

please [mark this thread solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so that others can benefit from it :)

---

