---
title: "Switching between sound devices (headset and standard)"
date: 2006-08-02
forum: General Help
---

### Post by therblack on 2006-08-02
Hi all,

I have just purchased a USB headset and it seems to be working pretty well with ubuntu (it is a plantronics 400).

What I want to do is configure things so that when I have the headset plugged in, all sound goes to the headset, but when it is not plugged in, all sould goes to my regular sound card.

My main problem seems to be that esd _always_ seems to want to use device 0...which is defined at boot time.

So, if I set things up so that my sound card doesn't used device 0 I can only use esd when my headset is plugged in.

On the other hand, if I set things up so that my sound card uses device 0, then sound always goes to that device even when I have my headphone plugged in.

I should add, that the only reason that I really need esd is for gnome sound effects when opening windows etc.


Any suggestions?

My esd.conf file is:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
default_options=

---

