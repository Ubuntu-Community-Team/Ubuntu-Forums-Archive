---
title: "Limited to 800X600 Resolution! HELP!"
date: 2007-05-05
forum: General Help
---

### Post by jack_teagarden on 2007-05-05
I know, tons of people have had this problem....

I can't get my box out of 800X600! It doesn't matter if I boot KDE or gnome, or anything!

My kernel is fine, and Graphics card too.

I left over the weekend and came back with a nasty surprise, and I can't get it working again!

Any suggestions, tests to run, etc.?

---

### Post by cptjaben on 2007-05-06
try this in the terminal. Then restart your X server. 

```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

Hope this helps.

---

### Post by jack_teagarden on 2007-05-06
Yeah, just tried it.
I've been unable to get it to work, with the usuals like "nvidia-config" and "dpkg-reconfigure", but even if I take out 640X480 and 800X600 It still boots in 800X600 and I can't change it!

Thanks for the suggestion!

---

### Post by ramjet_1953 on 2007-05-06
It's a bit hard to help you, when you don't give us any details of your hardware.

What video card/chipset do you have?
Are you running a widescreen or 4:3 monitor?

What is the native resolution of your monitor?

Answer these questions and we may be able to help you.

Regards,
Roger :cool:

---

### Post by SigmundL on 2007-05-06
Solved it by adding the correct sync frequencies (horizontal and vertical) for my display in xorg.conf.

---

### Post by jack_teagarden on 2007-05-06
Thanks guys!

I set my sync ranges to the right ones and now it works! I don't know how it just popped up like it did, but thanks a TON!

---

