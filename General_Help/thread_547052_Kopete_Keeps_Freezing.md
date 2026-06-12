---
title: "Kopete Keeps Freezing"
date: 2007-09-09
forum: General Help
---

### Post by snick512 on 2007-09-09
I had left running kopete running all night.. then a friend came over and said it wasn't responding / "frooze"

it did the same to me. (So im using Gaim right now)


I've tryed reinstalling it and killing the process while kopete is running, but nothing

Is there anyway to fix this?

---

### Post by por100pre1 on 2007-09-09
Try not to connect automatically to any account at Kopete startup, that worked for me.

Hope this helps. :)

---

### Post by snick512 on 2007-09-09
I have .... it freezes upon start-up

---

### Post by por100pre1 on 2007-09-09
```
pkill kopete
```

```
kedit /home/your-user-name/.kde/share/config/kopeterc
```

if using Gnome use this:

```
gedit /home/your-user-name/.kde/share/config/kopeterc
```

(replace your-user-name with your actual user name)

Look for [General] then find AutoConnect=true

change true to false.

Save and restart Kopete

Hope this helps. :)

---

### Post by snick512 on 2007-09-09
```

[General]
AutoConnect=false
EventIfActive=true
ReconnectOnDisconnect=true

```

still nothing

Mmmhmm lol. what now?

---

### Post by por100pre1 on 2007-09-09
No more ideas here, sorry. :(

Maybe somebody else will come with another idea.

---

