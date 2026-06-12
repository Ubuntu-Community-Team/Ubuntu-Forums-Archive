---
title: "Power Button behaviour"
date: 2005-06-03
forum: General Help
---

### Post by Schaap on 2005-06-03
I would like to modify the default power button behaviour so that it asks confirmation before shutting down.
Reason for this is that it has, repeatedly, happened to me that I accidently pressed the power button and the entire system would shut down.

I realise that I could edit the /etc/acpi/powerbtn.sh script, yet my knowledge fails me in that sort of scripting area.. some help would be appreciated :)

---

### Post by 23meg on 2005-06-03
you'd have to add something like this

```
echo "Are you sure you want to shut down?"
read -n 1 conf
if [ $conf = y ]; then
    echo "Shutting down..."
else 
    echo "Shutdown aborted..."
fi
```

---

### Post by dave9191 on 2005-06-03
If you are running KDE or kubuntu you can put 'dcop kdesktop default logout' into the powerbtn.sh file to bring up the logout/shutdown dialog. 

Dave

---

### Post by Schaap on 2005-06-03
[QUOTE=dave9191]If you are running KDE or kubuntu you can put 'dcop kdesktop default logout' into the powerbtn.sh file to bring up the logout/shutdown dialog. 

Dave[/QUOTE]
 How about Gnome ?

---

### Post by dave9191 on 2005-06-03
I only used gnome for a short while so Im not 100% sure. But Im not aware of a dcop equivlant on gnome. So I have no idea. Sry 

Dave

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=Schaap]How about Gnome ?[/QUOTE]
 ```
gnome-session-save --kill
```

---

### Post by Schaap on 2005-06-05
Thanks, will try it as soon as I boot back into linux again :)

---

