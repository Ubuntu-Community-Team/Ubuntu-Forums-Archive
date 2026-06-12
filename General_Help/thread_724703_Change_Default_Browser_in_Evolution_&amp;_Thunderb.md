---
title: "Change Default Browser in Evolution &amp; Thunderbird?"
date: 2008-03-14
forum: General Help
---

### Post by OzzyFrank on 2008-03-14
Hi. I was just wondering if there was a way to change the default web browser from Firefox to Opera? I figured there would be in Preferences, but in both email clients there doesn't seem to be an option. Am I looking in the wrong place? Do I need to manually edit a config file? Or is there no way around this? Cheers

---

### Post by TransitMan on 2008-03-14
This is from my Thunderbird user.js file to control which browser gets opened:
```

#user_pref("network.protocol-handler.app.ftp","/usr/local/bin/swiftweasel");
#user_pref("network.protocol-handler.app.http","/usr/local/bin/swiftweasel");
#user_pref("network.protocol-handler.app.https","/usr/local/bin/swiftweasel");

user_pref("network.protocol-handler.app.ftp","/usr/bin/opera");
user_pref("network.protocol-handler.app.http","/usr/bin/opera");
user_pref("network.protocol-handler.app.https","/usr/bin/opera");

#user_pref("network.protocol-handler.app.ftp","/usr/bin/firefox");
#user_pref("network.protocol-handler.app.http","/usr/bin/firefox");
#user_pref("network.protocol-handler.app.https","/usr/bin/firefox");

#user_pref("network.protocol-handler.app.ftp","/home/user-name/navigator/navigator");
#user_pref("network.protocol-handler.app.http","/home/user-name/navigator/navigator");
#user_pref("network.protocol-handler.app.https","/home/user-name/navigator/navigator");

```

I do not have one for Evolution as I do not use that program, yet.

---

### Post by OzzyFrank on 2008-03-15
Thanks, but I did a search throughout the whole filesystem for user.js and there isn't one. Only found 2 in the "Documents and Settings" folder on my Windows drive, hehe! Do I have to create this and, if so ,where to (I assume to .mozilla-thunderbird)? Cheers

---

### Post by OzzyFrank on 2008-03-24
OK, I Googled for the answer and it is that [COLOR="Purple"]user.js[/COLOR] doesn't exist so has to be created from scratch. You can also install **ChromEdit Plus** to do this for you (it will then be at the bottom of the Tools menu):

[http://webdesigns.ms11.net/extensions/chromeditplus-2.7.2.xpi](http://webdesigns.ms11.net/extensions/chromeditplus-2.7.2.xpi)

For Firefox, you can just drag the file to the browser and it will install, but for Thunderbird you need to open **Tools > Add-ons** (making sure you are viewing all files not just *.jar themes). Then open ChromEdit +, go to the **user.js** tab, and paste in this code (for Opera... change the name for your preferred browser):

user_pref("network.protocol-handler.app.http", "/usr/bin/opera");
user_pref("network.protocol-handler.app.https", "/usr/bin/opera");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/opera");

---

### Post by Het Irv on 2008-03-24
If you change the Default browser in System->Prefrences->Perferred Applications, will that do what you want it to do?

---

### Post by OzzyFrank on 2008-03-24
No, Opera was already my default browser. Thunderbird doesn't give a crap what your default browser is, hehe! But it was fixed easily enough. Now to find out how to replicate this in Evolution! That program obviously doesn't care what the default browser is either, but chooses Ubuntu's original default browser (ie Firefox).

---

### Post by Ashex on 2008-07-04
> **OzzyFrank said:**
> OK, I Googled for the answer and it is that [COLOR="Purple"]user.js[/COLOR] doesn't exist so has to be created from scratch. You can also install **ChromEdit Plus** to do this for you (it will then be at the bottom of the Tools menu):

[http://webdesigns.ms11.net/extensions/chromeditplus-2.7.2.xpi](http://webdesigns.ms11.net/extensions/chromeditplus-2.7.2.xpi)

For Firefox, you can just drag the file to the browser and it will install, but for Thunderbird you need to open **Tools > Add-ons** (making sure you are viewing all files not just *.jar themes). Then open ChromEdit +, go to the **user.js** tab, and paste in this code (for Opera... change the name for your preferred browser):

user_pref("network.protocol-handler.app.http", "/usr/bin/opera");
user_pref("network.protocol-handler.app.https", "/usr/bin/opera");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/opera");


Just giving this thread a bump. Thunderbird has been using firefox which was pretty irritating. After going through this, it opens with opera :)

---

