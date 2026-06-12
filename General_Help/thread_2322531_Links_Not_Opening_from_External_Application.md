---
title: "Links Not Opening from External Application"
date: 2016-04-28
forum: General Help
---

### Post by dannymichel on 2016-04-28
When i click links from my IRC client, it opens Chromium, but doesnt open the link. In fact, it opens a whole new separate Chromium window instead of opening up a new tab with the link

---

### Post by dannymichel on 2016-04-30
Links from outside applications don't open in Chromium. I click them from the application(such as IRC clinet), and it opens a new Chromium window, but does not open the URL. If i repeat the clicking, it will continue opening new blank Chromium windows.

---

### Post by dannymichel on 2016-05-01
Bump?

---

### Post by dannymichel on 2016-05-02
I was able to fix this with
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=Chromium
Exec=/usr/bin/chromium-browser %U
StartupNotify=false
StartupWMClass=chromium-browser
Terminal=false
Icon=chromium-browser
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito
```

---

