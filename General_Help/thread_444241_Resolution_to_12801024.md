---
title: "Resolution to 1280*1024"
date: 2007-05-15
forum: General Help
---

### Post by normva on 2007-05-15
How can I set my resolution to 1280*1024. The maximum resolution i can pick is 1024*768.

---

### Post by LaRoza on 2007-05-15
First make sure you have the video drivers you need. Searching the forum will yield results.

Next, open a terminal and enter:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Select the correct options and then restart.

That should work.

---

### Post by Verlaine on 2007-05-15
> **normva said:**
> How can I set my resolution to 1280*1024. The maximum resolution i can pick is 1024*768.

I found I had to log into terminal  mode and run

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the defaults until you get to the monitor resolution section then select 1280*1024 and remove all other choices.

I don't know if this is the easiest or best way but it works for me. If it doesn't your /etc/X11/xorg.conf file will be backed up with a datestamp appended to it.

---

### Post by seamuso on 2007-05-15
Check your refresh rates in your xorg.conf file also. You can have the right driver for your vid card, but wrong refresh rates and lose the ability to hit the higher resolutions that your supposed to be able to achieve.

---

