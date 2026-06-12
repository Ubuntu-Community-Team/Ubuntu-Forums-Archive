---
title: "Unknown Startup Problem"
date: 2007-08-26
forum: General Help
---

### Post by nx0 on 2007-08-26
After I log in to Ubuntu, my windows have no borders or close/maximize/minimize buttons, and I can't move them.

This used to only happen when I ran Beryl/Compiz, but now it happens at startup.

If I open my terminal it isn't whited out like it is in Beryl, so it makes me think its a problem with Compiz.

If I try to change the environment back to metacity (the only one that seems to work) Ubuntu freezes and I have to manually shut it down.

If the problem is Compiz loading at startup, how can I check and fix this problem?

---

### Post by nqsonk9 on 2007-08-26
First make sure that the installation of your Beryl / Compiz is absolutely fine (dont forget to install emerald-themes then). The last time I had the same problem, i simply restart X (Ctrl-Alt-Backspace) or reload window decoration (an option in Beryl manager)

And i hope this will do a little help with starting Beryl automatically:

[COLOR="DarkRed"]sudo gedit /usr/bin/startberyl.sh[/COLOR]
code:
[COLOR="DarkRed"]#!/bin/sh
beryl-manager
sleep 4
exec gnome-session[/COLOR]

[COLOR="DarkRed"]
sudo chmod a+x /usr/bin/startberyl.sh
sudo gedit /usr/share/xsessions/Beryl.desktop[/COLOR]
code:[COLOR="DarkRed"]
[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application[/COLOR]


BTW. Beryl doesnt work properly for every system and graphic card :'(

---

### Post by nx0 on 2007-08-26
Thanks for the info.

I tried what you suggested, and it seems Beryl isn't the problem on startup.

So I'm guessing its Compiz, since thats the only other environment I have installed.

---

### Post by nx0 on 2007-08-26
Bump?

---

