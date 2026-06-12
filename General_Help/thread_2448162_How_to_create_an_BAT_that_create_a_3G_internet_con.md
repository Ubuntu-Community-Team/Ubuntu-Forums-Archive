---
title: "How to create an BAT that create a 3G internet connection ?"
date: 2020-08-03
forum: General Help
---

### Post by aug7744 on 2020-08-03
I am new Linux user.
Linux use bat for commands thus windows ?
If yes is possible to create an desktop an bat to automatically run tasks and start an created 3G connection ?
What command I need to add in bat to do all above ?

---

### Post by Holger_Gehrke on 2020-08-03
What you're looking for is called a 'shell script' on Linux. They can be called whatever you want, no need for any special extension like '.bat' or '.sh'. Just write the commands into a file and make the file executable, either using the properties of the file in the file manager or by using chmod on the command line. Since users can have different shells that have different capabilities in terms of scripting it's a really good idea to put a special line at the very beginning of the file that tells the system what program to use to execute the commands in the file. This is called a shebang line and looks like this:
```

#!/bin/bash

```
Having this as the first line of a file tells the system to use the bash - the standard shell on Ubuntu - to interpret the commands in the file. For more information on shell scripting you might want to take a look into ["The Linux Command Line" by William Shotts]("http://www.linuxcommand.org/tlcl.php/index.php"), a good (and free) book on the topic.

As far as starting a 3g connection, I don't use that, but a look into the manual page for the command line tool for the network manager makes me think you'll need at least
```

#!/bin/bash
# switch 3g radio on
nmcli radio wwan on
# connect
nmcli connection up NameOfTheConnection

```
Lines starting with '#' are comments. Replace 'NameOfConnection' with the name you gave the connection when you created it. For a script to switch everything off again,  change the order of the commands ('nmcli connection ..' first then 'nmcli radio ...'), replace 'up' with 'down' and 'on' with 'off'.

**Again, this is untested guesswork since I don't use 3G. **AFAIK, networking has changed some between 18.04 - which I still use - and 20.04, so I might be completely wrong, but it should at least point you in the right direction.
Holger

---

### Post by ActionParsnip on 2020-08-03
Remember to mark the script as executable using
```

chmod +x /path/to/script

```
Some people like to put file extensions on their scripts but it's not necessary

---

### Post by aug7744 on 2020-08-13
Commands work in Lubuntu 20.04.
Thanks very much.

---

