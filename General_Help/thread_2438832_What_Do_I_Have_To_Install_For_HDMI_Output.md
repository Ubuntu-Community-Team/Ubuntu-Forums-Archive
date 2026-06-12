---
title: "What Do I Have To Install For HDMI Output?"
date: 2020-03-18
forum: General Help
---

### Post by mawil10132 on 2020-03-18
What Do I Have To Install For HDMI Output?

19.04 B. Beaver, dell inspirion

---

### Post by QIII on 2020-03-18
You should not have to install anything.

Are you having specific problems?

---

### Post by TheFu on 2020-03-18
> **mawil10132 said:**
> What Do I Have To Install For HDMI Output?

19.04 B. Beaver, dell inspirion

Well, 19.04 support ended 2 months ago, so for starters, 19.10.

---

### Post by Impavidus on 2020-03-19
On the other hand, if it's B. Beaver, you've installed 18.04, which is still supported.

HDMI output is supposed to work out of the box, but there have been problems with it in the past. Might it be graphics driver related? Maybe you can tell us a bit more about your hardware.

---

### Post by TheFu on 2020-03-19
Overall system summary:
```
inxi -Fz

```
Video devices:
```
lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
sudo lshw -C video
```

---

