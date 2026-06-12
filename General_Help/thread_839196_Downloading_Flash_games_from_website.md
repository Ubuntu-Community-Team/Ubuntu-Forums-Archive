---
title: "Downloading Flash games from website"
date: 2008-06-24
forum: General Help
---

### Post by Wikzo on 2008-06-24
On the following week I'm going on vacation. I'll take my laptop with me, but there is no Internet access. Therefore I want to have some few games to play, and I have two great Flash games I want to download.

Both are stored on an online website. Now my question is: How do I download them?

Desktop Tower Defense
[http://handdrawngames.com/DesktopTD/game.asp](http://handdrawngames.com/DesktopTD/game.asp)

Portal 2D
[http://www.newgrounds.com/portal/view/404612](http://www.newgrounds.com/portal/view/404612)

I have tried to use this command without any useful results.

```
wget -mk -w 2 -l 1 http://handdrawngames.com/DesktopTD/game.asp

```

Please help me, there must be a way to get those games! I use Firefox in Ubuntu 8.04 :)

---

### Post by Zorael on 2008-06-24
You can likely do this by examining the source file for that .asp page, but I know this method works. Install Flashblock from [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433). Browse to your game page, right-click the now-blocked embedded flash content, pick Copy Flash location and use wget to download it. Feel free to disable Flashblock afterwards, of course.

---

### Post by erginemr on 2008-06-24
A similar way to download Flash content from web pages also passes through using another plugin: **Video DownloadHelper**

[http://www.downloadhelper.net/](http://www.downloadhelper.net/)
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by erginemr on 2008-06-24
Besides, if you open the games in Flash, a copy of the flash (swf) file is kept in "/tmp" tempoarary folder as long as you keep the page open. You can copy this file to your desktop and run the game by dragging it to a Firefox window.

---

### Post by Wikzo on 2008-06-24
Thank you, but I have two problems:

1. I am able to download the Portal game by using ```
wget http://uploads.ungrounded.net/404000/404612_Portal.swf

```. But when I try to play it with Gnash or Swfdec Flash Player the game freezes after a minute or so, telling me that the file is corrupted. I need a stable Flash player in Ubuntu; which should I use?

2. There is some sort of protection on the Desktop Tower Defense game. If I do the same as above and play it with Gnash, I get a screen with a link to the game on their website. Is there any way to get past this protection?

---

### Post by erginemr on 2008-06-24
In that case, I suspect the games load themselves partially and proceed from thereon (say after a few levels). If this is the case, then you don't have much options.

You should try Firefox as the de facto/impromptu Flash player.

---

