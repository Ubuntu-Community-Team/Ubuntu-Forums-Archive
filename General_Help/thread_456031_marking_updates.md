---
title: "marking updates"
date: 2007-05-27
forum: General Help
---

### Post by n_hendrick on 2007-05-27
Is there a way to mark a certain update so it doesn't install when I do an apt-get upgrade? There is just one package that I don't want upgraded because the upgraded package is broken on my system but the original works. Thanks is advance.

---

### Post by milton1 on 2007-05-27
upgrade through adept/synaptic and un-check the package you want left alone.

There is probably a way to do this in apt-get, but I don't know it. Obvious question: have you tried:

man apt-get

---

### Post by n_hendrick on 2007-05-27
yeah I've looked at the documentation but nothing about marking packages as static

---

### Post by milton1 on 2007-05-27
I just looked through the man entry myself. No joy. However, the gui approach will work. A bit slower, but it accomplishes what you are trying to do.

---

### Post by n_hendrick on 2007-05-27
I guess I'll just have to stick to the gui....bummer

---

### Post by bapoumba on 2007-05-27
In synaptic, highlight the package > Package > Lock version.

---

### Post by n_hendrick on 2007-05-27
thanks thats what I wanted to know

---

