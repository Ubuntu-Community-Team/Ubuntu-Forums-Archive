---
title: "Last command in .sh files won't run."
date: 2013-04-03
forum: General Help
---

### Post by noersetiawan on 2013-04-03
[COLOR=#333333][FONT=Ubuntu Beta]I have this script in a *.sh file to enable natural scrolling. I've added it to Startup Application.[/FONT][/COLOR]

[COLOR=gray]#!/bin/sh
[/COLOR][COLOR=black]xinput [/COLOR][COLOR=#00008B]set[/COLOR][COLOR=black]-[/COLOR][COLOR=black]prop [/COLOR][COLOR=maroon]11 [/COLOR][COLOR=maroon]268 [/COLOR][COLOR=black]-[/COLOR][COLOR=maroon]106 [/COLOR][COLOR=black]-[/COLOR][COLOR=maroon]106
[/COLOR][COLOR=black]nautilus [/COLOR][COLOR=black]-[/COLOR][COLOR=black]q [/COLOR][COLOR=black]&&[/COLOR][COLOR=black] nautilus [/COLOR][COLOR=black]-[/COLOR][COLOR=black]n
[/COLOR][COLOR=#333333][FONT=Ubuntu Beta]
The problem is, whenever I login, the last command (nautilus -n) won't run -which is annoying because I can't use the Super button to open Dash- and I have to run nautilus manually. What's wrong?[/FONT][/COLOR]

---

### Post by mvs1207 on 2013-04-03
what is return (or exit) code of ```
 nautilus -q 
```

It is possible that the return code is non zero and hence the second part (after &&) is not executed.

---

### Post by noersetiawan on 2013-04-03
How do I check the return code? I have changed the && with ;, still not working.
I have tried my script above on terminal line-by-line, and everything works fine. The problem occur when running it from .sh file, nautilus simply won't run, and I have to click on Home icon or any other way to run it manually.

---

### Post by coldcritter64 on 2013-04-03
> **noersetiawan said:**
> How do I check the return code? I have changed the && with ;, still not working.
I have tried my script above on terminal line-by-line, and everything works fine. The problem occur when running it from .sh file, nautilus simply won't run, and I have to click on Home icon or any other way to run it manually.
Try removing the "&&", and putting "nautilus -n" on a new line below "nautilus -q". The operand "&&" meaning "then execute" will not be used if the first of the commands fails to complete fully. That is, the second command running is dependent on the first command being sucessfully completed. Cheers.

[s]Edit: if the line of code with the "&&" in completes in a terminal, that is because you are using the "Bash" shell. When that script is run, it is calling the "sh" shell interpreter not "Bash".[/s]

---

### Post by schragge on 2013-04-03
+1
*nautilus -q* quits nautilus. So, if there's no nautilus running, I can imagine that the command fails. Also preface the last command in script with *exec*, i.e.:
```

nautilus -q
exec nautilus -n

```This way the shell won't wait till nautilus ends.

> **coldcritter64 said:**
> if the line of code with the "&&" in completes in a terminal, that is because you are using the "Bash" shell. When that script is run, it is calling the "sh" shell interpreter not "Bash".Sorry, but no. && works in any POSIX-conform shell, not only in bash.

---

### Post by coldcritter64 on 2013-04-03
> **schragge said:**
> +1
*nautilus -q* quits nautilus. So, if there's no nautilus running, I can imagine that the command fails. Also preface the last command in script with *exec*, i.e.:
```

nautilus -q
exec nautilus -n

```This way the shell won't wait till nautilus ends.

Sorry, but no. && works in any POSIX-conform shell, not only in bash.
OK, thanks for correction, I'll strike that out . cheers

---

### Post by noersetiawan on 2013-04-04
Based on your reply, I have changed the last line to nautilus -q && nautilus -n &&[enter], and it works. Thanks for all your reply. How can I make this thread as solved?

---

### Post by claracc on 2013-04-04
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by noersetiawan on 2013-04-04
Done. Thanks.

---

