---
title: "Acestream"
date: 2016-03-12
forum: General Help
---

### Post by Edward 000 on 2016-03-12
How can I install Acestream on Ubuntu 15.10? Thanks.

---

### Post by Bucky Ball on 2016-03-12
By having a quick look online for instructions and finding [this]("http://acestreamguide.com/linux/"). You would probably follow it verbatim, with the only change being to change 'raring' in the first command to whatever release you are using, for instance 'wily' for 15.10.

---

### Post by Fsirett on 2016-03-12
I had a quick look at something I thought I had seen in a KODI article. 

Apparently you can run it through Kodi, which makes all of this sort of thing much easier for me. I read that you can load Kodi from [https://kodi.tv/download/](https://kodi.tv/download/)
and if you download the SRP repository (*[http://srp.nu]("http://srp.nu.").*) part of it, from what I have read, includes AceStream within it. 

In my experience, I have found that anything done through Kodi is much easier than doing nearly any other way, but I am not the best at these things.

---

### Post by Edward 000 on 2016-03-17
Thank you guys for the reply :) I use Kodi too and yes it's easier :)

---

### Post by digl2 on 2016-03-20
[COLOR=#111111][FONT=Ubuntu]Hello, if you want just Acestream with Kodi, there is a solution.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Actually it seems that there are no more official repo for acestream
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, what I did is to install Acestream with Wine.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To install Wine, enter the following commands in your terminal):
[/FONT][/COLOR]

[LIST]
[*]sudo add-apt-repository ppa:ubuntu-wine/ppa
[*]sudo apt-get update
[*]sudo apt-get -y install wine1.8
[*]
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Or find more informations there: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) in order to install Wine
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then, find "Configure Wine" (probably in your "Start Menu") and find the tab "Applications" and change "Windows version" to "Windows XP".
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then browse your C: drive (shortcut is the Start Menu or browse /home/YOURNICKNAME/.wine/dosdevices/c:/ If you dont see the folder /.wine/ try to press Ctrl + H to see hidden folders) and copy/paste the Windows installer you downloaded from[http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en](http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Install the software.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The software is supposed to be installed in /home/YOURNICKNAME/.wine/dosdevices/c:/users/YOURNICKNAME/Application Data/ACEStream/player
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So just launch the file ace_player.exe to launch it. Maybe it is already launched in background. So close it and re-launch it.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After make a shortcut of the folder to your desktop. So go back to /home/YOURNICKNAME/.wine/dosdevices/c:/users/YOURNICKNAME/Application Data/ACEStream/ and select the folder /player/ . Then click on Ctrl + Shift and move the folder to your desktop to make it a shortcut.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And it works :)
[/FONT][/COLOR]

---

### Post by Edward 000 on 2016-04-03
> **digl2 said:**
> [COLOR=#111111][FONT=Ubuntu]Hello, if you want just Acestream with Kodi, there is a solution.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Actually it seems that there are no more official repo for acestream
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, what I did is to install Acestream with Wine.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]To install Wine, enter the following commands in your terminal):
[/FONT][/COLOR]

[LIST]
[*]sudo add-apt-repository ppa:ubuntu-wine/ppa
[*]sudo apt-get update
[*]sudo apt-get -y install wine1.8
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Or find more informations there: [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) in order to install Wine
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then, find "Configure Wine" (probably in your "Start Menu") and find the tab "Applications" and change "Windows version" to "Windows XP".
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then browse your C: drive (shortcut is the Start Menu or browse /home/YOURNICKNAME/.wine/dosdevices/c:/ If you dont see the folder /.wine/ try to press Ctrl + H to see hidden folders) and copy/paste the Windows installer you downloaded from[http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en](http://wiki.acestream.org/wiki/index.php/AceStream_3.0/en)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Install the software.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The software is supposed to be installed in /home/YOURNICKNAME/.wine/dosdevices/c:/users/YOURNICKNAME/Application Data/ACEStream/player
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So just launch the file ace_player.exe to launch it. Maybe it is already launched in background. So close it and re-launch it.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After make a shortcut of the folder to your desktop. So go back to /home/YOURNICKNAME/.wine/dosdevices/c:/users/YOURNICKNAME/Application Data/ACEStream/ and select the folder /player/ . Then click on Ctrl + Shift and move the folder to your desktop to make it a shortcut.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]And it works :)
[/FONT][/COLOR]

Thanks, I'll try it! :)

---

### Post by kmarks0201 on 2017-03-15
[HR][/HR]Came across this in a search... as much as I hate using Wine, the acestream guys don't really seem to committed to their Linux versions, and this works quite well.

---

