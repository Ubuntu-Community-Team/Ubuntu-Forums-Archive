---
title: "Libre Office Issues since upgrade"
date: 2012-10-21
forum: General Help
---

### Post by LandR on 2012-10-21
I upgraded last night to 12.10 and since have had a fair few issues, the worst though is with Libre Office. 

Sometimes when it loads a spreadsheet the entire screen goes black and the machine is totally unresponsive and I have to hard reset it.

Other problems include the menu bar not working and most bizzarely the issues you can see in the spreadsheet where the text on columns, rows and worksheets is just a pixelated mess. This also happens when typing in data to cells, it will appear as a pixelated mess until I hit return. You can also see things like font and font size are unreadable.

[img]http://www.speed-shot.co.uk/images/Other/libreoffice1.png[/img]

---

### Post by dino99 on 2012-10-21
i think you can confirm that report:

```
https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1069345
```

i get a menu bar under gnome-shell, but not with gnome-classic (which is my first choice). I've made a dist-upgrade from PP i386 to QQ and get a borked .config folder, so i've erased it and let ubu recreate one on next login, but got that issue.
Sadly i've not a solution yet, maybe try : rename your .config folder and/or switch to an other DE.

---

### Post by doubled on 2012-10-21
I have menu disappearance issues with LibreOffice Writer on a fresh install of the default Unity desktop. I installed libreoffice-style-galaxy, and the menu would not show up upon restarting LO. I uninstalled Galaxy and got the menu back, but it's erratic. I'm not confident of the stability of LibreOffice under 12.10.

---

### Post by LandR on 2012-10-21
I've just had the issue with the black screen again. I started Calc (just via clicking the icon in my sidebar), it opened up the program then the grid on the spreadsheet goes really distorted. The mouse becomes unresponsive then briefly becomes reponsive again (maybe a second or so) then it goes to a black screen.

I had some audio playing in the background and I could still hear the audio playing over the black screen I had just lost my graphics.

Had to reset the machine.

Is their anything I can look at, logs etc that might give me a clue as to what is causing this ?

---

### Post by wribeiro on 2012-12-12
This bug is reported in:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1082496](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1082496)

---

### Post by wribeiro on 2012-12-14
The bug "menu bar under gnome-classic (1069345)" is not related to the issues shown in the screen image.

I removed the packages menu integration (libreoffice-gnome/libreoffice-gtk)and solved the first problem, but the rendering of the text in the toolbar, menus and controls spreadsheet rows is still buggy.

Can someone please help me solve this?
LibreOffice is completely unusable for me.

---

