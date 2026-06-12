---
title: "I accidentally removed ubuntu.css file from /usr/share/gnome-shell/theme"
date: 2020-07-11
forum: General Help
---

### Post by dudev on 2020-07-11
I accidentally removed _**ubuntu.css**_ file from ***/usr/share/gnome-shell/theme*** path so can you send me this file please (or give me a link with solved question). I would appreciate it.

---

### Post by Dennis N on 2020-07-11
Are you sure of that location? I don't see a ubuntu.css file in there in Ubuntu 20.04:

```
dmn@Tyana-vm:/usr/share/gnome-shell/theme$ tree
.
&#9492;&#9472;&#9472; Yaru
    &#9492;&#9472;&#9472; gnome-shell-theme.gresource

1 directory, 1 file

```

There is another directory (Yaru) with one file inside. 
Yaru is the default theme.

---

### Post by monkeybrain20122 on 2020-07-11
Ubuntu.css is here /usr/share/gnome-shell/extensions/ubuntu-dock@ubuntu.com/ubuntu.css
so I suppose you can just reinstall the ubuntu-dock

---

### Post by deadflowr on 2020-07-12
Run
```
sudo apt install --reinstall gnome-shell-common
```
that's where the file comes from.
Only applies to Ubuntu releases older than 19.10.

Newer releases don't use that file.

---

### Post by ActionParsnip on 2020-07-12
Or restore from your backups. Do you backup your OS regularly?

---

