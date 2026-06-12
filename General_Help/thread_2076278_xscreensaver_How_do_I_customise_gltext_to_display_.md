---
title: "xscreensaver: How do I customise gltext to display text of choice?"
date: 2012-10-25
forum: General Help
---

### Post by blesbok on 2012-10-25
Am using 12.04 LTS. In
/usr/share/applications/screensavers/gltext.desktop , changed a line to read
```

Exec=/usr/lib/xscreensaver/gltext -root -front -text 'The text\n %l:%M:%S %p
```

But xscreensaver won't show *The text* but is stuck on my computer's name, as before. Any advice?

---

### Post by pbrane on 2012-10-25
you should be using the xscreensaver settings dialog box. but FYI GLText only displays system info or date and time.

---

### Post by Toz on 2012-10-25
Actually, GLText can display any text you want. Go to xscreensaver preferences, click on Settings then Advanced (if it is not selected). There you will see the command line. Change the command line to the one you want.

Note that the command line that you entered in post #1 is missing the closing single-quote - make sure you add it. This is the command line as I have it entered:
```
gltext -root -text 'The text'
```

Alternatively, you can edit ~/.xscreensaver directly to make the change.

---

### Post by blesbok on 2012-10-26
**ALT F2** followed by *xscreensaver-demo* brings up xscreensaver with display modes; Mode is *Only One Screen Saver* and *GLText* is the current selection. Under the display demo are the buttons *Preview* and *Settings...* Click on *Settings...* and there is *Command Line* as mentioned by **Toz**. It reads ```
gltext -root
``` Changing it to ```
gltext -root -text 'The text'
``` does what Toz said it would. Solved!

The file I mentioned was the wrong one to edit, even with that second quote mark, which is what I'd done. $HOME/.screensaver now contains the new text. Thank you for the help  :)

---

