---
title: "Matlab 2014b Launcher not &quot;locking&quot;"
date: 2014-10-26
forum: General Help
---

### Post by w-silva32 on 2014-10-26
Thought I would post my solution here since many people will want to lock their Matlab shortcut (installed via matlab-support) to their launcher.

Just upgraded to MATLAB 2014b and Ubuntu 14.10 (64bit). After installing Matlab and matlab-support, I wasn't able to lock the Matlab Launcher icon to my launcher. I would select "Lock to Launcher"  but nothing would happen and the Matlab icon would disappear after the application closed. I was able to fix it by pointing the .desktop file to the actual matlab binary instead of the shortcut in /usr/local/bin.

Steps to fix:

1. Make sure Matlab is closed
2. Open a terminal (Ctrl+alt+t)
3. Open the matlab .desktop file in gedit with sudo permissions ```
sudo gedit /usr/share/applications/matlab.desktop
```
4. Edit "Exec" line to point to your Matlab installed binary with a "-desktop" flag. For example, my Matlab 2014b install location (default): /usr/local/MATLAB/R2014b/bin/matlab -desktop

So your .desktop file might looks something like this:

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/usr/local/MATLAB/R2014b/bin/matlab -desktop
Name=MATLAB 2014b
Icon=/usr/share/icons/hicolor/48x48/apps/matlab.png
Categories=Development;Math;Science
Comment=Scientific computing environment
StartupNotify=true
StartupWMClass=com-mathworks-util-PostVMInit

```

5. Save the file and close gedit
6. Launch Matlab from unity and right-click the icon in the launcher, select "Lock to Launcher"

That should do it!

Hope this helps somebody else.
Will

---

