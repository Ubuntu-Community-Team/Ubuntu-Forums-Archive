---
title: "Create special launcher  How to?"
date: 2007-07-02
forum: General Help
---

### Post by Dubstar_04 on 2007-07-02
I have managed to install Pro/Engineer a 3D cad program for windows and linux on my feisty box. The only problem is that the only way I can launch the program is to open terminal and type 

```
LANG=en_GB.iso88591 /usr/local/ptc/proeWildfire3.0/bin/proe1
```

this is because i can't change the system language to ISO instead of UTF-8 and pro/e will only run with ISO.

This method of launch works fine but its not very elegant.

Any suggestions??

---

### Post by meatpan on 2007-07-02
> **Dubstar_04 said:**
> 
```
LANG=en_GB.iso88591 /usr/local/ptc/proeWildfire3.0/bin/proe1
```



Here is an option you can try:

Consider making an alias for the command.  An alias is a convenient shorthand for a wordy command.  For example,  'alias run_proe1="LANG=en_GB.iso88591 /usr/local/ptc proeWildfire3.0/bin/proe1"' will run your command whenever you type 'run_proe1'

If you add this definition to your ~/.bashrc file, the alias will automatically be ready whenever you open a new terminal.  You can view your current aliases by just typing 'alias'.

---

### Post by Dubstar_04 on 2007-08-16
For reference i managed to copy the comand to s text file i gave it some chmod +x and made a launcher to it.
bing bang bong done!!

---

