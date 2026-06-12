---
title: "Patch - howto?"
date: 2017-08-07
forum: General Help
---

### Post by smithbox on 2017-08-07
Hi all.
My OS: ```
 uname -a
Linux mike-desktop 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```
I have to add path from page: [https://github.com/nE0sIghT/chrome-gnome-shell-mirror/commit/d43f0f97f5fd56dafaecd6b95b00de8cf02d5432](https://github.com/nE0sIghT/chrome-gnome-shell-mirror/commit/d43f0f97f5fd56dafaecd6b95b00de8cf02d5432)
In spite of fact, I read many webpages still do something wrong.
If I could ask you for favor, to show me (step after step) how to build in this path.:confused:
Briefly, patching howto?
I would appreciate any help with links to tutorials with patching in practice, to lern this subject.
Thank you.
Regards.
Mark.

---

### Post by Autodave on 2017-08-07
I don't understand your question/problem. What exactly is your problem or what are you trying to do?

Some specs of your machine may be helpful.

---

### Post by smithbox on 2017-08-07
I tray to install: ANoise from site: [http://anoise.tuxfamily.org/](http://anoise.tuxfamily.org/)
To do this I have to install:
- gnome shell
   I get message ```
no_gnome_shell
```
- media player indicator.
To get this working, I need to install path from site: [URL="https://github.com/nE0sIghT/chrome-gnome-shell-mirror/commit/d43f0f97f5fd56dafaecd6b95b00de8cf02d5432"]https://github.com/nE0sIghT/chrome-g...00de8cf02d5432


[/URL]

---

### Post by dragonfly41 on 2017-08-07
[Does this link help you?]("https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation")

Look at Ubuntu installation.
```
[COLOR=#000000][FONT=courier]sudo apt-get install chrome-gnome-shell
```[/FONT][/COLOR]

---

### Post by smithbox on 2017-08-07
```
sudo apt-get install chrome-gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chrome-gnome-shell is already the newest version (9-0ubuntu1~ubuntu16.10.1).
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
```

[http://imgur.com/a/n7x7W](http://imgur.com/a/n7x7W)

---

### Post by dragonfly41 on 2017-08-07
Next suggestion since you have package installed

[go here ]("https://extensions.gnome.org/extension/55/media-player-indicator/")..

and follow instructions ..
> [COLOR=#555555][FONT=Cantarell]To control GNOME Shell extensions using this site you must install GNOME Shell integration that consists of two parts: browser extension and native host messaging application.[/FONT][/COLOR]
[Click here to install browser extension]("https://extensions.gnome.org/extension/55/media-player-indicator/#")[COLOR=#555555][FONT=Cantarell]. See [/FONT][/COLOR][wiki page]("https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation")[COLOR=#555555][FONT=Cantarell] for native host connector installation instructions.[/FONT][/COLOR][COLOR=#555555][FONT=Cantarell]

[/FONT][/COLOR]

---

### Post by dragonfly41 on 2017-08-07
Also if you go to chrome web store you can install extension ...

[https://chrome.google.com/webstore/search/gnome-shell](https://chrome.google.com/webstore/search/gnome-shell)

---

### Post by smithbox on 2017-08-07
Gnome Shell Integration - installed.
[URL="http://imgur.com/a/1zKGQ"]http://imgur.com/a/1zKGQ


[/URL]I can not install:
 ```
 gnome-shell-extensions-mediaplayer
``` 
My browser is FF.

SOLUTION on page:  [https://www.waltercedric.com/index.php/all-my-hobbies/352-linux/2284-ambient-noise-for-ubuntu-16-10](https://www.waltercedric.com/index.php/all-my-hobbies/352-linux/2284-ambient-noise-for-ubuntu-16-10)

---

### Post by dragonfly41 on 2017-08-07
Being curious, I did manage to install anoise before reading the SOLUTION link above
but after launching and listening to some ambient dinner conversations I removed anoise.
I have no use for it.

---

