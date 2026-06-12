---
title: "How to write a script in BASH shell which has to source a 'CSHRC' file in CSH shell?"
date: 2013-07-10
forum: General Help
---

### Post by cipher18 on 2013-07-10
Hi guys!
I am trying to write a script file in BASH shell. I need to source a CSHRC file before opening the program. Here is a piece of code that i have written;

#!/bin/tcsh
# Script to run Virtuoso

cd /<path_to_directory>
csh
source <file_name>.cshrc
virtuoso &

The problem I am facing is that until I execute the "EXIT" command in the terminal window the program doesn't open

Any help is appretiated!
Thank you in advance!!

---

### Post by steeldriver on 2013-07-10
Try removing the 'csh' command before the 'source xxx' - you shouldn't need it, you are already in a C shell because of the #!/bin/tcsh at the top of the script, and it's starting an *interactive* subshell (which is what you're exiting from when you type 'exit' in the invoking terminal) that is preventing the script from progressing to the next command (rather than executing the next command *inside* a C shell - which is probably what you intended)

---

