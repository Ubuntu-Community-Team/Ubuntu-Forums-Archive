---
title: "so i guess LTSP is broken"
date: 2015-06-03
forum: General Help
---

### Post by vktr2000 on 2015-06-03
sorry but I cannot log in with the client, 
ion graphical mode, I can log in with text mode
only, create account, then exit and restart client,
but can only log in with text, not graphical.

how do I make graphical work?

---

### Post by ramesh24 on 2016-03-05
This may be happened due to graphic driver non compatibility. Add the following lines in lts.conf file. (/var/lib/tftpboot/ltsp/i386 or amd64/lts.conf)
[default]
 LDM_DIRECTX=true
 X_COLOUR_DEPTH=16
 
# Disable video acceleration
 X_OPTION_01="\"NoAccel\""
 X_OPTION_02="\"DRI\"\"off\""

---

### Post by ramesh24 on 2016-03-05
Post your client specifications, make and model. It would be helpful to understand your issues.

---

