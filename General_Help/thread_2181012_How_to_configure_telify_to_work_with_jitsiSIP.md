---
title: "How to configure telify to work with jitsi/SIP"
date: 2013-10-15
forum: General Help
---

### Post by taxaza on 2013-10-15
[SIZE=3]**Create a handler for the SIP protocol that uses jitsi**[/SIZE]
Run in terminal:
```
sudo gedit /usr/share/applications/defaults.list
```
Add the following line at the end:
```
x-scheme-handler/sip=jitsi.desktop
```

[SIZE=3]**Fix jitsi.desktop to accept parameters (telephone url)**[/SIZE]
Run in terminal:
```
sudo gedit /usr/share/applications/jitsi.desktop
```
Change this line:
```
Exec=jitsi
```
To this:
```
Exec=jitsi %u
```

[SIZE=3]**Associate the SIP protocol**[/SIZE]
Run in terminal:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/sip/command '/usr/bin/jitsi sip:"%s"@sip.voip_provider_url.com'
```
where sip.voip_provider_url.com put the appropriate url for your SIP provider.

Then in terminal again:
```
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/sip/enabled true
gconftool-2 --set --type=bool /desktop/gnome/url-handlers/sip/need-terminal false
```

In Thunderbird/Firefox open the Telify preferences (Tools/Telify/Preferences) and set "Used Protocol" to sip:

Done!

---

