---
title: "Chromium app icon will not stay in Unity launcher"
date: 2013-04-12
forum: General Help
---

### Post by talhaguy on 2013-04-12
I'm using Ubuntu 12.10, 32-bit.

I usually use Chromium apps to create shortcuts to online apps that I can put in the Unity launcher. I've made some for Google Calendar, Google Contacts, Wunderlist, etc., which work fine. However, when I created an Evernote one, I encountered a puzzling issue. The app creates fine and I can put the app in the launcher, but when I restart my computer it disappears from there. If I put my computer sleep and open it up it will still be there. I'm not sure why this particular app shortcut will not stay in the launcher because all the other ones stay perfectly fine. I keep having to move the Evernote app shortcut into the launcher every time I restart, which is getting a little tedious.

Also, interestingly, the Evernote app shortcut was not the last one I created. I created the Google Contacts app shortcut after it and thought that I might face the same issue. However, this one works completely fine.

I'm not sure if it's something within the Evernote app shortcut code. As far as I can tell, it mimics the other app shortcuts. Here is what is in the file:
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Evernote Web
Exec=/usr/bin/chromium-browser "--app=https://www.evernote.com/Home.action?login=true&targetUrl=%2FHome.action#st=p&n=808fd4e8-9ae8-4961-83eb-e339bde05f1c"
Terminal=false
X-MultipleArgs=false
Type=Application
#Icon=chrome-https___www.evernote.com_Home.action_login=true&targetUrl=%2FHome.action#st=p&n=808fd4e8-9ae8-4961-83eb-e339bde05f1c
Icon=/home/talha/Pictures/evernote_ico.png
Categories=Network;WebBrowser;
StartupNotify=true
StartupWMClass=www.evernote.com__Home.action

If anyone might have some idea how to fix this it would be much appreciated!

---

