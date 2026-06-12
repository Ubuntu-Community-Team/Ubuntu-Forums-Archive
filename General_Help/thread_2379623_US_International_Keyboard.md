---
title: "US International Keyboard?"
date: 2017-12-07
forum: General Help
---

### Post by shintaomonk on 2017-12-07
So I have Lubuntu 17.10 with the English Keyboard. I noticed that there are no real keyboard layout settings, and neither is there any specific keyboard layouts under language settings.

I want to change my keyboard to US International, but still have (possibly easy change from taskbar) to change back to the regular US Keyboard

Could anyone help me with this?

---

### Post by sudodus on 2017-12-07
You can try according to this link at AskUbuntu,

[Making Umlauts in ubuntu 17.10 on a ThinkPad430](https://askubuntu.com/questions/967708/making-umlauts-in-ubuntu-17-10-on-a-thinkpad430/968758#968758)

```
setxkbmap -rules evdev -model evdev -layout us -variant altgr-intl
```

You can reset the keyboard to standard US English keyboard with

```
setxkbmap us
```

---

