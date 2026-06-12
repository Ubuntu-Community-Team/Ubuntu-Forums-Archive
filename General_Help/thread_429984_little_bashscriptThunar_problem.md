---
title: "little bash/script/Thunar problem"
date: 2007-05-01
forum: General Help
---

### Post by conehead77 on 2007-05-01
Hi,

i use the Thunar "customized actions" to run a script. It works as intended.

Now i want to see my script output (the "echo" commands).
If i start the script from the terminal i can see what i want. But when i start the script with Thunar there is no terminal to view it.

Any ideas how i can make the results of my script visible when i start it with Thunar?

---

### Post by conehead77 on 2007-05-04
After a long time of researching i finally found what i was looking for. Running a customized action with Thunar starts this script:

#!/bin/bash
gnome-terminal -x bash ~/bashtest_start.sh $*

bashtest_start.sh is the script i wanted to run in first place. In order to be able to see my script output i needed to open a new bash and run this second script there.
$* is the filename from Thunar in this case which is given to the next script as parameter.

---

