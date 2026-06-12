---
title: "What happened to the preferences menu???"
date: 2015-12-25
forum: General Help
---

### Post by Evil Wayz on 2015-12-25
I used to be able to change the appearance of everything from highlighting to how transparent my terminal was.  Now there's just theme and icon size.  Ubuntu tweak doesn't do either of those.

---

### Post by Vladlenin5000 on 2015-12-25
What preferences menu? Where?

Your post is really vague. You could have, at the very least, informed what Ubuntu release you're running...

---

### Post by Evil Wayz on 2015-12-26
It says right there in the upper right corner what ubuntu I'm running.  

[IMG]http://i64.tinypic.com/fapwjq.jpg[/IMG]

And I don't know what those white lines are, they just showed up when I accidentally changed by theme settings.  

Regardless, I changed the theme setting using that radio button there and it said default by one so I assumed that would be what I would go back to if I didn't like it.  Well I didn't, so I clicked on default and now I got this hideous orange based theme that I can't stand.  And there's only three themes listed, Ambiance, Adwaita and High Contrast.  Tweak shows about twenty five listed but I can't remember the combination of gtk and windows settings.

Oh and I'm using gnome flashback, not Unity.

---

### Post by grahammechanical on 2015-12-26
> Oh and I'm using gnome flashback, not Unity.

You knew that. Nobody else did.

Change a setting in flashback metacity and it changes things in flashback compiz and compiz unity. Changes to settings in one user session are reflected in the other user session settings. And sometimes become difficult to correct.

Have you installed any themes? They would need to be GTK+3 based themes.

---

### Post by v3.xx on 2015-12-26
And this is metacity, right?

```
update-alternatives --get-selections | grep x-window-manager
```

---

### Post by Evil Wayz on 2015-12-26
Clicking on Metacity in the Other section of my menu doesn't seem to do anything.  I don't have a compiz manager installed that I know of.  I guess I'll download some gtk3 themes and see if they work, I'm guessing all the themes that tweak tool shows are gtk2.

---

### Post by Evil Wayz on 2015-12-28
When I run that command: 
```
update-alternatives --get-selections | grep x-window-manager
```

THis is the output:

```
x-window-manager               auto     /usr/bin/metacity

```

---

