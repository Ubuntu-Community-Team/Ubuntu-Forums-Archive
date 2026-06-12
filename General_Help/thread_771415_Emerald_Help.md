---
title: "Emerald Help"
date: 2008-04-27
forum: General Help
---

### Post by griehl2490 on 2008-04-27
I have Emerald installed with two themes inside it but I don't know how to set them as the theme and have the windows change. Help?

---

### Post by Ponomous on 2008-04-27
So when you open emerald there are the themes you have shown in a list.  all you have to do is click one and the windows should change.  Is this not happening?  what are you running?

---

### Post by griehl2490 on 2008-04-27
> **Ponomous said:**
> So when you open emerald there are the themes you have shown in a list.  all you have to do is click one and the windows should change.  Is this not happening?  what are you running?

Yes. I click on them and nothing happens. What do you mean by what am I running? I'm not sure how to respond to that....like what version of ubuntu or emerald or just specs?

---

### Post by Ponomous on 2008-04-27
haha yeah i suppose i wasnt very clear on that.  What version of ubuntu are you running?

Also I am going to make the assumption that you have compiz installed as well.

One more thing, have to tried restarting, I had this problem as well and just by restarting it fixed.

---

### Post by griehl2490 on 2008-04-27
> **Ponomous said:**
> haha yeah i suppose i wasnt very clear on that.  What version of ubuntu are you running?

Also I am going to make the assumption that you have compiz installed as well.

One more thing, have to tried restarting, I had this problem as well and just by restarting it fixed.

Yes. I have compiz installed along with the configuration things for compiz. I have like the desktop cube and what not. I'm on Hardy and I have it installed inside windows through Wubi. I have restarted it before to no avail though.

---

### Post by Ponomous on 2008-04-27
have you tried
```
emerald --replace
```

---

### Post by griehl2490 on 2008-04-27
It doesn't output anything but it changed the color of the bar at the top of each window to red....sometimes when I close the terminal it goes away and sometimes it stays.

---

### Post by Ponomous on 2008-04-27
I am assuming the red bar was the theme you were looking for?

Use Alt-F2 - this opens a terminal "launcher" of sorts. All programs that you start in a terminal will be closed when you close that terminal so thats why the red bar was going away...although sometimes you can get around this by typing in a "&" after the command.

You could try this with emerald, by typing

```
emerald --replace &
```

---

### Post by Moop on 2008-04-27
Install the fusion-icon from Synaptic. After it's installed you can find it in Applications-System Tools. It makes it easy to switch emerald on and off without a restart.

---

### Post by griehl2490 on 2008-04-28
> **Ponomous said:**
> I am assuming the red bar was the theme you were looking for?

Use Alt-F2 - this opens a terminal "launcher" of sorts. All programs that you start in a terminal will be closed when you close that terminal so thats why the red bar was going away...although sometimes you can get around this by typing in a "&" after the command.

You could try this with emerald, by typing

```
emerald --replace &
```

No. I don't know why it was picking red. It wasnt the theme I wanted.

---

### Post by schauerlich on 2008-04-28
Try adding "emerald --replace" without the quotes into your sessions file. There should be a Sessions option under in Preferences. Then just log out and back in with Ctrl+Alt+Backspace.

---

