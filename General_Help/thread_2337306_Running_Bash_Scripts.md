---
title: "Running Bash Scripts"
date: 2016-09-16
forum: General Help
---

### Post by Artsnova on 2016-09-16
Hello,  
I've written a bash script that I want to run.  In the terminal, the script and I are in the same directory: /home/user
The script has as the shebang line #!/bin/bash
The filename is testa.sh and I've changed its permissions so that it is executable
In the various tutorials I've read, while a very few will prefix the script filename with 'bash', most just say to enter the script filename on its own.  

If I enter testa.sh, I get a  testa.sh: command not found error
If I enter bash testa.sh the script executes successfully. 

My question is why must I prefix my command with 'bash' in order to run my script, while others clearly don't have to?  

What do I need to do in order to be able to just type in the name of my script file and have it execute without having to prefix it with the bash command? 

Thanks.

---

### Post by speed... on 2016-09-16
Try with:
```
./testa.sh
```


/Edit
Sorry, lost the last question...
You can copy it to /usr/bin or add the path to the script:


Edit your .bashrc to add the desired directory on the PATH environmental variable.
export PATH=path/to/the/script:$PATH

---

### Post by Artsnova on 2016-09-16
Hi Mr. Speed, 
Thank you for the two tips. 
1 - prefixing my script file name with './' works.  
2 - will edit my .bashrc to add the directory to  PATH.

Thanks again.

---

