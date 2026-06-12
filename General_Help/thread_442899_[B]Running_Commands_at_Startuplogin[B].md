---
title: "[B]Running Commands at Startup/login[/B]"
date: 2007-05-14
forum: General Help
---

### Post by jbowman86 on 2007-05-14
Hi Guys,

I Use a bluetooth connection to my phone to get web access and am sick of manually connecting my linux box to my phone then running a wvdial. I am wondering if there is any way to get 2 commands to auto run at login.

First i need to get this line to run in a terminal:

          "sudo rfcomm bind rfcomm0 00:18:AF:4B:C6:85 3"

(PS if i can get this to run in a terminal will it ask me for my password due to the 'sudo'?)

Then after that i need to get this line to run in a terminal:

          "wvdial phone"

Any help will be great, thanks in advance.

PS im running ubuntu 6.10

---

### Post by mssever on 2007-05-14
> **jbowman86 said:**
> Hi Guys,

I Use a bluetooth connection to my phone to get web access and am sick of manually connecting my linux box to my phone then running a wvdial. I am wondering if there is any way to get 2 commands to auto run at login.

First i need to get this line to run in a terminal:

          "sudo rfcomm bind rfcomm0 00:18:AF:4B:C6:85 3"

(PS if i can get this to run in a terminal will it ask me for my password due to the 'sudo'?)

Then after that i need to get this line to run in a terminal:

          "wvdial phone"

Any help will be great, thanks in advance.

PS im running ubuntu 6.10

You can make a simple script:[LIST=1]
[*]Create a new file
[*]Set the first line to ```
#!/bin/bash
```
[*]Put your commands in the file and save it
[*]Make the file executable, either via the properties dialog in Nautilus or by ```
chmod +x your/file/name
```
[*]Go to System > Preferences > Sessions and add your script to the list of startup programs[/LIST]Tips:[LIST]
[*]To make the password prompt available even when your script isn't running in a terminal, replace sudo with gksudo, and surround the rest of the command with *single* quotes.
[*]To totally remove the password prompt, do ```
sudo chown root /path/to/your/script
sudo chmod +s /path/to/your/script
``` Then remove all instances of sudo or gksudo from your script. This is called running setuid root. It means that your script always runs with root privileges. Due to the inherent security risks associated with setuid, be sure that what you put in a setuid script is correct.[/LIST]

---

### Post by gianluigi.zanettini on 2007-06-10
Many thanks ;)

---

