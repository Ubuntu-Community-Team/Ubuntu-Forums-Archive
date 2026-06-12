---
title: "Laptop doesn't restart."
date: 2013-03-02
forum: General Help
---

### Post by Henkdroid on 2013-03-02
Hi all,
When I try to restart my computer it almost turns off but the fan keeps running and the on light is still on. When I shut down my computer it does shut down properly. How can I fix this?

---

### Post by gordintoronto on 2013-03-02
What brand and model of computer? What version of Ubuntu? If the model is xyzzy, put this into Google:
xyzzy restart ubuntu
or this:
xyzzy reboot ubuntu

---

### Post by Henkdroid on 2013-03-03
Whoops, should have mentioned that in the post. It's a ThinkPad T61. I tried searching google but I didn't find any soultions. It's running 12.10.

---

### Post by gordintoronto on 2013-03-03
I can only suggest:
sudo shutdown -h now

---

### Post by jackclarck on 2013-03-04
i think you need to instal new window in your laptop, it may happen due to virus files in your laptop.

---

### Post by zero2xiii on 2013-03-04
> **jackclarck said:**
> i think you need to instal new window in your laptop, it may happen due to virus files in your laptop.

No, no oh and no.

1. He stated he is running UBUNTU 12.10, NOT WINDOWS.
2. He stated that his thinkpad shuts down software side, not hardware side.
3. Linux viruses are almost NON EXISTANT.
4. I do not know of even a windows virus that causes this behavior.


> Hi all,
 When I try to restart my computer it almost turns off but the fan keeps running and the on light is still on. When I shut down my computer it does shut down properly. How can I fix this?

Can you please explain what "almost turns off" means?
Hit F1 during shutdown and note the messages on screen. My laptop used to get stuck at "unmounting main file system" which after a quick google search was fixed and now shuts down properly.

+1 for the shutdown from terminal:
```
sudo shutdown now
```

Please state whether this shuts down the computer properly/fully.

Cherz and good luck :)

---

