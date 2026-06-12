---
title: "GCC woes"
date: 2005-10-20
forum: General Help
---

### Post by schulermx on 2005-10-20
It appears that I don't have a preinstalled GCC command on my computer. I was pretty certain that most distributions had the gcc command out of the box.

Here is what I mean since what I wrote above probably doesn't make sense:

```
schulerm@box:~$ gcc
bash: gcc: command not found
schulerm@box:~$ man gcc
No manual entry for gcc

```

I checked Synaptic and I have gcc-4.0, gcc-4.0 base, gcc-doc all installed.
Is there something I'm missing or not doing here?

---

### Post by Jenda on 2005-10-20
Try ```
sudo apt-get install build-essential
```This should install all you need.

---

### Post by schulermx on 2005-10-20
[QUOTE=Jenda]Try ```
sudo apt-get install build-essential
```This should install all you need.[/QUOTE]

Ah, didn't notice that package.

Problem solved, thanks.

---

### Post by Jenda on 2005-10-20
You're welcome. I love it when it's this easy.

---

