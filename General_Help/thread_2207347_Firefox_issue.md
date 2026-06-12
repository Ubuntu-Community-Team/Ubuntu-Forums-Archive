---
title: "Firefox issue"
date: 2014-02-23
forum: General Help
---

### Post by mulldog on 2014-02-23
My very first post but I have a problem. I hope someone can help? I have the latest version of Ubuntu installed however when I attempt to open a second firefox page Ubuntu completely freezes up, my PC starts making whirling & clicking noises and no commands will work. The only way I can exit my PC is turning off the power.

This problem open appears to arise when a second firefox page is opened but when I simply use one everything is fine. I would like to have the ability to have multi-windows open however. How can I fix this please?

---

### Post by fdrake on 2014-02-23
can you tells more about your system (computer cpu/memory?)
also press "ctrl"+"alt"+"t" (o just run the terminal program)  and type (copy paste) this commands:
```
uname -a
firefox -v
dmesg | grep firefox

```
copy and paste here your outputs.

after that try this:
```

sudo apt-get --purge remove firefox
sudo apt-get install firefox
sudo apt-get upgrade && sudo apt-get update

```
try to run firefox again with multiple tabs/winds

---

### Post by mulldog on 2014-02-23
Thanks for helping. I tried all those things and Firefox still kept crashing on a second page. I have removed it and opted for Chromium which works like a dream (so far). :P

---

