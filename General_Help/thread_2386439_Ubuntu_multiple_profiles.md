---
title: "Ubuntu multiple profiles"
date: 2018-03-06
forum: General Help
---

### Post by bizhat on 2018-03-06
I use 2 firefox profiles.  Here is my 2nd firefox profile shortcut

```

boby@hon-pc-01:~$ cat .local/share/applications/firefox-vpn.desktop 
[Desktop Entry]
Version=1.0
Name=Firefox VPN
Comment=Browse the World Wide Web
GenericName=Web Browser
Keywords=Internet;WWW;Browser;Web;Explorer
Exec=firefox -P vpn %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=go-home
Categories=GNOME;GTK;Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/chrome;video/webm;application/x-xpinstall;
StartupNotify=true
Actions=new-window;new-private-window;

[Desktop Action new-window]
Name=Open a New Window
Exec=firefox -P vpn -new-window

[Desktop Action new-private-window]
Name=Open a New Private Window
Exec=firefox -P vpn -private-window
boby@hon-pc-01:~$ 

```

I have a differnnt icon for this firefox.

The problem is when i start normal firefox, both get combined in unity bar, so  accessing the browser become little harder.

Is there a way i can keep them separate ?

I copied /usr/bin/firefox to /use/bin/firefox-vpn and update my shortcut "Exec" line, still both firefox get combined and show with one icon in unity bar. Any solution to keep them separate ?

---

### Post by kostkon on 2018-03-06
Probably, the only other way to make your DE see them as different apps, and not group them under the same icon, would be to try setting a custom WM_CLASS on the 2nd instance.

So, for starters, you could try using the default firefox executable (so that you won't have to maintain a second one) and changing the exec entry of your firefox-vpn.desktop to: 
```
Exec=firefox -P vpn %u --class=Firefox-VPN
```
The above will probably not work, so then use the second Firefox executable you've created, hopefully that will really start a 2nd instance of Fiirefox, and change the entry of your firefox-vpn.desktop, again, to:
```
Exec=firefox-vpn -P vpn %u --class=Firefox-VPN
```

Hope that helps.

---

### Post by bizhat on 2018-03-06
Thank you very much

```

Exec=firefox -P vpn %u --class=Firefox-VPN

```

This worked.

---

