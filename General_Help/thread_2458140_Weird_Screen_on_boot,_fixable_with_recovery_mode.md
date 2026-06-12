---
title: "Weird Screen on boot, fixable with recovery mode"
date: 2021-02-17
forum: General Help
---

### Post by dimensionobscura on 2021-02-17
Hello everyone,
I'm posting here to report a problem i've been having with Linux lately.
I used to have linux mint, and after an update, the following screen appears each and everytime i log into my laptop.
I've found out that i can work around it through recovery mode, but i can't keep doing it all the time.
I've tried reinstalling the distro, i even switched to another distro, Ubuntu Mate, yet the screen won't go.
I understand its a driver issue, yet i don't know how to fix it.
I'm not sure what kind of info would be relevant, so i'll leave it blank, yet i'll try to answer any question i can.
Thank you.
[IMG]https://i.stack.imgur.com/adHl6.jpg[/IMG]

---

### Post by Bashing-om on 2021-02-17
Hello dimensionobscura - Welcome to the forum.

Concur that this looks like a graphic's driver issue.
So, let's see what there is to work toward.
Post back:
```

lspci -k | grep -iEA5 'vga|3d'
sudo lshw -C display

```

[INDENT]a tale gets told
[/INDENT]

---

