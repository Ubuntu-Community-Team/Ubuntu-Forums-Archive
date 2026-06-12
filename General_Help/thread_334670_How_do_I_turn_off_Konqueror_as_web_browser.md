---
title: "How do I turn off Konqueror as web browser"
date: 2007-01-09
forum: General Help
---

### Post by mastergunner on 2007-01-09
I have Thunderbird email and Firefox 2.0 as a web browser. I have Kubuntu 6.06. When I click on a link in an email it opens Konqueror. I would like it to open Firefox. How can I either turn Konqueror off as a web browser or tell Thunderbird to use Firefox as my web browser. Thanks for the help.

---

### Post by kebes on 2007-01-09
> **mastergunner said:**
> I have Thunderbird email and Firefox 2.0 as a web browser. I have Kubuntu 6.06. When I click on a link in an email it opens Konqueror. I would like it to open Firefox. How can I either turn Konqueror off as a web browser or tell Thunderbird to use Firefox as my web browser. Thanks for the help.

K Menu (bottom left) > System Settings > KDE Components > Default Applications

You can change the default apps for email, web browsing, etc.

---

### Post by kebes on 2007-01-09
If the above doesn't work, try right-clicking on an HTML file, and selecting "Open with > Other" then select firefox and click "Remember this association."

---

### Post by mastergunner on 2007-01-09
Well thanks guys but I cant find the Firefox executable file. I am new to Linux so I am still lost. I went to default applications but couldn't find the executable to set up my default browser. I did set up my default email which was easy to find and do. I downloaded and installed the new version of firefox and it was a pain so I have a shortcut to fiefox on my desktop.

---

### Post by kebes on 2007-01-09
If you installed Firefox with Synaptic, then it's probably located at:
/usr/bin/firefox

If you want to find out where a program is located, go to a [terminal]("http://psychocats.net/ubuntu/terminal"), and type:
which firefox

(or "which programname" in general) This tells you where the program executable can be found. (In a more general case, you can use "locate" and "find" on the commandline to find any file, but "which" is especially useful for executables.)

I hope that helps.

---

### Post by thelocust on 2007-01-21
[B]close firefox and thunderbird 

open ~/.mozilla-thunderbird/<profile>.default/prefs.js

and add 

[/B]```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```[B]

and that should do it.

be sure to do this in all your profile folders, they are 8 digits long consisting of letters and numbers and have .default at the end. 8)[/B]

---

