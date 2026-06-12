---
title: "Network widget gone..."
date: 2008-04-02
forum: General Help
---

### Post by Blice on 2008-04-02
I accidentally removed my network widget; The one where you can right click and do manual configuration and do wireless networks with and stuff. I looked in the 'Add to panel" dialog and all I saw was the network monitor widget. I also asked in the IRC room a couple times and didn't get any answers.


Anyone?

---

### Post by Crafty Kisses on 2008-04-02
> **Blice said:**
> I accidentally removed my network widget; The one where you can right click and do manual configuration and do wireless networks with and stuff. I looked in the 'Add to panel" dialog and all I saw was the network monitor widget. I also asked in the IRC room a couple times and didn't get any answers.


Anyone?

Did you get the Widget from gDesklettes?

---

### Post by Blice on 2008-04-02
> **Codename said:**
> Did you get the Widget from gDesklettes?

Er... Dunno? It came with Ubuntu..

---

### Post by Iowan on 2008-04-02
Right-clicking on About yields **nm-applet 0.6.5**
[http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")
Unfortunately, that doesn't help you get the icon back.

I discovered a checkbox under System>Preferences>Sessions for Network Manager applet - see if yours got unchecked.

---

### Post by retrow on 2008-04-02
You could try adding that in session:

System >> Preferences >> Sessions >> Startup Programs >> Add

Type in *nm-applet* in the command window and whatever description you want to give it. When you restart, the applet should be in its old place.

On second thought, just restarting too should do the trick, but I'm not sure.

---

