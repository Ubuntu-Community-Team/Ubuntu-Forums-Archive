---
title: "Installing Opera Fonts"
date: 2008-07-02
forum: General Help
---

### Post by WeEatVista on 2008-07-02
I just installed Opera just to check it out because lately Firefox has been crashing out of know-where, and going to a grey-screen every 10 minutes. So I installed Opera 9.5 and opened it up. There are a few minor problems...


The font is not smooth as it is in firefox, the font looks all digital and rough. I like the smooth look as in firefox. I looked in 'Appearance' and 'Preferences' and firefox uses serif. So then I went to Opera, and tried to change the font but Opera doesnt have serif in the font list. How can I install that?

Also, I can't seem to remember the name of it, but the bar where you enter the URL, (ill post screens of opera v firefox) is really small, almost hard to read. How can I fix this?

Thanks,

We Eat Vista

---

### Post by kuja on 2008-07-03
serif is a very generic font I think. Try using something like Dejavu Sans.

---

### Post by Blingin2Mingin on 2008-07-14
I got rid of the rough fonts in Opera 9.5 by doing the following.

```
sudo gedit /etc/opera6rc.fixed
```

I then added the following lines under the entry that says :
; Settings in this file are not overridable by users

```
[User Prefs]
Enable Core X Fonts=0
```

I saved the file and restarted Opera and the problem websites then rendered beautifully.

---

### Post by svivian on 2008-07-20
> **WeEatVista said:**
> The font is not smooth as it is in firefox, the font looks all digital and rough. I like the smooth look as in firefox.

What are you, nuts? Fonts look waaaay smoother in Opera (and all other KDE apps like Kate and Amarok).

If you're adamant you want rubbish fonts like Firefox, Blingin's solution can be done from inside Opera, just type opera:config in your address bar, type "fonts" in the quick search then uncheck the "Enable X Core Fonts" box. But honestly I don't see the problem.

---

