---
title: "Can't empty Garbage Bin"
date: 2006-11-07
forum: General Help
---

### Post by Abaddon on 2006-11-07
My Garbage Bin is filling up with all my various files, but when I right click on the Garbage bin in my panel, and select empty, nothing seems to happen.

I suspect it might be a permissions thing.

Where is the trash folder so I can delete them manually?

---

### Post by Ramses de Norre on 2006-11-07
```
sudo chown -R `whoami`:`whoami` ~/.Trash
rm -rf ~/.Trash/*
```

---

### Post by carla on 2006-11-10
> **Ramses de Norre said:**
> ```
sudo chown -R `whoami`:`whoami` ~/.Trash
rm -rf ~/.Trash/*
```

In Edgy, I received this response to the first command:

```
chown: cannot access `/home/carla/.Trash': No such file or directory
```

but I entered the second command anyhow, out of stubborn curiosity. :) I received another prompt in return, as if the command had been obeyed in the background...but it hadn't.

Any ideas? Thank you so much for your help!

---

### Post by carla on 2006-11-11
Okay, I just found success in Edgy:

```
rm -r $HOME/.local/share/Trash/*
```

---

### Post by Ramses de Norre on 2006-11-11
You are probably using kde then? It seems the location of thrash is different between the two.

---

### Post by carla on 2006-12-16
> **Ramses de Norre said:**
> You are probably using kde then? It seems the location of thrash is different between the two.

*nod* Yep, that's right. :)

---

### Post by nothingworks on 2008-05-17
lolz same thing happened with my new,updated Hardy Heron install.
this worked for me:

rm -rf  ~/.local/share/Trash/files/*

also mark the folder writable so you can empty the thrash in the future
sudo chmod 777 ~/.local/share/Trash/files



Cant believe this is broken. Hope this helps.

---

