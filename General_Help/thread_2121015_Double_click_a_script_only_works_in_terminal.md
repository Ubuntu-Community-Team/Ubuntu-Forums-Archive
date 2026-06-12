---
title: "Double click a script only works in terminal?"
date: 2013-02-28
forum: General Help
---

### Post by Alan87i on 2013-02-28
I have a simple script to replay a beep wav file 

```
#!/bin/bash
watch -n 1 aplay /beep2.wav 
```
when I double click on it and choose run nothing happens . if I choose run in terminal it works fine. 
How do I get it to run with out a terminal window?
Thanks 
Allan

---

### Post by |{urse on 2013-02-28
Add gnome-terminal -x before your aplay command, like this
 
#!/bin/bash
gnome-terminal -x watch -n 1 aplay /beep2.wav

---

### Post by Alan87i on 2013-02-28
Thanks that works when I click run .

---

### Post by sudodus on 2013-02-28
> **|{urse said:**
> Add gnome-terminal -x before your aplay command, like this #!/bin/bashgnome-terminal -x watch -n 1 aplay /beep2.wavBut if you don't want to see any terminal window, you can run xterm with the option iconic, for example
```

#!/bin/bash
xterm -iconic -e espeak 'hello world'

```

---

