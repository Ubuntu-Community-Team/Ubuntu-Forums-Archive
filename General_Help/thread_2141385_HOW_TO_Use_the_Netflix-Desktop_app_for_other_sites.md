---
title: "HOW TO: Use the Netflix-Desktop app for other sites"
date: 2013-05-02
forum: General Help
---

### Post by scottpledger on 2013-05-02
As much as I love finally being able to peruse and watch my Netflix account on Linux, there are a number of other sites which are heavily Silverlight-dependent, such as my local cable operator's online on-demand streaming service and, more recently (since Flash is no longer actively developed on Linux and Google has removed the DRM code from Flash) my Amazon Instant Prime videos.  Therefore, I set out on an epic quest to be able to use this great hack for other sites as well.  Here is the final log of my journey (aka step-by-step instructions for beginners):
[LIST=1]
[*]Set up a small script that you can use to run the special version of wine more easily.
[LIST=1]
[*]With your favorite editor, create the file "/usr/bin/wine-compholio" (as root) with the following contents:
```

#!/bin/bash


export WINEPREFIX="${HOME}/.wine-browser"


/opt/wine-compholio/bin/wine "$@"

```
[*]Then, make that file executable by running ```
sudo chmod +x /usr/bin/wine-compholio
```
[/LIST]

[*]Now, if you wish to have somewhat easier access to the modded Firefox, you can create a file on your desktop called "Mozilla Firefox.desktop" with the following contents:
```

[Desktop Entry]
Comment[en_US]=
Comment=
Exec=\swine-compholio "C:\\\\Program Files\\\\Mozilla Firefox\\\\firefox.exe" -profile "C:\\\\browser-profile"
GenericName[en_US]=
GenericName=
Icon=F0E6_firefox.0
MimeType=
Name=Mozilla Firefox
Path=~/.netflix-desktop/dosdevices/c:/Program Files/Mozilla Firefox
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=

```
[*]Using either the shortcut created above or the command below, execute your beautifully hacked version of Firefox ```
wine-compholio "C:\\Program Files\\Mozilla Firefox\\firefox.exe" -profile "C:\\browser-profile"
```
[*]Now, we have to make Firefox act like Firefox. Once that opens, press "Ctrl-l" to open the change URL box.  Type "about:config".  Accept the fact that you're "breaking your warranty".  Find the preference whose name is "browser.tabs.autoHide" and double click it to change its value to "false".
[*]This will show your tab bar.  Now you can right click on the empty space next to the tabs in the tab bar and check the "Menu Bar", "Navigation Bar", and (optionally) the "Add-on bar".
[*]Your Firefox is looking much more like what it should, but it isn't quite there yet.  For me, the white close circle in the upper right was rather obnoxious, so I removed it by going to "Tools > Addons", then under the "Extensions" pane, disable the "Fullscreen Close Plugin".  Restart your browser as prompted and ta-da! A beautifully hacked, multipurpose Firefox!
[/LIST]

This is my first HOW-TO here on ubuntuforums, so if you need any help with anything or have any comments/questions, let me know!  Thanks, and I hope this helps you as much as it helps me!

---

### Post by kgr132 on 2013-05-06
Thank you very much. I only followed steps 4, 5 & 6 just to mess with the Netflix environment. It's so nice to have it work in a normal "Netflix in a browser" way. It's also great to finally be rid of the "Fullscreen Close Plugin". That thing was really annoying. Great work.

---

