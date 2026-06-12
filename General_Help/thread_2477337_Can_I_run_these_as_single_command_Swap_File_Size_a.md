---
title: "Can I run these as single command? Swap File Size adjust"
date: 2022-07-22
forum: General Help
---

### Post by naxal on 2022-07-22
Hello,

I use Ubuntu (VMs) for multiple home server projects. Often I end up adjusting the swap file depending on the need. Following are the commands that I run with sudo privilege.

> 1. **swapoff /swap.img** (Turning off the Swap File)

2. **rm /swap.img** (Remove Swap File)


3. **dd if=/dev/zero of=/swap.img bs=1M count=512** (Create new Swap File -> Value to change depending on swap requirements)


4. **chmod 600 /swap.img** (Permission Editing Swap File)


5. **mkswap /swap.img** (Assign Swap File)


6. **swapon /swap.img** (Turning on the Swap File)

Just like two commands **apt update && apt upgrade -y **can be run together, is there anyway I can run these above mentioned commands as single command at one go? Can anyone help me do that?

Thanks.

---

### Post by mikewhatever on 2022-07-22
You can coopy/paste all of the above in a text file, and then run the text file itself. Text files with multiple commands and statements are called "scripts", and they are used all over in any OS.

---

### Post by Holger_Gehrke on 2022-07-22
There's a lot of ways to run multiple commands in one line.

[LIST]
[*]command1 && command2 : run command2 if command1 runs successfully 
[*]command1 ; command2 : run command1 then command2 without conditions 
[*]command1 || command2 : run command2 if command1 produces an error 
[/LIST]
 
And of course there's also command-substitution:[INDENT]command2 $(command1) : run command1 and put it's standard-output into the command-line for command2 (can also be written with backticks (`) around command1 instead of '$()')
[/INDENT]

And - as mikewhatever already said - putting your commands into a text file and marking that file as executable is also always an option especially if it's a procedure you want to use repeatedly. Putting a shebang-line ('#!/usr/bin/bash' as the very first line) at the beginning of a script is usually a good idea. There are more languages than just the shell to write scripts in and a shebang makes it obvious for the system what interpreter to use for the script in question.

Holger

---

### Post by Impavidus on 2022-07-22
Apart from making a separate script file, you could make a bash function in your .bashrc or write an alias.

---

