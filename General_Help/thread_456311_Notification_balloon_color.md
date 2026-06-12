---
title: "Notification balloon color"
date: 2007-05-27
forum: General Help
---

### Post by Prism on 2007-05-27
Hi there,

I switched my theme lately to a milky colored theme. It looks very nice IMHO, but when a program uses the notification daemon (for example, a media player or Ubuntu's updates are available message), the balloon message brought up uses Ubuntu's yellow-brown (#DCDCA0) color for the balloon border and left size.

I attach a screenshot.

Which place controls this color? I looked in the theme folder in ~/.themes, but it doesn't contain this color. Any other ideas?

---

### Post by drs305 on 2007-05-27
```
gconf-editor
```

/apps/notification-daemon/theme

This is a string entry, so you would need the name of the new theme you want to use for this entry. The default is ubuntu

If you wanted to enter it in terminal and know the theme name you want to use, the command would be:

```
gconftool-2 --type string --set /apps/notification-daemon/theme 'enter_theme_here' 
```

---

### Post by Prism on 2007-05-27
Thanks, that did it. Although I'm pretty sure it's not a very good behaviour. :)

---

