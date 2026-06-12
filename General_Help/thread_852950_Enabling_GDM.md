---
title: "Enabling GDM"
date: 2008-07-08
forum: General Help
---

### Post by Jimbo13 on 2008-07-08
I'm using ubuntu as a media server and I turned GDM off can anyone tell me how to turn it back on from the terminal.

If you are confused about what I did this was the tutorial I was using, it neglected to mention how to re-enable GDM.

[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

---

### Post by aktiwers on 2008-07-08
Type:
```
startx
```or
```
/etc/init.d/gdm start
``` (dont remember if this needs a sudo, give it one if this fails).

Then go enable it again.

---

### Post by Rocket2DMn on 2008-07-08
```
sudo /etc/init.d/gdm start
```

---

### Post by jocko on 2008-07-08
Do what aktiwers and rocket2DMn said to start up gnome.
Once gnome is running just undo what you did in the first place; go to System --> Administration --> Services, and tick "Graphical Logic Manager (gdm)"

---

### Post by Jimbo13 on 2008-07-08
Thanks got it running with startx :guitar:

---

