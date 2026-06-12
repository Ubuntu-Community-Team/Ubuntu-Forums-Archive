---
title: "Screenshot of &quot;Quit&quot; options?"
date: 2007-02-08
forum: General Help
---

### Post by dushkal on 2007-02-08
There's a dialog which comes up when one hits the Quit button or the Quit menu. Does anyone know ow to take a screen shot of the same? The problem is when this dialog is shown, the rest of the windows and the screen is disabled hence the normal screenshot is not possible. I tried it also from GIMP, but without any success....

---

### Post by 23meg on 2007-02-08
You can use xnest to start an embedded X session and take a screenshot of the xnest window. Or maybe a timed method of taking a screenshot would work.

---

### Post by dushkal on 2007-02-08
Timed method does not work. Already tried it. I'll try the xnest thing. A friend suggested that I can try virtual server or vmplayer, and then take the screenshot of any screen...seems too much just for a screenshot.

---

### Post by dawguk on 2007-02-08
Aye, use xnest.

```
sudo apt-get install xnest
```

Once that's done, you can easily open a new desktop session by clicking Applications > System Tools > New Login in a Nested Window.

If this option isn't there, just right click your Applications panel, and click on Edit Menus. Enable it there, and try again. I have just done exactly this, and attached is my shot of my logout screen.

HTH :)

---

