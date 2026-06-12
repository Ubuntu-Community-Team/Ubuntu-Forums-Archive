---
title: "Setting folder icon recursivly via bash script"
date: 2017-05-28
forum: General Help
---

### Post by arthur26 on 2017-05-28
Hello I would like to change all of my music folder icons via a bash  script. a few years ago I found a one line solution but have since  forgot it and cannot find it online.
  I can set the icon like this

  ```
gvfs-set-attribute -t string /home/arthur/Music metadata::custom-icon file:///home/arthur/Graphics/Revenant/Music.png
```

I managed to get one folder deep with this

```
for i in /home/arthur/Music/*; do
    gvfs-set-attribute -t string "$i" metadata::custom-icon file:///home/arthur/Graphics/Revenant/Music.png
done
``` 

 I cannot however figure out how to recursivly set all of Music's  subfolders to the same Icon. If anyone can help me out it would be much  appreciated.

  Using Linux Mint 18.1 Mate

---

### Post by &amp;KyT$0P# on 2017-05-28
Try -
```
find /home/arthur/Music -type d -exec gvfs-set-attribute -t string {} metadata::custom-icon file:///home/arthur/Graphics/Revenant/Music.png \;
```

**I have not tested that command**, so run this first to make sure it'll do what you want -
```
find /home/arthur/Music -type d
```

Refer to [FONT=Courier New]man find[/FONT] for more info

---

### Post by arthur26 on 2017-05-28
That works perfectly, thank you

---

### Post by &amp;KyT$0P# on 2017-05-28
You're welcome. :KS

---

