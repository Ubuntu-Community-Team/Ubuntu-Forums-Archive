---
title: "How do I set it to run a command right after I come out of suspend?"
date: 2007-06-19
forum: General Help
---

### Post by Gadren on 2007-06-19
I have an issue where after I suspend my laptop, the wifi doesn't work.  I have a couple commands which fix the problem, but I'd like to be able to have it run those commands automatically, when I take the laptop out of suspend.  How do I do that?

---

### Post by Brucevdk on 2007-06-20
I think you can create a file named *xx-descriptive_name.sh* in */etc/acpi/resume.d/* where xx is a number between 01 and 99 (01 is executed first, 99 is executed last). 99 would probably be fine in your case. The file itself is a simple shell script so should start with a shebang and then the commands you wish to be executed.

```

#!/bin/sh

# your commands here

```

You should probably let root own it and chmod +x it just like the other files in the directory.

---

