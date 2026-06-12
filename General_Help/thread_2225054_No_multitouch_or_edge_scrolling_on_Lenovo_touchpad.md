---
title: "No multitouch or edge scrolling on Lenovo touchpad"
date: 2014-05-19
forum: General Help
---

### Post by yamel3 on 2014-05-19
I've read a lot of similar posts, but I don't see my exact configuration. I'm working on a Lenovo Yoga 2 11", running 14.04. It has an ElanTech touchpad, but settings are limited out of the box. No mention of multitouch or edge scrolling in system settings.

xinput list gives me this:[INDENT]Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Elantech Touchpad                      id=12    [slave  pointer  (2)]
[/INDENT]

I'd love to make multitouch work from the touchpad, but after days of pointing and grabbing scroll bars, I'd be happy with edge scrolling.

Thanks!

---

### Post by yamel3 on 2014-05-19
Exciting news! I fixed it myself (thanks to duckduckgo and some bug reports!)

The ElanTech touchpad problem is a bug - there's a long thread dealing with it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all)

The advice in post #137 worked for me. (Shout to [http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/](http://www.evilcodingmonkey.com/2014/01/23/ubuntu-activate-multi-touch-on-elantech/) - a stop on the way to solving.)

---

