---
title: "Delaying Some Startup Programs With &quot;sleep&quot;??"
date: 2007-08-22
forum: General Help
---

### Post by bunnyfly on 2007-08-22
Hello, to reduce bootup stutter and slow loading, I'm trying to delay my non-essential startup programs by a few seconds on startup. I used to use a program to do this in my old Windows, and it made bootup smoother and faster. I went into System-Preferences-Sessions-Startup and altered all of my lesser apps to have a delay with the sleep command but it isn't working.

For example, Skype's command is "sleep 5 && skype"

It works in a regular prompt, but somewhy none of my startup programs load when I use this with them. Any suggestions? Thanks,
[bunnyfly]

---

### Post by eentonig on 2007-08-22
Two possible solution.
- I play with the starting order for my programs by adjusting the priority in the sessions.
- I create a little script to start the program. I call the script, have it sleep, and then execute the program.

---

### Post by bunnyfly on 2007-08-22
Ah - the script works great! Thank you : )
[bunnyfly]

---

### Post by schistyshebz on 2007-08-23
Would you mind posting or PM'ing the script you used? I can't seem to get the Start-up processes to delay.

---

