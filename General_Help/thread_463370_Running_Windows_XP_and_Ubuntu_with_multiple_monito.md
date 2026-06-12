---
title: "Running Windows XP and Ubuntu with multiple monitors"
date: 2007-06-03
forum: General Help
---

### Post by wildzer0 on 2007-06-03
OK, here's the setup I want :) I know it's possible to do with various software, etc. but I'm not sure what I need or how to set up so I'm hoping someone here can point me in the right direction. I like Ubuntu, and use it for everything except playing online poker. I use tools (such as autohotkey) when I play so I can't just install the client under Wine. 

So here's what I'd like to do: I have a laptop that I can install Windows and all my poker stuff on, and a desktop I can use for Ubuntu. I have multiple monitors connected to my desktop, which I need when I play poker. Ideally, I'd like to have my laptop sitting next to my desktop and hit some fancy button or something where I could use the same desktop mouse, keyboards and have my laptop screen show up, extended across both monitors (in a 3200x1200 resolution or thereabouts). 

It seems I can find stuff to use the same keyboard or mouse,or extend my laptop screen, but not both and I can't figure out what crazy configuration I need to make it work. If anyone has any ideas they would be much appreciated.

---

### Post by pseudonym on 2007-06-03
For your keyboard and mouse, you could use a Keyboard/Video/Mouse (KVM) switch, without the video part (which would normally used to control 2 or more machines from one monitor).

If you want your laptop display to become part of one large display (if I'm understanding you right), you might be able to do it by connceting to the X server on your desktop, instead of using the local one on the laptop (remember, it's an X *server* ). As to how you would configure this exactly, I'm don't know, but I'm pretty sure it's the direction you want to be heading in.

---

