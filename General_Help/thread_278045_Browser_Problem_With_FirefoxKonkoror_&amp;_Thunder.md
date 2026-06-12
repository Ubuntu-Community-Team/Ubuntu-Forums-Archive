---
title: "Browser Problem With Firefox/Konkoror &amp; Thunderbird"
date: 2006-10-15
forum: General Help
---

### Post by Craftycorner on 2006-10-15
My preferred email client is Thunderbird and my preferred email client is Firefox which I have secured nicely.  The hiccup is when I click a hyperlink in Thunderbird, Konqueror pops open and takes me to the website.  Please tell me how to get Firefox and Thunderbird to talk to each other.:-? 

Thanks
Crafty

---

### Post by thelocust on 2007-01-21
[B]close firefox and thunderbird 

open ~/.mozilla-thunderbird/<profile>.default/prefs.js

and add 

[/B]
[LEFT]```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```[/LEFT]
 
[B]
and that should do it.

be sure to do this in all your profile folders, they are 8 digits long consisting of letters and numbers and have .default at the end. :cool:[/B]

---

### Post by peterLinux on 2007-01-21
With Koquerer popping up I assume you have Kubuntu
A more elegant solution would be to go to 
System Settings
and on the top (Personal) click Default Applications

For e-mail pick
/usr/bin/mozilla-thunderbird

For www pick
/usr/bin/firefox

Peter

---

### Post by thelocust on 2007-01-22
**That doesn't work. 8)**

---

### Post by chip616 on 2008-07-01
theLocust:

> close firefox and thunderbird

open ~/.mozilla-thunderbird/<profile>.default/prefs.js

and add


Code:

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");



and that should do it.

be sure to do this in all your profile folders, they are 8 digits long consisting of letters and numbers and have .default at the end. 

OK, that worked.  However, for Firefox version 2 in Kubuntu 8.04, you have to change those two lines to read:

```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-2");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-2");
```

Thanks for the help -- even this far down the line!

Frank.

---

