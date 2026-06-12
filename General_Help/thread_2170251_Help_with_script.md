---
title: "Help with script"
date: 2013-08-25
forum: General Help
---

### Post by ndnd on 2013-08-25
Hi I have a script I need to run in CSH and getting the following error 

> Choice (a, u, i, q) [i] ? ./install: 44: ./install: Syntax error: newline unexpected


The script snippet where the error is occurring  

> echo " u - Uninstall AABB"
echo " i - Information"
echo " q - quit"
echo ""

echo -n "Choice (a, u, i, q) [i] ? "
set answer = $<
if ( $answer == "a" || $answer == "A" ) then
    goto NEWINSTALL
    else if ( $answer == "b" || $answer == "B") then
    goto INSTALL_AABB
    else if ( $answer == "u" || $answer == "U") then


Anyone can please point out. I am sure it has to do with space or a line but not able to understand the correct syntax

---

### Post by steeldriver on 2013-08-25
Does your script have the correct shebang (#!/bin/csh) at the top? how exactly are you executing it?

The error looks a lot like the script is actually being executed by a non-csh shell, e.g.

```

$ ./cshell.sh 
 u - Uninstall AABB
 i - Information
 q - quit

Choice (a, u, i, q) [i] ? a
NEWINSTALL: label not found.

```

works (obviously I don't have the rest of the script, with the NEWINSTALL label); however forcing it to use /bin/sh I get 

```

$ **sh** ./cshell.sh 
 u - Uninstall AABB
 i - Information
 q - quit

Choice (a, u, i, q) [i] ? ./cshell.sh: 10: ./cshell.sh: Syntax error: newline unexpected

```

---

### Post by ndnd on 2013-08-25
Hello steeldriver,
I see that the first line on the file is 

> #!/bin/csh -f

Now coming to how you got it work. I need a bit more help here. So the name of the file is > install

I do the following > $csh
%sudo sh ./install

to which I get the above mentioned error. 

I assumed that "%" means I am running the C-shell script so when you type 
"./cshell.sh" I am not sure what you mean here. 

can you please give exact syntax for me. 

Thanks in advance.

---

### Post by steeldriver on 2013-08-25
If you have a script file with a shebang, and have made it executable i.e.

```
chmod +x install
```

then you can run it simply by typing the name of the file - the only 'trick' is that because the current directory is not on your executable PATH you usually need to prefix that with ./ i.e.

```
./install
```

to mean 'the file called install **in the current directory**'. Or in your case (to give it elevated privileges)

```
sudo ./install
```

Adding 'sh' before the name is unnecessary and forces the script to be run in whatever shell /bin/sh points to (by default, in Ubuntu, that's /bin/dash), overriding the #!/bin/csh directive in the file itself.

EDIT: as well, changing the terminal's shell to csh before calling the script is also unnecessary - a executable file with a 'shebang' is all you need

Hope this helps

---

### Post by ndnd on 2013-08-25
Worked Perfectly ! thanks it was the issue about making the file executable.

---

