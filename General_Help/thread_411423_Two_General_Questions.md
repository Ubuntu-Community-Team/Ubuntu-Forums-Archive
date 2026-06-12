---
title: "Two General Questions"
date: 2007-04-16
forum: General Help
---

### Post by BostonBrother on 2007-04-16
When I suspend or hibernate my computer and bring it back up I loose my network connection on my ethernet card.  Is there a command that will re-establish a connection again, because right now I have been doing a restart to get it back up.

Second question is how do I change my preferred browser from konqueror to firefox.  If I click a link in other applications it always brings it up in Konqueror instead of firefox.  I've gone to the system setting and set the default application there for my browser to firefox, but none of the applications seem to be honoring this.  Have I forgotten something?

---

### Post by NeoLithium on 2007-04-16
1) You can open a terminal window and type ```
 sudo /etc/init.d/networking restart
```

2) I'm not sure about that. usually in the specific program where you click the links, will also have an option in their own settings for default browser, you might have to check in there.

Hope this helps a bit :)

---

