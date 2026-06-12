---
title: "modifying the bashrc file"
date: 2007-09-24
forum: General Help
---

### Post by Luis Miguel 78 on 2007-09-24
Recently I managed to install the latest version of the building energy modelling software Esp-r on my laptop, however, in order to run it is necessary to update the bash profile file and add an extra line on the PATH=:/opt/esru/bin.. (something like that) , the closest one to a bash profile file was on my home directory and it was called bashrc and it could only be seen after activating the hidden files option. I added the line at the end of the file, and then I was able to run Esp-r. However something happened, It deactivated all the system commands from the terminal, I could try to run for example sudo or the su command and they wont be available. To bring it back the system to the original state, I had to go to the bashrc file and erase the PATH= line I had added before.
 
Do you have any idea where should I added the PATH line? maybe the bashrc file is not the right one; or perhaps I need something else in the line so the system commands remain active.
 
Any help guys you can give me on this, it will help me a lot, Im new to linux and ubuntu
 
Thanks,

Luis

---

### Post by Adramelech on 2007-09-24
the line you have to add is

PATH=$PATH:/opt/esru/bin

That way, you append you directory to the PATH variable and you dont delete the old ones, the old ones are necessary to locate the system commands.

---

### Post by Luis Miguel 78 on 2007-09-24
Thank you Adramelech for the fast reply
It works perfect now!
thanks!

---

### Post by suhailsqm on 2008-06-10
i want to modify my PATH. but i can find my bashrc file in my home directory
the closest i can find is /etc/bash.bashrc

i am in ubuntu kde 8.04

need urgent help ..

thanks in advance

---

### Post by mali2297 on 2008-06-10
> **suhailsqm said:**
> i want to modify my PATH. but i can find my bashrc file in my home directory
the closest i can find is /etc/bash.bashrc

i am in ubuntu kde 8.04

need urgent help ..

thanks in advance

The file is hidden. If you use a file manager, check the option to show hidden files, or if you use the terminal, check
```

ls -A

```

If you still cannot find it, you might have to create it. Copy the global bash.bashrc to use it as a template:
```

cp /etc/bash.bashrc ~/.bashrc

```

---

