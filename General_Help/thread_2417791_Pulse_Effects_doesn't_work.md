---
title: "Pulse Effects doesn't work"
date: 2019-04-27
forum: General Help
---

### Post by cingelis on 2019-04-27
I downloaded Pulse Effects but it doesn't work, when I try to start it [This]("https://youtu.be/HRORptL-UK0") happens and nothing else, is there a way to fix it or is there another equalizer that I could use?

---

### Post by vixtron on 2019-04-27
I highly recommend [PulseEffects]("https://github.com/wwmm/pulseeffects") it provides the most of all equalizers on linux, check the images in the repository.
(I realized you just used that)

---

### Post by vixtron on 2019-04-27
Run ```
dconf reset -f /com/github/wwmm/pulseeffects/
```
This used to solve this issue for me.
If that didn't work for you give me the output of this command by executing it from the terminal:
```
G_MESSAGES_DEBUG=pulseeffects
```

---

### Post by cingelis on 2019-04-27
for some reason neither of these commands do anything

---

### Post by cingelis on 2019-04-27
never mind, restarting my pc fixed the issue, don't know why I didn't think of doing that in the first place

---

