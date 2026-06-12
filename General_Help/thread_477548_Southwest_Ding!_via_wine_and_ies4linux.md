---
title: "Southwest Ding! via wine and ies4linux"
date: 2007-06-18
forum: General Help
---

### Post by hotspoons on 2007-06-18
I got an e-mail from a forum user who wanted to know how to get Southwest Ding! working with wine. If you don't know, Ding! is an application that receives special airfares and offers to frequent fliers of Southwest...a lot of times getting you roundtrip tickets anywhere in the US for less than $100. So it is a useful tool if you fly a lot, but is only available for Mac and PC. But it works great with Wine, if you have ie6 installed through the ies4linux script and write a little script. So here's how you get it working:

[LIST=1]
[*]Install wine (enable universe, apt-get install wine)
[*]Download the[ ies4linux script]("http://www.tatanka.com.br/ies4linux/page/Installation"), run default install for ie6
[*]Download [Ding!]("http://southwest.com/cgi-bin/systray?action=download&refId=2006050000000051&ref=ding_info") to your desktop
[*]Open up Internet Explorer 6 and in the address bar, type the following(replace *your unix username* with, well your unix username) and click go:*c:\windows\profiles\*your unix username*\Desktop*
[*]Double click on the Ding! icon, accept all of the defaults and install it.
[*]Create a bash script for launching Ding. You need to export the wine prefix you use for the IE6 install. It will be something like this:
```

#!/bin/bash
export WINEPREFIX="/home/*your UNIX username*/.ies4linux/ie6"
wine ~/.ies4linux/ie6/drive_c/Program\ Files/Southwest\ Airlines/Ding/Ding.exe

```
Again, replace **your UNIX username** with your username
[*]chmod +x to what ever file name you gave the script
[*]create a launcher for Ding! in your favorite desktop environment.

[/LIST]

---

### Post by PowerRanger on 2007-08-05
I needed to install this for the wife, your instructions worked perfectly.  Thanks!

Mike

---

### Post by bjhom on 2007-08-20
I get it to install, but when I go to register, I get
> 
A communication error has occurred.  Please check your internet connection and click "Retry" to attempt to connect.


Needless to say retrying doesn't work. Clicking on any of the icons to the right (ie Book Air, Book Car,...) brings up ie6 with the correct page.

Any ideas of what to do would be appreciated.

---

### Post by PowerRanger on 2007-08-23
Sorry, I can't be of much help.  It works on mine.  Are you using a proxy by any chance?

---

### Post by bone2006 on 2007-09-05
I'm having the same issue

---

### Post by cybergalvez on 2007-11-01
Thanks ! my wife just asked for Ding and this worked without any trouble - as advertised!

---

### Post by phosphoricx on 2008-01-03
Thanks for the great HOWTO! Worked like a charm.

---

### Post by cybergalvez on 2008-01-28
Is Ding still working for you? I just installed it today and when Ding starts it uses 100% of the CPU
Jose

> **hotspoons said:**
> I got an e-mail from a forum user who wanted to know how to get Southwest Ding! working with wine. If you don't know, Ding! is an application that receives special airfares and offers to frequent fliers of Southwest...a lot of times getting you roundtrip tickets anywhere in the US for less than $100. So it is a useful tool if you fly a lot, but is only available for Mac and PC. But it works great with Wine, if you have ie6 installed through the ies4linux script and write a little script. So here's how you get it working:

[LIST=1]
[*]Install wine (enable universe, apt-get install wine)
[*]Download the[ ies4linux script]("http://www.tatanka.com.br/ies4linux/page/Installation"), run default install for ie6
[*]Download [Ding!]("http://southwest.com/cgi-bin/systray?action=download&refId=2006050000000051&ref=ding_info") to your desktop
[*]Open up Internet Explorer 6 and in the address bar, type the following(replace *your unix username* with, well your unix username) and click go:*c:\windows\profiles\*your unix username*\Desktop*
[*]Double click on the Ding! icon, accept all of the defaults and install it.
[*]Create a bash script for launching Ding. You need to export the wine prefix you use for the IE6 install. It will be something like this:
```

#!/bin/bash
export WINEPREFIX="/home/*your UNIX username*/.ies4linux/ie6"
wine ~/.ies4linux/ie6/drive_c/Program\ Files/Southwest\ Airlines/Ding/Ding.exe

```
Again, replace **your UNIX username** with your username
[*]chmod +x to what ever file name you gave the script
[*]create a launcher for Ding! in your favorite desktop environment.

[/LIST]

---

### Post by bjhom on 2008-03-29
I installed Ding back in January and it worked great, but recently I too noticed it runs near 100% cpu. If anyone has found a way to fix this I'd appreciate any help. 

wine version 0.9.58 and 
ie6 version 6.0.2800.1106 
Ding Installer version 1.05

---

### Post by anfractuosities on 2008-05-14
I installed Ding on my parents computer, after install xubuntu edgy.  I used this method, and it works great, except when they click on a link to check the ticket specials, it opens ie but the browser remains blank....any idears?

---

