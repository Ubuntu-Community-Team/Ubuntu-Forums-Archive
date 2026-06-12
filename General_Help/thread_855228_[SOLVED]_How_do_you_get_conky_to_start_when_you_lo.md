---
title: "[SOLVED] How do you get conky to start when you log in"
date: 2008-07-10
forum: General Help
---

### Post by Bigtime_Scrub on 2008-07-10
I want conky to load and start when I log in, how do I do that?

I created a script .conky_start.sh with #!/bin/bash
sleep 20 && conky


I run compiz so I was trying to add a little delay to let the desktop settle itself. I made the script with text editor and saved it in my home folder.

---

### Post by Sealbhach on 2008-07-10
.

---

### Post by SkonesMickLoud on 2008-07-10
Make the script executable by right clicking on the script, selecting "Properties", clicking the "Permissions" tab and tick the "Allow executing file as program" box.

Then, go to System >> Preferences >> Sessions >> Startup Programs tab.  Click add and in the "Command" box enter:

```
sh ~/.conky_start.sh
```

You can name it whatever you like.

Then, hit Ctrl+Alt+Backspace (first save anything that's open) and see if it worked for you.

---

### Post by SkonesMickLoud on 2008-07-10
> **Sealbhach said:**
> You can add it to startup sessions.

System/Preferences/Sessions

Command is 

conky


.

That starts conky right away, without any sleep.  Doing so will allow Compiz to draw shadows around the conky window.

---

### Post by Bigtime_Scrub on 2008-07-10
I deleted the script I made and added conky in the sessions like you said. It start ups when I log in but it also covers any window I open too.

---

### Post by SkonesMickLoud on 2008-07-10
> **Bigtime_Scrub said:**
> I deleted the script I made and added conky in the sessions like you said. It start ups when I log in but it also covers any window I open too.

Like I said, that lets conky start right away, without any sleep, which let's compiz draw all sots of stuff around it.  Rewrite your script, or dumpster-dive your trash for it and see my post above.

As for it covering windows, check your .conkyrc for a line containing "own_window_type".  What does it say after that?

---

### Post by Bigtime_Scrub on 2008-07-10
> **SkonesMickLoud said:**
> Make the script executable by right clicking on the script, selecting "Properties", clicking the "Permissions" tab and tick the "Allow executing file as program" box.

Then, go to System >> Preferences >> Sessions >> Startup Programs tab.  Click add and in the "Command" box enter:

```
sh ~/.conky_start.sh
```

You can name it whatever you like.

Then, hit Ctrl+Alt+Backspace (first save anything that's open) and see if it worked for you.

Yeah that did it thanks. I hadn't seen your post yet when I wrote that. Thank you very much. I thought I needed a script but I wasn't too sure.

---

