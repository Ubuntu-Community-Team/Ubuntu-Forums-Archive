---
title: "Command line switches in Chrome"
date: 2013-01-09
forum: General Help
---

### Post by daKoolaid on 2013-01-09
How do we add these? In chromium it was so easy with a file to edit in /etc/chromium-browser/Default but Chrome doesn't have a way. 

I added my flag to the .desktop file but it wasn't applied. Is there a better way to do this?

---

### Post by llamabr on 2013-01-09
Dunno.  Maybe if you say more specifically what you'd like to do, we can try to steer you in the right direction.

---

### Post by vasa1 on 2013-01-09
What did you do? Could you give an example? Here is one of my Chrome .desktop files from /usr/share/applications:
```
[Desktop Entry]
Version=1.0
Name=Privo Chrome
GenericName=Web Browser
Exec=/opt/google/chrome/google-chrome --start-maximized --profile-directory=Default --proxy-server=127.0.0.1:8118 %U
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;Favorites;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito

```
I've removed a lot of extraneous material. That's why it's so short ;)

BTW, you could also provide what you see when you type ```
about:
``` in the address bar and hit enter.
I see:
```
Google Chrome	23.0.1271.97 (Official Build 171054)
OS	Linux
WebKit	537.11 (@136278)
JavaScript	V8 3.13.7.5
Flash	11.5.31.5
User Agent	Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11
Command Line	 /opt/google/chrome/google-chrome --start-maximized --profile-directory=Default --proxy-server=127.0.0.1:8118 --flag-switches-begin --disable-asynchronous-spellchecking --disable-restore-session-state --disable-threaded-animation --disable-webgl --disable-force-compositing-mode --disable-sync-app-notifications --disable-threaded-compositing --flag-switches-end %U
Executable Path	/opt/google/chrome/google-chrome
Profile Path	/home/vasa1/.config/google-chrome/Default
Variations	853359fa-186f5907
1d3048f1-9de009d0
cd73da34-cf196cb ...
```

---

### Post by daKoolaid on 2013-01-09
> **vasa1 said:**
> What did you do? Could you give an example? Here is one of my Chrome .desktop files from /usr/share/applications:
```
[Desktop Entry]
Version=1.0
Name=Privo Chrome
GenericName=Web Browser
Exec=/opt/google/chrome/google-chrome --start-maximized --profile-directory=Default --proxy-server=127.0.0.1:8118 %U
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;Favorites;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito

```
I've removed a lot of extraneous material. That's why it's so short ;)
 
BTW, you could also provide what you see when you type ```
about:
``` in the address bar and hit enter.
I see:
```
Google Chrome    23.0.1271.97 (Official Build 171054)
OS    Linux
WebKit    537.11 (@136278)
JavaScript    V8 3.13.7.5
Flash    11.5.31.5
User Agent    Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.97 Safari/537.11
Command Line     /opt/google/chrome/google-chrome --start-maximized --profile-directory=Default --proxy-server=127.0.0.1:8118 --flag-switches-begin --disable-asynchronous-spellchecking --disable-restore-session-state --disable-threaded-animation --disable-webgl --disable-force-compositing-mode --disable-sync-app-notifications --disable-threaded-compositing --flag-switches-end %U
Executable Path    /opt/google/chrome/google-chrome
Profile Path    /home/vasa1/.config/google-chrome/Default
Variations    853359fa-186f5907
1d3048f1-9de009d0
cd73da34-cf196cb ...
```
 
Ohhh ok, I was just changing the desktop file in Chrome's /opt folders. Now that I modified the one in /usr/share/applications, it works fine. Thanks alot!

---

### Post by vasa1 on 2013-01-09
A possibly better idea would be to copy over .desktop files to ~/.local/share/applications and then mess with them. That way, they'd be unaffected by updates to the browser.

---

### Post by daKoolaid on 2013-01-30
> **vasa1 said:**
> A possibly better idea would be to copy over .desktop files to ~/.local/share/applications and then mess with them. That way, they'd be unaffected by updates to the browser.
Yeah I just noticed that my switch is gone after Chrome updated. If I copy the google-chrome.desktop into the folder you mention, I try to launch it and it says Untrusted Application and then nothing happens.  

How do I fix this?

---

### Post by vasa1 on 2013-01-31
Two things ... 

you could share the contents of the particular .desktop file in case there's something in there that needs to be fixed

Also, you could first try the following contents in a new .desktop file:
```

[Desktop Entry]
Version=1.0
Name=Temp Chrome
GenericName=Web Browser
Comment=Access the Internet
Exec=/opt/google/chrome/google-chrome %U
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
X-Ayatana-Desktop-Shortcuts=NewWindow;NewIncognito

```
This works for me. If it works for you, put in the switch and try again.

---

### Post by daKoolaid on 2013-01-31
Thanks vasa1, I made a desktop file out of what you said and that works fine.

---

