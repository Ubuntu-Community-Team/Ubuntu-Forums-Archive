---
title: "command for close browser in ubuntu"
date: 2013-04-15
forum: General Help
---

### Post by mdasrafulislam on 2013-04-15
Can any body let me know the command for closing browser from ubuntu terminal? I dont want to kill the process , I just want to shut  down the browser normally from terminal. If I kill the process then it  will ask me restore when it start again. I need this command in one of  my project.

---

### Post by SlugSlug on 2013-04-15
What browser?

```
pkill -9 firefox
```

---

### Post by sp-1070 on 2013-04-15
if you did open it in a terminal just use cntrl + c 
you could killall -9 firefox-bin.

---

### Post by mdasrafulislam on 2013-04-15
Thanks for reply. Actually I dont want to kill the process , I just shut down the browser normally from terminal. If I kill the process then it will ask me restore when it start again. I need this command in one of my project.

---

### Post by mdasrafulislam on 2013-04-15
Thanks for reply. Actually I dont want to kill the process , I just shut  down the browser normally from terminal. If I kill the process then it  will ask me restore when it start again. I need this command in one of  my project.

---

### Post by nerdtron on 2013-04-15
> **mdasrafulislam said:**
> Thanks for reply. Actually I dont want to kill the process , I just shut down the browser normally from terminal. If I kill the process then it will ask me restore when it start again. I need this command in one of my project.

I just tried it with ```
killall firefox
```
Firefox closed and when I open up, is did not asked for a restore.
killall command (with no options) sends a SIGTERM signal to the process named firefox. It is not a force terminate.
 By the way, if I understand it right, don't use -9 option in the kill command because it like forcing to kill the process.

---

### Post by prodigy_ on 2013-04-15
[http://how-to.wikia.com/wiki/How_to_gracefully_kill_%28close%29_programs_and_processes_via_command_line](http://how-to.wikia.com/wiki/How_to_gracefully_kill_%28close%29_programs_and_processes_via_command_line)

---

