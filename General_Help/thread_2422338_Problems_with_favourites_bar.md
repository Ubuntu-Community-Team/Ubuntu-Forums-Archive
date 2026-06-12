---
title: "Problems with favourites bar"
date: 2019-07-05
forum: General Help
---

### Post by redpoppet on 2019-07-05
Hi everybody
I have had this problem with a number of programs that I have just put up with until now.

With a couple of programs only (balena etcher and now the Brave Browser) I install it without problems, it shows up in the activities list of programs (gnome desktop) and they launch ok from there.  The problem is that when I add them to the favourites bar the icon appears but the program doesn't launch.  I have to launch the program by opening the activities up and launching from there. I have just installed onto machine with the same problem.  A problem with Brave in general?  

Is this is a fixable problem?  I have decided to use Brave now as my default browser so being able to launch it from the favourites bar is just convenient.

Many thanks to anybody who can help me with this.

RP

---

### Post by uRock on 2019-07-05
You may have to do what was mentioned in this post, [https://askubuntu.com/questions/1026528/adding-custom-programs-to-favourites-of-ubuntu-dock](https://askubuntu.com/questions/1026528/adding-custom-programs-to-favourites-of-ubuntu-dock)

---

### Post by redpoppet on 2019-07-05
Thanks for pointing me to that link.  I have no idea how to do any of what is asked there, but I will do my usual googling and see if I can conquer it.  I've got a lead and usually that's enough as I learn more about Linux each day.  I'm a recent windows refugee so the learning part of these things is great.

Thanks again.

---

### Post by uRock on 2019-07-05
If you want to give it a try, then here's the data you need in order to create the **.desktop** file. Everything bolded needs to be edited. Once you're done, then you can save it here, ***/usr/share/applications***, and it should be available to all users to place the application in the favorites. Place the file here, if you want it just for yourself, ***~/.local/share/applications*** .  Filename should look something like, **firefox-esr.desktop**

```
[Desktop Entry]
Name=**Firefox ESR**
GenericName=Web Browser
X-GNOME-FullName=**Firefox ESR Web Browser**
Exec=**/usr/lib/firefox-esr/firefox-esr %u**
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=**firefox-esr**
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;
StartupWMClass=**Firefox-esr**
StartupNotify=true
```

---

### Post by redpoppet on 2019-07-05
That's mighty kind of you to help me out like that.  I'll give it a go.

Thanks.

---

