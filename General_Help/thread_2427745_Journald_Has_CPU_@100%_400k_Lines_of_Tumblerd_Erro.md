---
title: "Journald Has CPU @100% 400k Lines of Tumblerd Errors"
date: 2019-09-25
forum: General Help
---

### Post by uRock on 2019-09-25
Good day friends,

journald has been jumping to 100% for a few days now and I had thought it was due to a wireless card that had been giving issues, but after running journalctl and holding the space bar for a few minutes, I have found more than 400,000 lines of this error,

```
OxfordComma tumblerd[8567]: gst_poll_read_control: assertion 'set != NULL' failed
```

I know there are a lot more than that number of lines as I held the space bar for several minutes and didn't even get through Sep 23rd. Any ideas on troubleshooting and solving this would be very welcomed.

---

### Post by uRock on 2019-09-25
Killing tumblerd did bring the CPU usage back down to normal, but I'd love to find out why it's happening and stop it from repeating.
```
killall tumblerd
```

---

### Post by uRock on 2019-09-25
It seems this is likely triggered when a new video is completed by Motion and Thunar is open to the the target directory. I've switched to PCmanFM for now. I don't need thumbnails for videos and by default PCmanFM doesn't create thumbnails for files over 2MB.

---

### Post by Holger_Gehrke on 2019-09-25
You can find a configuration for the thumbnailer tumblerd in /etc/xdg/tumbler/tumbler.rc. It is documented [here]("https://docs.xfce.org/xfce/thunar/tumbler"). Disabling thumbnails for videos solved a similar problem for me some time ago.

Holger

---

### Post by uRock on 2019-09-25
> **Holger_Gehrke said:**
> You can find a configuration for the thumbnailer tumblerd in /etc/xdg/tumbler/tumbler.rc. It is documented [here]("https://docs.xfce.org/xfce/thunar/tumbler"). Disabling thumbnails for videos solved a similar problem for me some time ago.

Holger

I'll check that out. Thanks!

---

