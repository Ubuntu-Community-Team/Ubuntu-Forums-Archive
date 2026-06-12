---
title: "Help running .sh files"
date: 2013-07-12
forum: General Help
---

### Post by carmen2012 on 2013-07-12
I updated from Ubuntu 10.04 LTS to Ubuntu 13.04 with Cinnamon.  One of the programs that I use is Serviio and the file to run is a .sh file

When I was on 10.04, I could just double click on it and it would execute.  On 13.04, this does not work.  Instead, it opens up as a text document.  I did find a terminal command (sh ./serviio-console.sh) through Google which works

However, how can I set up 13.04 so that I can just double click on the .sh file to run it.  I have gone into the properties of the .sh file to ensure that it is set to execute.

Thank you

---

### Post by bry012 on 2013-07-12
You might need to change the shebang line at the top of the .sh file. for example, I run ubuntu 13.04 and my path to the bash environment or sh environment is '/bin/bash' instead of say '/usr/bin/bash'. That said you might need to look at the beginning of the file and change the portion starting with '#!', the shebang, to the correct path to bash or sh. The final product would look something like this:

#!/bin/bash

Remember to place this at the beginning of the file in question.This tells your computer what environment to run your script through, bash in this case.
hope this helps!

---

### Post by carmen2012 on 2013-07-12
> **bry012 said:**
> You might need to change the shebang line at the top of the .sh file. for example, I run ubuntu 13.04 and my path to the bash environment or sh environment is '/bin/bash' instead of say '/usr/bin/bash'. That said you might need to look at the beginning of the file and change the portion starting with '#!', the shebang, to the correct path to bash or sh. The final product would look something like this:

#!/bin/bash

Remember to place this at the beginning of the file in question.This tells your computer what environment to run your script through, bash in this case.
hope this helps!

Thank you for your response.

Serviio.sh has the path listed as #!/bin/sh .  I've tried changing it to #!/bin/bash and also #!/usr/bin/bash but it still opens in a text editor when I double click on it.

---

### Post by bry012 on 2013-07-13
i think i found a fix. You will probably have to go and change your nautilus settings in dconf-editor. You should be able to find it in the start menu search bar. Once there go to org => gnome => nautilus => preferences and change the  executable-text-activation option to either launch or ask(prompts for action before running).
here is a link to more detailed instruction:
[http://askubuntu.com/questions/286621/how-do-i-run-executable-bash-scripts-in-nautilus](http://askubuntu.com/questions/286621/how-do-i-run-executable-bash-scripts-in-nautilus)

I just tried this in ubuntu cinnamon so it should work unless you installed a different file manager.

---

### Post by carmen2012 on 2013-07-13
That worked, thank you so much for your help

---

### Post by bry012 on 2013-07-13
Your welcome :)

---

### Post by carmen2012 on 2013-07-13
Everything works, but If I can ask you just one more thing.

On the link that you provided ( [http://askubuntu.com/questions/286621/how-do-i-run-executable-bash-scripts-in-nautilus](http://askubuntu.com/questions/286621/how-do-i-run-executable-bash-scripts-in-nautilus) ), we used the second answer on the list and dconf-editor to make the change.

The first answer at the top of the page offers the same sort of solution but with a gui[FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][COLOR=#333333] ([/COLOR][/FONT]open nautilus, click Files > Preferences) .  Is that option stripped out of 13.04.  I did a search for Nautilus in my install and nothing came up.

---

### Post by HiImTye on 2013-07-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
Nautilus has been renamed to 'Files' but the executable is still nautilus, so if you were to launch it from a terminal you would still type ```
nautilus
```

---

### Post by monkeybrain2012 on 2013-07-15
Instead of using dconf, the easy way is simply to open nautilus (or File) , go to File > Preference > Behaviour and find the Executable Text Files and select "Ask" instead of "View"

---

### Post by carmen2012 on 2013-07-15
> **monkeybrain2012 said:**
> Instead of using dconf, the easy way is simply to open nautilus (or File) , go to File > Preference > Behaviour and find the Executable Text Files and select "Ask" instead of "View"

Thank you for the solution, this worked.

---

