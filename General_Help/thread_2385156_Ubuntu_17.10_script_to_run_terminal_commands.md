---
title: "Ubuntu 17.10 script to run terminal commands"
date: 2018-02-16
forum: General Help
---

### Post by Weedoobs on 2018-02-16
Hello guys! Still learning, so don't laugh at me.
Im trying to figure out how can i make a .sh executable to start terminal and run a command like "apt update" let's say. Or "tizonia --youtube-audio-search eminem" for example.

I know if i want the terminal to stay open after i have to change my terminal profile or use a --hold flag, but i can't seem to make my script work, dunno why?

I write 
#!/bin/bash  
gnome-terminal -x bash -c "apt update"
save it as .sh, make it executable and nothing...Do i run it with the wrong program or what?

Thanks.

---

### Post by ajgreeny on 2018-02-17
You must run **apt update** as root with sudo, so change the command used to ```
gnome-terminal --hold -x bash -c "sudo apt update"
```
The **--hold** option will keep it open after running and sudo will allow apt update to proceed as if run normally in terminal.

It's working for me so should for you as well.

---

### Post by again? on 2018-02-17
The --hold flag doesn't work for me and the -x flag appears to be on the way out.
```
**[COLOR="#006400"]glen@Xubarty:~$[/COLOR] gnome-terminal --hold -x bash -c "sudo apt update"**
Option &#8220;-x&#8221; is deprecated and might be removed in a later version of gnome-terminal.
Use &#8220;-- &#8221; to terminate the options and put the command line to execute after it.
Failed to parse arguments: Unknown option --hold

```

Appending the command/script with $SHELL keeps the terminal open for me.
Reading the above error and testing, this works for me...
```
gnome-terminal -- sh -c "sudo apt update; exec $SHELL"
```

---

