---
title: "Pipelight(silverlight) and DRM access"
date: 2015-08-02
forum: General Help
---

### Post by haitem-belgacem on 2015-08-02
Hello to everyone,

since some days j'm trying to see a movie on a VOD website
i have 48h to see the movie before the location limit and the video don't work

Silverlight is the used system for DRM reasons, i make a diagnosis and this is my differents tries :


[LIST]
[*]installation of pipelight (silverlight and flash). the player silverlight works but the loading of the video turn indefinitely. the timer stay in 00:00:00/00:00:00. the installation of "user agent override" doesn't make change.
[/LIST]


[LIST]
[*]The use of firefox via wine. impossible to install silverlight executable
[/LIST]


[LIST]
[*]The use of a virtual machine (virtualbox Win 7). Same result of the first try, the player silverlight works but the loading of the video turn indefinitely.
[/LIST]


[LIST]
[*]i try to play the video on a native windows 7, the player silverlight works and a silverlight window appear ans ask me to accept a DRM from microsoft server.
[/LIST]

my conclusions is, the special DRM window appear only on a native windows and doesn't appera on a virtual windows.
i think so there are a network blocking on linux to microsoft server.

I have disabled the firewall ubuntu, but nothing works.

If someone have a runway to fix this problem? or if there are logs to see more informations?

Thank you for your help.

---

### Post by yancek on 2015-08-02
Did you use the instructions at the site below?  If not, what did you use?  

[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

---

### Post by haitem-belgacem on 2015-08-02
Yes i used this iinstructions to install silverlight.
the plugin work on websites who don't use specific DRM.

in my diagnosis i reveal the same problem on virtual machine windows 7.

---

### Post by sgian on 2015-08-02
It depends on the site you are trying to use.

Netflix works with Chrome on Ubuntu, nothing else needed.

Amazon Prime works with Firefox on Ubuntu if you install HAL.

There might be other sites that have workarounds, but I don't know what site you are trying to access.

---

### Post by haitem-belgacem on 2015-08-03
I'm tring to use mytf1VOD.fr (french website)
the question  is, why the virtual machine get the same blocking?

---

### Post by haitem-belgacem on 2015-08-03
The website tell me that

> [COLOR=#000000][FONT=Arial]**Your operating system or your web browser is incompatible.**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]_Explication :_ 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The VOD is possible on OS environnements like Mac OS Intel, Windows 8, 7, Vista or XP with the browser internet explorer, firefox, chrome and safari. The videos editors require that the downloaded files are protected with DRM (Digital Right Management), numeric locks, developed by Microsoft who need the « Silverlight » plugin of Microsoft. [/FONT][/COLOR]We apologize us[COLOR=#000000][FONT=Arial] to not can use our VOD service.[/FONT][/COLOR]

---

### Post by bapoumba on 2015-08-03
Most probably this :
[https://bugs.launchpad.net/pipelight/+bug/1235918](https://bugs.launchpad.net/pipelight/+bug/1235918)
[https://bugs.launchpad.net/pipelight/+bug/1243655](https://bugs.launchpad.net/pipelight/+bug/1243655)

If I understand correctly, the video drivers have to be signed by Microsoft..

---

### Post by haitem-belgacem on 2015-08-03
Yeah, after some read time, i found some persons who have the same problem.
but, i don't find an issue to resolve it.

---

### Post by haitem-belgacem on 2015-08-03
Yeah my problem is solved

The problem is the new silverlight 5.1 need to verify the graphic card driver. if it is not sined by microsoft, the VOD doesn't play (error 6030)

The solution it is simply installing pipelight ([http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html))
and enable silverlight 4.0
[COLOR=#000000][FONT=monospace]sudo pipelight-plugin --enable silverlight4.0

if the plugin doesn't appear on firefox, execute this command line
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sudo pipelight-plugin --create-mozilla-plugins

and voila, the problem is solved.

User agent is not necessary.

But i don't testing the silverlight 5.0.

Thank all for your help.[/FONT][/COLOR]

---

