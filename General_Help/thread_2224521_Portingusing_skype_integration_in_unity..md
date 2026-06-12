---
title: "Porting/using skype integration in unity."
date: 2014-05-16
forum: General Help
---

### Post by piotrknetka on 2014-05-16
Is there any way to use this:
[https://extensions.gnome.org/extension/696/skype-integration/](https://extensions.gnome.org/extension/696/skype-integration/)
extension in unity? Basically I am mostly interested in white icon in system tray. Or is there any other option to have white skype incon in system tray?

---

### Post by kostkon on 2014-05-18
Two options for you:

Install sni-qt, i.e.
```
sudo apt-get install sni-qt:i386
```
to get the Skype icon back in the tray.

Or, use [skype-wrapper]("https://launchpad.net/~skype-wrapper/+archive/ppa") that will integrate Skype into the messaging menu and will look like this:
[ATTACH=CONFIG]253261[/ATTACH]

Restart Skype after doing one of the above.

Hope that helps.

---

### Post by piotrknetka on 2014-05-18
Thank you for the replay :), but unfortunately both of these ideas are useless for me because i want to have WHITE icon instead of classic green skype icon.

---

