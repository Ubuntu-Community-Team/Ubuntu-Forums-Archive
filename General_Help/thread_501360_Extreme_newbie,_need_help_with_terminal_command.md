---
title: "Extreme newbie, need help with terminal command"
date: 2007-07-15
forum: General Help
---

### Post by Projectre on 2007-07-15
how do i install Adobe Flash Player? on terminal? i try to type  (  ./flashplayer-installer  ) on terminal, and nothing happen, what do i have to type, or do before typing   (  ./flashplayer-installer  )  ,cuz i can't get it to work. please help.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   **_4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s)._**
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by Rovdjur on 2007-07-15
> **Projectre said:**
> how do i install Adobe Flash Player? on terminal? i try to type  (  ./flashplayer-installer  ) on terminal, and nothing happen, what do i have to type, or do before typing   (  ./flashplayer-installer  )  ,cuz i can't get it to work. please help.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

   1.  Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   **_4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s)._**
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

First you need to extract the folder to a folder (just extract to the desktop for now), then once you see the folder on your desktop, in terminal type:

```
cd install_flash_player_9_linux
```

That will navigate you to the folder, then type the install command:

```
./flashplayer-installer
```

That should do it.

---

### Post by 505 on 2007-07-15
The file you have downloaded is not executable. This is to prevent dagerous programs to run that download themselves from the Internet.

To make is executable to, either:
right-click, choose properties, tab permission and select the execure mark. -or-
in the terminal, type 'chmod +x flashplayer-installer'
Then you can do ./flashplayer-installer to install it.

By the way, Flash is also available from the repositories. Just type 'sudo aptitude install flashplugin-nonfree'

---

