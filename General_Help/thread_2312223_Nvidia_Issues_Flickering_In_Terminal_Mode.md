---
title: "Nvidia Issues: Flickering In Terminal Mode"
date: 2016-02-02
forum: General Help
---

### Post by shibby4555 on 2016-02-02
Ubuntu 14.04 on my Asus laptop, I had installed nvidia drivers from apt, I can't remember which version, (recommended or something). 
**[SIZE=1][FONT=arial]ASUS ROG G56JK-EB72 Gaming Laptop Intel Core  i7 4710HQ (2.50GHz) 12GB Memory 1TB HDD NVIDIA GeForce GTX 850M 2GB  GDDR3 15.6" Windows 8.1 64-Bit                 [/FONT][/SIZE]**

I'm extremely frustrated by this, I was perfectly fine with nouvea but needed some cuda.

This is turning out to be more frustrating than usual because when I drop into failsafe graphics mode, upon login the screen turns blank. I have to keep hitting CTRL ALT F{#} to refresh to screen just long enough to type most of a command. I've never experienced this before. 

Tried stopping the gdm service, and the screen permanently goes blank.

Tried to stop gdm using:
```

sudo /etc/init.d/gdm stop
79 Syntax Error: fi Unexpected } 

```

Weird. Its extraordinarily difficult to get much done, I can barely type in my password before I have to refresh. Has anyone come across this before? I've searched high and low and have not seen a similiar issue. Will try removing nvidia in meantime, but I've been getting into issues.

-------
EDIT: Solved this by purging nvidia, I must have made a typo when I tried earlier

---

