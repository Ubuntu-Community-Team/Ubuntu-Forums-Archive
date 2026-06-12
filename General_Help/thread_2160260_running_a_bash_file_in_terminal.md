---
title: "running a bash file in terminal"
date: 2013-07-06
forum: General Help
---

### Post by goof on 2013-07-06
i have a bash file that executes from crontab the bash file is 

#!/bin/bash 
java -jar "path and file"

this works fine but i want it to open and run in a terminal rather than just run how can this be done?
if iwas just running it without crontab i would just paste java -jar "path and file" in terminal and this works fine but how do i specify in bash file that i want it to run in terminal ?

---

### Post by The Cog on 2013-07-06
I would guess something like this:
```
#!/bin/bash 
export DISPLAY=:0.0
gnome-terminal -e java -jar "path and file"
```
but it won't work unless you are logged in at the time, because if you're not logged in then you don't own the display and don't have rights to open windows on it.

---

### Post by goof on 2013-07-06
#!/bin/bash  export DISPLAY=:0.0 gnome-terminal -e java -jar "path and file"

doesint execute


export DISPLAY=:0.0 gnome-terminal java -jar "path and file"

does open terminal but it cd to the folder that the bash is in which then wont execute the file it just opens terminal navagated to desktop fr example if the bash was on the desktop -e should execute the code but doesint nothing happens when bash runs thanks for reply

---

### Post by The Cog on 2013-07-07
I really have trouble working out where the punctuation should be in that response. But if the problem is that it ends up in the wrong directory, then add a cd command to the script:
```

#!/bin/bash 
export DISPLAY=:0.0
cd /wherever/you/need/to/be
gnome-terminal -e java -jar "path and file"

```

---

