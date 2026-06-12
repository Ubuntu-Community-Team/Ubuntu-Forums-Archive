---
title: "Enable indicator via shell ?"
date: 2020-07-06
forum: General Help
---

### Post by ikerib-reg on 2020-07-06
Hi,

In our company we have 200 Ubuntu Mate 16.04 and for enabling indicator I have to open Mate-Tweak => Interfaces => check Enable indicators

We don't want to do it manyally, so is there any way to do it via shell script?? how??

Thanks in advance

---

### Post by Impavidus on 2020-07-06
Do you realise that Ubuntu Mate 16.04 has reached end of life? Of 16.04, only regular Ubuntu still has 9 months of support left. The flavours only had 3 years of support. Yes, I know it's not easy to quickly migrate 200 computers to 20.04.

I'm quite sure there's a shell command to change these settings, but I don't use Mate, so it's a bit hard for me to find out. Further, things like this are likely to change from one release to the next.

---

### Post by ikerib-reg on 2020-07-06
yes, we know. We are going to upgrade all of them to Ubuntu Mate 20.04 lts but meanwhile (and also in 20.04) we need to enable this feature.

---

### Post by tea for one on 2020-07-06
I also do not use Mate Desktop but I would think that it is built on top of Gnome 3. I do **not** know about the base of 16.04 with Mate.

Nevertheless, I think that you need to explore **gsettings** [http://manpages.ubuntu.com/manpages/focal/man1/gsettings.1.html](http://manpages.ubuntu.com/manpages/focal/man1/gsettings.1.html)

For example, Gnome Terminal is supplied without the menu bar at the top and you can enable/disable it with **gsettings**.

To enable the menu bar

```
gsettings set org.gnome.Terminal.Legacy.Settings headerbar false
```

To disable the menu bar

```
gsettings set org.gnome.Terminal.Legacy.Settings headerbar true
```

I would imagine that there is a similar command to enable/disable the indicators.

---

### Post by Holger_Gehrke on 2020-07-06
Another person not using Mate giving his opinion ...

 Unless I misinterpret things, mate-tweak is a [python script]("https://github.com/ubuntu-mate/mate-tweak") and you can just look at the code to see what it does. Seems to me it just copies some .desktop files into the autostart-folder if you activate indicators.

Holger

---

