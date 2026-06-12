---
title: "Ctrl+c in Minicom"
date: 2008-07-08
forum: General Help
---

### Post by jonlemur on 2008-07-08
I can't seem to figure out how to send a "Ctrl+c" command in minicom, gtkterm, picocom, or cutecom.  The test that I'm using is this ```
# cat > newfile
``` If I do this from a terminal on my host machine (like gnome-terminal) I can hit "Ctrl+c" and it will exit and give me another prompt.  I can also hit "Ctrl+d" to send it the end-of-file that it would like to get, and it closes, giving me another prompt.  

But if run the same command from minicom (or any of the others mentioned above) to a device with embedded Linux, I can only issue the "Ctrl+d" command to end cat.  I can't use "Ctrl+c"

I need to use "Ctrl+c" in a much more important application, but cat seemed like an easy test to see if it worked.

I've searched a lot and read a bunch of other forums, and it seems like it's a common problem.  Unfortunately, none of the posts I saw had solutions, so I wanted to see if anyone here has run across this issue and found a solution.

---

### Post by jonlemur on 2008-07-10
bump

---

### Post by txcrackers on 2008-07-10
Can't quite remember what the key-sequence is, but try sending a "break" (CTRL+A Z)? it's been many years since I last used minicom...

---

### Post by jonlemur on 2008-07-10
Ctrl+A Z opens the options menu, where I can turn the capture on, or change the settings, etc.  I haven't been able to figure out how to send a Ctrl+C through it though.

---

### Post by dedmeet on 2011-02-09
I know this thread is old, but this info seems to be very obscure, and this post comes up high in google, so here is the answer:

Switch off hardware flow control, which then enables the break :)

---

### Post by LinuxChristian on 2011-03-11
Thank you very much. That was just the answer I was looking for. Even old thread needs answers :)

---

### Post by jonlemur on 2011-07-30
Wow, it's been a long time since I've been on here.  Thanks for the answer!

---

### Post by Wim Sturkenboom on 2011-07-30
> **jonlemur said:**
> Wow, it's been a long time since I've been on here.  Thanks for the answer!
If your issue is solved, mark it as such using the thread tools just above the first post.

---

