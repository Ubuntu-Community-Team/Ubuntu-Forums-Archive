---
title: "Mouse over on top panel minimizes GRAH!!!"
date: 2008-06-18
forum: General Help
---

### Post by -Outcast- on 2008-06-18
Folks I changed something and I do not know what. Now every time I hover my mouse near the panels/toolbar the bloody window minimizes. A complete pain

Any idea?

---

### Post by Yuki_Nagato on 2008-06-18
Are you running GNOME, KDE, XFCE, or any other GUI environment?

Can you remember changing anything recently?  Poking around in any .conf files recently?

Anything at all that can help narrow down the search?

---

### Post by -Outcast- on 2008-06-18
yea, compiz I tried out for the cube. Started then. I unticked everything on it. even ran metacity --replace nothing. 

If I go to normal visual effects mode it stops. So it's something there. But I want to keep wooble effect. So I need it. I removed compiz did a reboot

Any ideas. Its driving me nuts!

---

### Post by -Outcast- on 2008-06-18
Thank crap, I found the solution on the compiz website

rm -rf ~/.config/compiz/compizconfig/* ~/.compizconfig/*
rm -rf ~/.kde*/share/apps/compizrc*
gconftool-2 --recursive-unset /apps/compiz /apps/compizconfig

Back to normal. That was a friggin nightmare, windows darting all over the place. 

Thanks for the reply

---

