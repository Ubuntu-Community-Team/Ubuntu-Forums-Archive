---
title: "remap Ctrl key?"
date: 2012-11-23
forum: General Help
---

### Post by minsf on 2012-11-23
How can I remap (left) Control key so that:
1. If it is pressed and released with no other key, it acts as Escape.
2. If it is pressed & held together with another key, it acts as Control (no change in behavior in this case).

The closest I was able to do is:
```

xmodmap -e 'remove Control = Control_L'
xmodmap -e 'keysym Control_L = Escape'
xmodmap -e 'add Control = Escape'

```
The problem is that this now pressing Ctrl+A sends Escape followed by Ctrl+A (rather than just Ctrl+A) even when another key is pressed. This is bad since, for example, in vim's insert mode, I cannot use Ctrl+R to paste a register, because this first sends Escape which throws me into normal mode...

---

### Post by Impavidus on 2012-11-24
I see another complication: When you press escape you want it to be undecided whether that's an escape or a control until you either press another key at the same time (making it control)or you release escape (making it escape). So you don't only want to change the "label" of a key, but also the actions: ignore the press, turn a release without other keys into a press followed by a release, turn a press of another key whilst holding control into a press of control followed by a press of the other key. Sounds nasty to me... It will probably get really complicated.

---

### Post by minsf on 2012-12-07
[https://github.com/alols/xcape](https://github.com/alols/xcape)

---

