---
title: "Unable to configure Furius Moon due to incorrect .ini config"
date: 2013-08-30
forum: General Help
---

### Post by owise1 on 2013-08-30
I had a problem with the Furius Moon screenlet - when launched it was not possible to configure or move the screenlet.  Looking at ~/.config/screenlets/FuriusMoon/default/FuriusMoon.ini I noted that skip_taskbar was set to True.  Changing this to false and restarting the screenlet allowed normal configuration.

opacity=1.0
scale=1.5
theme_name=southern hemisphere
is_sticky=False
keep_above=False
is_dragged=False
keep_below=True
y=32
x=1400
skip_taskbar=False

Posted just in case anyone else had this problem.

Fresh install of 13.04 on an intel NUC

cheers

Dave

---

