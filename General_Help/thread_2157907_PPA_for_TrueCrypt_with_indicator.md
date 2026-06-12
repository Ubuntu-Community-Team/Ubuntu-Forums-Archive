---
title: "PPA for TrueCrypt with indicator"
date: 2013-06-27
forum: General Help
---

### Post by recover89 on 2013-06-27
Hello everyone.

I've made a PPA for a modified version of TrueCrypt that I've made, that replaces the normal tray icon with an app indicator. This is necessary in recent Ubuntu versions since the whitelist is no longer available.

I have only tested it for 13.04, but I made it available for 12.10 too, can someone please test 12.10?

```
sudo add-apt-repository ppa:stefansundin/truecrypt
sudo apt-get update
sudo apt-get install truecrypt
```

To automatically grant TrueCrypt sudo powers, use "[FONT=Courier New]sudo visudo[/FONT]" and add this (important: add it to the end of the file!):
```
your_username ALL=(ALL) NOPASSWD:/usr/bin/truecrypt
```

If you're wondering why TrueCrypt exits when you hide it, go to Preferences » Background Task and uncheck "Exit when there are no mounted volumes". I'm thinking of changing the default setting for this.

Hope this helps some people. This is my first package, so all feedback is appreciated.

---

### Post by tetralectic on 2013-08-09
This is great. The lack of a Truecrypt indicator was my biggest peeve when the Unity systray whitelist was discontinued. Many, many thanks. Any chance of a monochrome appindicator icon?

---

### Post by recover89 on 2013-08-09
You can modify the icon located at /usr/share/pixmaps/truecrypt-indicator.xpm (if I remember correctly).

---

### Post by meilin on 2013-08-09
Nice work! I have made a post on [my blog]("http://ubuntuhandbook.org/index.php/2013/08/install-truecrypt-with-indicator-ubuntu-1304/").

---

