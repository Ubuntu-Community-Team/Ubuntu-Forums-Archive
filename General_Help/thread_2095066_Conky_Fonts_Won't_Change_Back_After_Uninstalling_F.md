---
title: "Conky Fonts Won't Change Back After Uninstalling Fluxbox"
date: 2012-12-15
forum: General Help
---

### Post by Nosophorus on 2012-12-15
Hello!

I'm using Ubuntu 12.04 (Precise Pangolin) with the MATE Desktop Environment and I installed Fluxbox to try it out and I got disappointed from what I saw. Then, I uninstalled it using this command:

```
sudo apt-get autoremove --purge fluxbox
```

Then I did:

```
rm -r ~/.fluxbox
```

The only thing I did while experimenting with Fluxbox was to change the default font. I followed [these instructions]("http://fluxbox-wiki.org/index.php?title=Style_overlay") and edited my "~/.fluxbox/init" and "~/.fluxbox/overlay" files. I did this to those two files:

For the "~/.fluxbox/init" file I did this:

```
session.styleOverlay: ~/.fluxbox/overlay
```

For the "~/.fluxbox/overlay" file I did this:

```
menu.title.font: sans-10:bold
toolbar.clock.font: sans-10:bold
toolbar.workspace.font: sans-10:bold
*font: sans-8
```

The problem is that, right now, my conky fonts look like they were taken from some Windows 3.0 app!

On my laptop I have the same "conky.conf" file that I use on my desktop and I copied it from my laptop and replaced that one on my desktop, but the problem has not been solved and the conky fonts still are crappy.

Any help would be deeply appreciated.

Thank You!

---

### Post by Habitual on 2012-12-15
```
grep -i font /path/to/your/conky.conf
```

---

