---
title: "How do you remove AIGLX"
date: 2007-04-08
forum: General Help
---

### Post by hec1979 on 2007-04-08
Does anyone know how to remove AIGLX after you have gotten it with the
 sudo apt-get update command and have issued sudo apt-get dist-upgraded. Im really not sure how it work is there a command for me to check if it is installed

---

### Post by desheikh on 2007-04-08
Ubuntu edgy onwards come with AIGLX enabled by default, you dont need to worry about this unless your using XGL.

To disable AIGLX you can add the following lines at the end of your xorg.conf file:

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

---

