---
title: "Will there be a problem if I rename chromium-browser file?"
date: 2017-08-27
forum: General Help
---

### Post by webmiester on 2017-08-27
Hi guys,

Ive been trying to figure out how to lockdown Chromium the best I can.  So far, whitelists and configuration add-ons can easily be bypassed.  What I did is set Chromium to run on kiosk mode and kiosk app so that people wont have the capability to surf all sorts of apps with it and only use it for its intended system application use.  My problem, is that even this can be bypassed by opening a terminal (using keyboard shortcut) and loading chromium from the command line.

I figured, maybe if I was to change the chromium-browser name into something else, then people who open the terminal wont be able to simply open chromium.  Will this pose any problem?  Like will ubuntu or chromium still look for the chromium-browser name under that filename after it starts?  Just for kicks, can anyone tell me what directory I should look chromium-browser up?  Thanks so much.

---

### Post by dragonfly41 on 2017-08-27
I would consider developing a bundled app in Qt 5.* with built in webapp/browser.

[http://doc.qt.io/qt-5/topics-web-content.html](http://doc.qt.io/qt-5/topics-web-content.html)

Example here ... [http://doc.qt.io/qt-5/qtwebengine-webenginewidgets-demobrowser-example.html](http://doc.qt.io/qt-5/qtwebengine-webenginewidgets-demobrowser-example.html)

---

