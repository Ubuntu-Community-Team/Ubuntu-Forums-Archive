---
title: "using export command in main menu"
date: 2008-05-27
forum: General Help
---

### Post by mygind on 2008-05-27
Hey there!
So I've installed maple and found out that to start it right I have to use:
"export AWT_TOOLKIT=MToolkit && ./maple11/bin/xmaple"
in a shell.

Now what I want is a shortcut from the top menu which does this command. But it doesn't know the command "export", bacause it's a shell-only command? Or is it because I have to fond it somewhere in a place like "/usr/share/bin/export"
which I don't seem to find

Anyone know what to do? Is there a substitute for the "shortcut" export?

-Mygind-

---

### Post by danwood76 on 2008-05-27
What you can do is create a small bash script that launches the app.

So make a file in gedit containing the following:
```

#!/bin/bash
export AWT_TOOLKIT=MToolkit && ./maple11/bin/xmaple

```
Name it something like launch_maple.sh and make it executable in the permissions editor.
double click it to launch it and check that it works.

The xmaple path in the above statement looks incorrect, if you run that command from the terminal without changing dir then make it ~/maple11/bin/xmaple instead (~/ means your home directory)

---

### Post by mygind on 2008-05-27
sweet! thanks alot.
Problem solved (and yes it was a typo...)

---

