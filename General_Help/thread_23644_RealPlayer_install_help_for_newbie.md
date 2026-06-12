---
title: "RealPlayer install help for newbie"
date: 2005-04-03
forum: General Help
---

### Post by Chemroydal Tissue on 2005-04-03
This is my first Linux distro, and I'm having trouble installing RealPlayer 10. Any advice would be helpful, as this is only the third 3rd party application I've installed.

---

### Post by pieter hollenberg on 2005-04-03
what is your trouble exactly ?

did you read this article ?

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

i will copy it for you

9.3 Real Player

Realplayer is good for listening to BBC Radio, among otherthings. You are required to manually download Realplayer from here. Once it is downloaded, move it to your home folder (if its not there already), then open up a terminal and type

 chmod u+x RealPlayer10GOLD.bin       
 sudo ./RealPlayer10GOLD.bin

You are then prompted for an installation directory. I chose

 /opt/realplayer

Answer yes to creating symbolic links, and let it use the default directory.

Realplayer should now be in your Gnome menu, under the Sound&Video section. 

this helped for me !

---

### Post by Lustiger Lurch on 2005-04-03
[http://www.elyps.de/guide.html#realplayer](http://www.elyps.de/guide.html#realplayer)

the important part is in english, so don't mind the .de  ;)

---

### Post by Riverside on 2005-04-04
[QUOTE=pieter hollenberg]what is your trouble exactly ?

did you read this article ?

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

i will copy it for you

9.3 Real Player

Realplayer is good for listening to BBC Radio, among otherthings. You are required to manually download Realplayer from here. Once it is downloaded, move it to your home folder (if its not there already), then open up a terminal and type

 chmod u+x RealPlayer10GOLD.bin       
 sudo ./RealPlayer10GOLD.bin

You are then prompted for an installation directory. I chose

 /opt/realplayer

Answer yes to creating symbolic links, and let it use the default directory.

Realplayer should now be in your Gnome menu, under the Sound&Video section. 

this helped for me ![/QUOTE]Except that whilst this installs Real Player on the system, the information is incomplete in that the installed Real Player is not actually functional (on Hoary, at least).

What is needed is to do, in the Gnome desktop view:

System | Preferences | Sound | General | uncheck "Enable sound server startup"

...and then Real Player will function (system sounds will no longer work though, so if sounds when Gnome starts etc are required, this is an issue).

In addition, for personal preference, I also did:

cd /opt realplayer
sudo chown root -R *
sudo chgrp root -R *

---

### Post by Chemroydal Tissue on 2005-04-04
[QUOTE=Riverside]Except that whilst this installs Real Player on the system, the information is incomplete in that the installed Real Player is not actually functional (on Hoary, at least).

What is needed is to do, in the Gnome desktop view:

System | Preferences | Sound | General | uncheck "Enable sound server startup"

...and then Real Player will function (system sounds will no longer work though, so if sounds when Gnome starts etc are required, this is an issue).

In addition, for personal preference, I also did:

cd /opt realplayer
sudo chown root -R *
sudo chgrp root -R *[/QUOTE]

Thanks, RP is running fine. Nicht eine Problem war das Deutsch gewesen. Gut kann ich Deutsch.

---

