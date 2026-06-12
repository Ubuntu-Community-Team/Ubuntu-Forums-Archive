---
title: "Simpest way to launch ruby program from desktop entry?"
date: 2008-05-11
forum: General Help
---

### Post by demetrisk on 2008-05-11
I use a desktop shortcut to launch a ruby program (Rubyripper) by means of a script. Here is the relevant part of the desktop entry:

```

Exec=/home/demetris/rrip.sh

```

... and here's the script:

```

#!/bin/bash

cd ~/apps/rubyripper-0.5.0
./rubyripper_gtk2.rb

```

Is it possible to launch such a program directly from a desktop entry, without using a shell script? Is there a better or simpler way to do this?

Thanks for reading! :-)

---

### Post by macaholic on 2008-05-11
I would say the shell script is the simplest and best way to accomplish such a task. I use shell scripts for all my desktop entries that need multiple commands. You should be able to just run ```
~/apps/rubyripper-0.5.0/rubyripper_gtk2.rb
``` directly as a command, which would get rid of the script.

---

### Post by demetrisk on 2008-05-11
Thanks, macaholic!

I already tried launching the ruby script (rubyripper_gtk2.rb) directly from the desktop entry, but it does not work. It only works via the terminal or a shell script.

I was just curious to know if there are better/recommended ways to do this.  :-)

Thanks again.

---

