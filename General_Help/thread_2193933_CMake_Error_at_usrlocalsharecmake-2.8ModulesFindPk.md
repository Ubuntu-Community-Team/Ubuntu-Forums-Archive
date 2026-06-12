---
title: "CMake Error at /usr/local/share/cmake-2.8/Modules/FindPkgConfig.cmake"
date: 2013-12-15
forum: General Help
---

### Post by nameless10 on 2013-12-15
Hello forum-mates!
I was trying to install "cdemu" program. So I used the launchpad repositories, but when I tried to install from Terminal or Synaptic, it wasn't found. I checked the Software Sources, all was right and cdemu ppa was present there. ```
sudo apt-get install cdemu-daemonReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cdemu-daemon
```
Then I tried to compile this application - [http://cdemu.org/debian/](http://cdemu.org/debian/) and here are the sources: [http://cdemu.org/project/#download](http://cdemu.org/project/#download). I used the README and INSTALL file to know how do I install 'cdemu': [http://pastebin.com/m8iabYui](http://pastebin.com/m8iabYui). After I used '*ccmake ..*' command an error occurred - [http://pastebin.com/LPHAEEjz](http://pastebin.com/LPHAEEjz). I checked in [COLOR=#000000][FONT=Consolas]*/usr/local/share/cmake-2.8/Modules/* and the file "[/FONT][/COLOR][FONT=Consolas][COLOR=#000000]FindPkgConfig.cmake" is present.[/COLOR][/FONT]
[FONT=Consolas][COLOR=#000000]What I'm doing wrong or which dependencies aren't present?
Thank you for any helpful answer!
[my machine: Ubuntu 12.04 x86][/COLOR][/FONT]

---

### Post by wes-q on 2014-01-06
I have this exact problem! I am really confused and frustrated...

---

