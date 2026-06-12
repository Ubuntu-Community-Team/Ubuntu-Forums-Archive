---
title: "skyforlinux not showing in unity indicator"
date: 2017-05-22
forum: General Help
---

### Post by d.atanasov on 2017-05-22
Hello everybody, 

After many days spend with the skype:i386 I decided to give a try to skypeforlinux 5.2.0.1 version. Everything seems fine but its not displayed in the indicator when I try to minimize it or close it. 
I have sni-qt, libappindicator1 installed. I have tried to add it manually to messages using dconf-editor, however this did not worked as well. I am using Ubuntu 17.04 and will be glad if someone has further ideas on the subject. 

Best, 

Dinko

---

### Post by howefield on 2017-05-22
Try opening Skypeforlinux with..

```
env XDG_CURRENT_DESKTOP=Unity skypeforlinux
```

If the Skype icon appears in the panel you could change the EXEC= line in the skype .desktop file to look like

```
Exec=env XDG_CURRENT_DESKTOP=Unity /usr/bin/skypeforlinux %U
```

it should mean that the panel icon will apear all the time, not sure if a new desktop file is written when the application is updated though, you might need to check that.

---

### Post by kostkon on 2017-05-22
Latest Skype is a multiplatform electron-based app (basically, a glorified web app) and it does not have indicator support and I doubt it will ever get one.

---

### Post by d.atanasov on 2017-05-22
Great it works. If the panel icon appears all the time I will simply create a shell script to set the env variable before actually running the application. Thanks a lot.

---

### Post by d.atanasov on 2017-05-22
> **kostkon said:**
> Latest Skype is a multiplatform electron-based app (basically, a glorified web app) and it does not have indicator support and I doubt it will ever get one.

Well maybe its not so bad to have a multi-platform application. Maybe if number of request are filed to the skype team they might reconsider it :)

---

### Post by howefield on 2017-05-23
> **d.atanasov said:**
> Great it works. If the panel icon appears all the time I will simply create a shell script to set the env variable before actually running the application. Thanks a lot.

Cool, you shouldn't need a script, just change the EXEC line in the /usr/share/applications/skypeforlinux.desktop file as above.

---

