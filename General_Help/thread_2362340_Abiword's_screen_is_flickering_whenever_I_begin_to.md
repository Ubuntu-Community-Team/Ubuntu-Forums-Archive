---
title: "Abiword's screen is flickering whenever I begin to type"
date: 2017-05-27
forum: General Help
---

### Post by ardouronerous on 2017-05-27
I've just installed Lubuntu 16.04.2 on my old Dell Inspiron E1505, and one of the first things I notice is Abiword's screen is flickering whenever I begin to type, and it gets pretty annoying, especially when I have to create important documents.

Any lightweight alternatives available in the repos for Abiword? I don't want to venture out of the repos as much as possible.

---

### Post by vasa1 on 2017-05-27
See [https://ubuntuforums.org/showthread.php?t=2362324](https://ubuntuforums.org/showthread.php?t=2362324)

---

### Post by ardouronerous on 2017-05-27
Okay for the reply.
That's unfortunate, I've already themed my Lubuntu to my liking, so don't want to go to another theme.

Any alternatives to Abiword?

---

### Post by vasa1 on 2017-05-27
The fix only changes the theme for Abiword only, not for the rest of the system. Good luck with finding something else. If you do, please share!

---

### Post by ardouronerous on 2017-05-27
> **vasa1 said:**
> The fix only changes the theme for Abiword olny, not for the rest of the system. Good luck with finding something else. If you do, please share! 		

How do I change the theme of Abiword?

I can't find adwaita in Lubuntu Software Center, and I've been searching Abiword for theme changing, there no option for it.

---

### Post by vasa1 on 2017-05-27
First, please try```
GTK_THEME=Adwaita abiword
```from a terminal. Does that do anything?

If that works, try```
GTK_THEME=Adwaita:dark abiword
```and see if you like that better.

---

### Post by ardouronerous on 2017-05-27
This opened up Abiword.
It fixed the flickering issue.

Does that mean I have to access Abiword from the terminal always, then?

Adwaita dark looks a lot better and it fits my current theme.

---

### Post by vasa1 on 2017-05-27
> **ardouronerous said:**
> This opened up Abiword.
It fixed the flickering issue.

Does that mean I have to access Abiword from the terminal always, then?

Adwaita dark looks a lot better and it fits my current theme.
No, you can make a .desktop file and that will allow you to double-click on the Abiword icon or on an Abiword file to open it with the Adwaita theme:

Here's my .desktop file which I have in *~/.local/share/applications*:
```
[Desktop Entry]
Exec=bash -c 'GTK_THEME=Adwaita:dark abiword %U'
Icon=abiword
Terminal=false
Type=Application
Categories=Office;WordProcessor;GNOME;GTK;X-Red-Hat-Base;
StartupNotify=true
X-Desktop-File-Install-Version=0.9
MimeType=application/x-abiword;text/x-abiword;text/x-xml-abiword;text/plain;application/msword;application/rtf;application/vnd.plain;application/xhtml+xml;text/html;application/x-crossmark;application/docbook+xml;application/x-t602;application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.sun.xml.writer;application/vnd.stardivision.writer;text/vnd.wap.wml;application/wordperfect6;application/wordperfect5.1;application/vnd.wordperfect;application/x-abicollab;application/vnd.palm;application/x-applix-word;application/x-kword;application/x-mif;application/x-mswrite;application/x-palm-database;text/abiword;text/richtext;text/rtf;
Name=AbiWord
GenericName=Word Processor
Comment=Compose, edit, and view documents

```

To make the .desktop file, open *leafpad* and paste the above contents into it. Save it as */home/vasa1/.local/share/applications/abiword.desktop* but instead of *vasa1*, use your own username.

---

### Post by ardouronerous on 2017-05-27
Okay, thanks that worked.:p

---

### Post by vasa1 on 2017-05-27
> **ardouronerous said:**
> ...
I can't find adwaita in Lubuntu Software Center, ...
At some point in 2014, the Adwaita theme was folded into GTK+ and then no longer available as a separate package: [https://blogs.gnome.org/mclasen/2014/06/13/a-new-default-theme-for-gtk/](https://blogs.gnome.org/mclasen/2014/06/13/a-new-default-theme-for-gtk/)

---

### Post by romparomp on 2017-07-23
Cheers vasa1, much appreciated

thank you for posting your question ardouronerous

through using your assistance suggest :

using leafpad to open "abiword.desktop", pasting in vasa1's script, and saving "abiword.desktop"

start leafpad from starter button/accessories/leafpad <alt> + <f> 'open' 'search' = type in "abiword.desktop" <enter> then insert vasa1's  script (the file 'biword.desktop was completely blank before that, if it contains text rename the file by 'save as...' reopen 'abiword.desktop <ctrl> + <a> delete, then paste in vasa1's script.

The abiword flickering soon disappears

---

